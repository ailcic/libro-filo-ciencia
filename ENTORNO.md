# Entorno de trabajo y decisiones técnicas

Documento de traspaso: qué hace falta para compilar este libro en una máquina
nueva, qué decisiones ya están tomadas y por qué, y qué cosas de la máquina
donde se montó el proyecto son excepcionales y **no** hay que repetir en otra.

Escrito el 6 de septiembre de 2026, al convertir el manuscrito en libro Quarto.
El relato cronológico de ese trabajo está en [`BITACORA.md`](BITACORA.md).

---

## 1. Máquina nueva: lo mínimo

En cualquier Linux, macOS o Windows **con Perl disponible** (es decir, en
cualquier sistema que no sea inmutable), alcanza con esto:

```bash
# 1. Quarto. Trae pandoc embebido: no instales pandoc por separado.
#    https://quarto.org/docs/get-started/  (o el gestor de paquetes del sistema)

# 2. LaTeX, solo si querés generar el PDF. TinyTeX se instala en el home,
#    sin root, y descarga los paquetes que falten a medida que los necesita.
quarto install tinytex

# 3. El repositorio
git clone <url-del-repo> libro-filosofia-ciencia
cd libro-filosofia-ciencia
quarto check     # pandoc y LaTeX deben dar OK
quarto render    # HTML y PDF en _book/
```

La primera compilación del PDF tarda algunos minutos porque TinyTeX baja
`babel-spanish`, `hyphen-spanish`, `tex-gyre`, `tex-gyre-math`, `unicode-math`,
`microtype` y `koma-script`. Las siguientes tardan alrededor de un minuto.

No hace falta Python: el libro todavía no ejecuta código. Cuando exista el
capítulo 8 habrá que agregar Jupyter, un `requirements.txt` y el paso
correspondiente en el workflow de CI.

**Si solo vas a escribir y revisar el HTML, saltate el paso 2.** El sitio se
compila en segundos y no necesita LaTeX.

---

## 2. Lo que fue excepcional en la máquina de origen (Fedora Kinoite)

Todo esto es una particularidad de un sistema inmutable **sin Perl**. En una
máquina normal nada de esto hace falta, y conviene no arrastrarlo.

El problema de fondo: `tlmgr`, el gestor de paquetes de TeX Live, es un script
de Perl, y la imagen base de Kinoite no incluye Perl. Por lo tanto **la
instalación automática de paquetes LaTeX que hace Quarto no funciona ahí**: el
render falla con `env: 'perl': No such file or directory`.

Lo que hubo que hacer a mano en esa máquina:

1. **Instalar los paquetes LaTeX descomprimiendo los `.tar.xz` de tlnet**
   directamente en `~/.TinyTeX/texmf-dist`, y correr `mktexlsr` (que sí es un
   script de shell). Se instalaron así `babel-spanish`, `hyphen-spanish` y
   `tex-gyre-math`.
2. **Registrar el español en la configuración de idiomas.** Los patrones de
   guionado se cargan al construir el formato, y el `language.dat` activo
   —`~/.TinyTeX/texmf-var/tex/generic/config/`— lo genera `tlmgr`, así que no
   incluía el español. Se agregaron a mano las líneas correspondientes en
   `language.dat` y `language.def` (quedaron copias `.bak` al lado).
3. **Reconstruir el formato de xelatex sin `fmtutil`** (que también es Perl):

   ```bash
   xetex -ini -jobname=xelatex -progname=xelatex -etex xelatex.ini
   cp xelatex.fmt ~/.TinyTeX/texmf-var/web2c/xetex/xelatex.fmt
   ```

Sin el paso 3 el PDF compila igual, pero **con guionado inglés**: la
justificación del texto en castellano queda mal y babel avisa con
`No hyphenation patterns were preloaded for the language 'spanish'`.

Si alguna vez hiciera falta otro paquete LaTeX en esa máquina, hay dos caminos
mejores que repetir todo esto: `rpm-ostree install perl-interpreter` (queda
persistente, exige reiniciar) o un `toolbox` con Perl, que comparte `$HOME` y
por lo tanto puede operar sobre `~/.TinyTeX`.

### Consecuencia que sí es permanente

En `preamble.tex` las fuentes se piden **por nombre de archivo y no por nombre
de familia**:

```tex
\setmainfont{texgyrepagella}[Extension=.otf, UprightFont=*-regular, ...]
```

