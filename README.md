# Filosofía de la ciencia

Libro de filosofía general de las ciencias, en castellano, escrito en abierto y
en curso de escritura. Fuente en Markdown, compilado con [Quarto](https://quarto.org)
a un sitio HTML navegable y a un PDF.

- **Se lee en** <https://manual.delaciencia.org> (GitHub Pages, publicado por CI en
  cada *push* a `main`); el PDF se adjunta a cada *release*.

- **Estado**: **versión 0.1** (2026-09-13): primera parte completa (capítulos 0–9).
  Segunda parte (capítulos 10–17) y epílogo pendientes; hay borradores de los
  capítulos 10–12 en el directorio, fuera del libro. El plan completo de la obra
  está en el capítulo 1, §7.
- **Cuaderno del capítulo 8**: [`cuaderno_08_estadistica.ipynb`](cuaderno_08_estadistica.ipynb),
  introducción a la probabilidad y la estadística con simulaciones, para
  estudiantes de filosofía. Necesita Python 3 con las bibliotecas de
  [`requirements.txt`](requirements.txt); no forma parte del libro compilado.
- **Bitácora**: [`BITACORA.md`](BITACORA.md) — qué se hizo, cuándo, por qué, y las
  convenciones del proyecto.
- **Entorno y compilación**: [`ENTORNO.md`](ENTORNO.md) — cómo dejar una máquina
  lista para compilar el libro, y qué decisiones técnicas están tomadas.
- **Licencia**: CC BY-SA 4.0 ([`LICENSE`](LICENSE)).

## Compilar

```bash
quarto preview          # sitio con recarga automática, para escribir
quarto render           # HTML + PDF en _book/
quarto render --to html # solo el sitio (segundos)
quarto render --to pdf  # solo el PDF (~1 min)
```

## Qué es cada archivo

| Archivo | Para qué |
|---|---|
| `_quarto.yml` | Configuración única del libro: capítulos, partes, formatos, estilo de cita. |
| `capitulo_NN_tema.md` | Un archivo por capítulo. Markdown de pandoc. |
| `index.qmd` | Portada del sitio y presentación del libro. |
| `referencias.qmd` | Contiene el `::: {#refs}` donde va la bibliografía general. |
| `referencias.bib` | Bibliografía única: una clave por obra. |
| `apa.csl` | Estilo de cita APA 7; la localización castellana la da `lang: es`. |
| `preamble.tex` | Tipografía del PDF (TeX Gyre Pagella). |
| `cuaderno_08_estadistica.ipynb` | Cuaderno Jupyter de acompañamiento del capítulo 8 (no se compila con el libro). |
| `requirements.txt` | Bibliotecas de Python que usa el cuaderno. |
| `custom.scss` | Tipografía del HTML. |

## Corregir

Quien encuentre un error puede abrir una *errata* en las issues del repositorio
(hay plantilla) o proponer la corrección directamente. Las correcciones se acreditan.