`\setmainfont{TeX Gyre Pagella}` falla, porque fontspec busca por fontconfig y
fontconfig no conoce el árbol texmf de TeX Live. Pedirlas por archivo hace que
XeTeX las encuentre por kpathsea. **Esto no es un parche de Kinoite: hace falta
igual en una TinyTeX recién instalada y en el runner de CI.** No lo cambies por
la forma "linda" salvo que instales las fuentes en el sistema, cosa que haría
el repositorio dependiente de la máquina.

---

## 3. Decisiones tomadas

### Motor: Quarto

Se evaluaron cuatro caminos:

| Opción | Por qué sí / por qué no |
|---|---|
| **Quarto** ✅ | Es pandoc por dentro (lo trae embebido), así que "fuente Markdown, salida LaTeX" se cumple por construcción. Aporta el ensamblado del libro, el HTML navegable con buscador, y una sola configuración en lugar de nueve encabezados YAML duplicados. |
| Pandoc plano + Makefile | Cero abstracción nueva, pero el ensamblado del libro, la numeración y el HTML navegable hay que construirlos y mantenerlos a mano. |
| Jupyter Book / MyST | La fuente sería MyST, un dialecto distinto de pandoc, con su propio motor de citas. Contradice el requisito central. |
| mdBook / MkDocs | HTML excelente, ruta a PDF/LaTeX pobre. |

**Los capítulos siguen siendo `.md`, no `.qmd`.** Quarto los acepta igual, y así
cada capítulo se puede compilar suelto con pandoc: la salida de Quarto queda
abierta si algún día conviene irse. Solo el capítulo 8, cuando exista, necesitará
ser `.qmd` porque llevará código Python.

### Citas: APA 7 con `lang: es`

`apa.csl` está comiteado en el repositorio. La localización castellana la da
`lang: es` en `_quarto.yml`; no existe ni hace falta un "apa-es.csl". APA imprime
"&" entre autores también en castellano; si se prefiere "y", es un cambio de una
línea en el `.csl` (el término `and` con `form="symbol"`).

Reemplazó al `chicago-author-date.csl` que los nueve capítulos declaraban en su
YAML y que nunca existió en el directorio.

### Bibliografía: una sola, `referencias.bib`

Los nueve `referencias_capNN.bib` tenían 259 entradas con 183 claves: 76
duplicadas, **y ya divergiendo entre archivos**. Se fundieron en uno solo, con
una clave por obra.

Cuatro claves estaban definidas de manera distinta según el archivo y se
resolvieron a mano: `kuhn1962structure` (se conservó la nota sobre la 2.ª ed.
ampliada de 1970), `popper1978dos` (la nota superconjunto), 
`rescher1977methodological` ("Basil Blackwell", el sello correcto en 1977) y
`scriven1959explanation` (es un artículo de *Science*: `@article`, no `@book`).

**Cuidado con `and` dentro de campos `publisher`**: el lector BibTeX lo toma
como separador de una lista de nombres e imprime "Chapman; Hall". Hay que
proteger el campo con llaves dobles: `publisher = {{Chapman and Hall}}`.

### Dónde aparece la bibliografía

- **HTML**: Quarto agrega automáticamente la lista de referencias al final de
  cada capítulo, más la bibliografía completa en `referencias.qmd`.
- **PDF**: una sola bibliografía, al final.

Esto **no es configurable capítulo por capítulo**. En un libro Quarto el PDF es
un único documento de pandoc, y cada `div #refs` que encuentre recibe la
bibliografía *completa*: con un bloque de referencias por capítulo, el PDF salía
con las 183 obras repetidas nueve veces, 334 páginas en lugar de 236. Por eso
ningún capítulo escribe su sección de referencias a mano.

Tener bibliografía por capítulo también en el PDF exigiría abandonar citeproc
por biblatex con `refsection`, y con eso se perdería el `.csl` de APA. Queda
como decisión abierta.

### Numeración manual

`number-sections: false`. El manuscrito numera a mano sus capítulos
("Capítulo N." en el `title:` del YAML) y sus secciones ("§N."), y las
remisiones en prosa dependen de esa numeración. Además el capítulo 8 todavía no
existe: con numeración automática, el 9 pasaría a ser el 8 y todas las
remisiones del libro quedarían corridas.

### Estructura de los capítulos

En un libro Quarto un `#` en el cuerpo significa **capítulo nuevo**. Por eso las
secciones son `## §N. Título` y el título del capítulo va en el `title:` del
YAML, no como encabezado. Si alguna vez se pega texto viejo con `# §N.`, hay que
demotarlo.

### El repositorio vive fuera de Nextcloud

Un `.git` sincronizado por Nextcloud se corrompe cuando dos máquinas escriben
índices y locks a la vez. La sincronización entre máquinas la hace git. En la
carpeta vieja de Nextcloud quedó un aviso y la copia previa a la conversión, que
se puede borrar: su estado exacto es el primer commit de este repositorio.

Lo único que sigue viviendo solo en Nextcloud es `complementos_bibcienciasffyh/`
—PDF con copyright—, por eso está en `.gitignore`.

---

## 4. Revisar el HTML mientras el repositorio es privado

### Mientras escribís, en tu máquina

```bash
quarto preview
```

Levanta el sitio en `localhost` con **recarga automática**: guardás el `.md` y el
navegador se actualiza solo. Es la forma de trabajo normal y no necesita
LaTeX ni conexión.

### Desde otro dispositivo, o para mostrárselo a alguien

GitHub Pages **no está disponible para repositorios privados en el plan
gratuito** (hace falta Pro o superior). El workflow de CI ya contempla esto: el
paso de Pages está dormido y solo se activa cuando exista la variable de
repositorio `PUBLICAR_PAGES` con valor `true`
(Settings → Secrets and variables → Actions → Variables). Mientras tanto CI
igual compila y no falla.

Tres opciones, de menor a mayor esfuerzo:

1. **Artefactos de CI** (funciona hoy, sin configurar nada). Cada push deja en
   la pestaña Actions dos artefactos descargables: `sitio-html` (el sitio
   entero, se descomprime y se abre `index.html`) y `libro-pdf`. Cero
   infraestructura; a cambio, hay que bajar un zip cada vez.

2. **Cloudflare Pages** (la recomendación si vas a revisar seguido). Es gratis,
   **despliega desde repositorios privados**, y da una URL por rama y por pull
   request, así que podés ver un capítulo en curso sin tocar `main`. Si además
   querés que el sitio no sea público, Cloudflare Access —el plan gratuito de
   Zero Trust cubre hasta 50 usuarios— lo deja detrás de un login por correo.
   Configuración: comando de build `quarto render --to html`, directorio de
   salida `_book`. Netlify hace lo mismo, pero su protección con contraseña es
   de pago.

3. **GitHub Pages**, cuando el libro se haga público o si pasás a un plan Pro.
   Ya está todo escrito: creás la variable `PUBLICAR_PAGES=true` y activás Pages
   en Settings → Pages con origen "GitHub Actions".

Para leerlo en el teléfono o en una tablet dentro de tu propia red, otra opción
barata es `python3 -m http.server --directory _book` y entrar por la IP de la
máquina (o por Tailscale, si las máquinas ya están en la misma red privada).

---

## 5. Pendientes

1. **Título definitivo y nombre del autor**: `_quarto.yml` los tiene marcados
   como `TODO`.
2. **Confirmar la licencia**: quedó CC BY-SA 4.0.
3. **Capítulo 8** (probabilidad e inferencia): es el único capítulo con código.
   Cuando exista, será `.qmd`, y habrá que agregar `requirements.txt`, el paso
   de Python en CI, y decidir la política de `freeze` (si se versiona `_freeze/`
   o si cada render re-ejecuta el código con semillas fijas).
4. **Decidir si se quiere bibliografía por capítulo en el PDF** (ver arriba).
5. **DOI y versionado**: cuando haya una primera versión pública, conviene un
   tag `v0.1`, el PDF adjunto al release y Zenodo vinculado al repositorio para
   acuñar el DOI. Nada de eso está montado todavía.
6. **Dónde publicar, además del repositorio.** GitHub Pages es alojamiento, no
   edición: no da ISBN ni catálogo ni indización. Para un libro de texto
   universitario en castellano conviene averiguar la editorial universitaria y
   el repositorio institucional, que son los que dan presencia bibliográfica.
7. Lo que sigue abierto de las entradas anteriores de la bitácora: verificar el
   año de la traducción de Popper, el de Díez y Moulines, la cita de Britannica,
   y armonizar el capítulo 7 §2 con el capítulo 4.
