# Bitácora del libro

Registro de trabajo sobre el manuscrito. **Las entradas van en orden cronológico inverso** (la más reciente primero). Cada entrada consigna: qué archivos se tocaron, qué se agregó o modificó, qué se verificó y qué quedó pendiente.

Convenciones del proyecto, para no volver a averiguarlas:

- Un archivo por capítulo (`capitulo_NN_tema.md`). **Una sola bibliografía, `referencias.bib`**, para todo el libro: una clave por obra (formato `autorAÑOpalabra`), definida una única vez aunque la obra se cite en varios capítulos.
- Pandoc Markdown (Quarto lo trae embebido), citas autor-fecha `[@clave]`, **secciones con `## §N. Título`**, énfasis con `*cursiva*`.
- El título del capítulo va en el `title:` del YAML y **no** como encabezado en el cuerpo: en un libro Quarto un `#` en el cuerpo significa capítulo nuevo.
- El encabezado YAML de cada capítulo lleva solo `title:` y `date:`. Bibliografía, estilo de cita, idioma y formatos se declaran una vez en `_quarto.yml`.
- Ningún capítulo escribe su sección de referencias a mano: Quarto la agrega al final de cada capítulo en el HTML, y en el PDF la bibliografía aparece una sola vez, en `referencias.qmd`.
- Cada capítulo cierra indicando sus prolongaciones en la segunda parte (plan de la obra: capítulo 1, §7).
- Énfasis solo con *cursiva*: los capítulos de la primera parte no usan negrita ni subtítulos de nivel 3; cada sección es prosa continua bajo `## §N. Título`.
- La numeración de capítulos y secciones es **manual** (`number-sections: false`): las remisiones en prosa dependen de ella y el capítulo 08, todavía ausente, no debe correr la cuenta.

## Estado del manuscrito (al 6 de septiembre de 2026)

| Cap. | Título breve | Estado |
|---|---|---|
| 00 | Notas para empezar: influencias y deudas | escrito |
| 01 | Conocer científicamente | escrito — ampliado 2026-09-06 |
| 02 | La indeterminación de la prueba | escrito — ampliado 2026-09-06 |
| 03 | El giro historicista | escrito |
| 04 | La explicación científica | escrito — ampliado 2026-09-04 |
| 05 | El realismo y sus alternativas | escrito |
| 06 | La experimentación y los instrumentos | escrito |
| 07 | Narración, selección y modelo | escrito |
| 08 | Probabilidad e inferencia | pendiente |
| 09 | Valores, comunidad y sociedad | escrito |
| 10–18 | Segunda parte + epílogo | pendientes |

---

## 2026-09-06 — Publicación: el manuscrito se convierte en libro Quarto sobre git

**Archivos modificados**

- Los 9 capítulos: encabezados de sección, encabezado YAML y bloque de referencias.
- `capitulo_00_algunas notas para empezar.md` → `capitulo_00_notas_para_empezar.md` (el espacio rompe scripts, URLs y CI).
- `referencias_cap00.bib` … `referencias_cap09.bib` → **`referencias.bib`** (único).
- Nuevos: `_quarto.yml`, `index.qmd`, `referencias.qmd`, `preamble.tex`, `custom.scss`, `apa.csl`, `.gitignore`, `LICENSE`, `.github/workflows/render.yml`, `.github/ISSUE_TEMPLATE/errata.yml`.
- `BITACORA.md`: convenciones reescritas (bibliografía única, `## §N.`, YAML mínimo, numeración manual).

**Motivo**

El libro pasa a publicarse en abierto. Se evaluaron pandoc plano con Makefile, Jupyter Book/MyST y mdBook, y se eligió **Quarto**: es pandoc por dentro —lo trae embebido—, de modo que el requisito de fuente Markdown con salida LaTeX se cumple por construcción, y aporta lo que un Makefile obligaría a construir a mano: ensamblado del libro, HTML navegable con buscador, y una sola configuración en lugar de nueve encabezados duplicados. Los capítulos siguen siendo `.md` y no `.qmd`, así que cada uno se puede compilar con pandoc suelto: la salida de Quarto queda abierta. MyST se descartó por ser un dialecto distinto de pandoc; mdBook, por su ruta a PDF.

El repositorio vive ahora en `~/proyectos/libro-filosofia-ciencia`, **fuera de Nextcloud**: un `.git` sincronizado se corrompe cuando dos máquinas escriben índices y locks a la vez. Los PDF de `complementos_bibcienciasffyh/` quedan en Nextcloud y están en `.gitignore` (tienen copyright).

**Cambios en el manuscrito**

- Las secciones pasan de `# §N.` a `## §N.`: en un libro Quarto un `#` en el cuerpo significa capítulo, de modo que cada § habría producido un capítulo del PDF. El título lo aporta el `title:` del YAML.
- Los encabezados YAML pierden `bibliography`, `csl`, `lang`, `link-citations`, `reference-section-title` y `author`: todo eso se declara una vez en `_quarto.yml`.
- Se quita el bloque `# Referencias` manual del final de cada capítulo. Quarto agrega la lista al final de cada capítulo en el HTML; en el PDF la bibliografía va una sola vez, en `referencias.qmd`.

**Bibliografía**

Los nueve `.bib` tenían 259 entradas con 183 claves: 76 duplicadas, y ya divergiendo. Cuatro claves estaban definidas de manera distinta según el archivo y se resolvieron a mano:

- `kuhn1962structure` — se conserva la variante con la nota sobre la 2.ª edición ampliada de 1970.
- `popper1978dos` — se conserva la nota superconjunto (la del capítulo 1, que además indica la procedencia de la fórmula kantiana citada en la p. 22).
- `rescher1977methodological` — «Basil Blackwell», que es el sello correcto en 1977.
- `scriven1959explanation` — es un artículo de *Science*: queda como `@article` y no como `@book`.

Además, cinco campos `publisher` con «and» se protegieron con llaves dobles: el lector BibTeX los tomaba como lista de nombres e imprimía «Chapman; Hall».

**Estilo de cita**

APA 7 (`apa.csl` comiteado) con `lang: es`, que da la localización castellana. Reemplaza al `chicago-author-date.csl` que los nueve capítulos declaraban y que nunca existió en el directorio: **queda cerrado el pendiente n.º 2 de la entrada del 2026-09-04 y el n.º 4 de la entrada anterior.**

**Entorno**

Quarto 1.10.18 instalado en `~/.local/opt` (trae pandoc 3.10 embebido) y TinyTeX en `~/.TinyTeX`, ambos sin `rpm-ostree` ni contenedores, que en Kinoite es lo que corresponde. **Queda cerrado el pendiente n.º 1 de la entrada anterior: pandoc ya está disponible y los capítulos compilan con `--citeproc`.**

Hay una salvedad importante, anotada abajo como pendiente: `tlmgr` es un script de Perl y Fedora Kinoite no trae Perl, de modo que la instalación automática de paquetes LaTeX de Quarto **no funciona en esta máquina**. Los paquetes que faltaban —`babel-spanish`, `hyphen-spanish`, `tex-gyre-math`— se instalaron descomprimiendo a mano los `.tar.xz` de tlnet en `~/.TinyTeX/texmf-dist`, y el español se registró a mano en `language.dat` y `language.def` para reconstruir el formato de xelatex con `xetex -ini` (sin `fmtutil`, que también es Perl). Sin ese paso el PDF sale con guionado inglés.

En `preamble.tex` las fuentes se piden **por nombre de archivo** y no por nombre de familia: los `.otf` de TeX Gyre viven en el árbol texmf y XeTeX los encuentra por kpathsea, mientras que buscarlos por nombre exige que fontconfig los tenga registrados, cosa que no ocurre ni en una TinyTeX recién instalada ni en el runner de CI.

**Verificaciones hechas**

- Las 183 claves citadas resuelven contra `referencias.bib`; ninguna entrada queda sin usar; ninguna duplicada. El render no emite advertencias de citeproc.
- `quarto render` produce HTML navegable y un PDF de 236 páginas.
- El PDF incrusta TeX Gyre Pagella (texto y matemática) y TeX Gyre Heros; los rótulos salen en castellano («Tabla de contenidos», «Capítulo»).
- Cada archivo produce un capítulo, no ocho: la demotación de encabezados quedó bien.
- La bibliografía aparece una sola vez en el PDF. Antes de corregirlo se repetía en los nueve capítulos —cada `div #refs` de un libro Quarto recibe la bibliografía completa—, lo que inflaba el PDF a 334 páginas.
- Las citas salen en autor-fecha APA con localización castellana («En M. Curd & S. Psillos (Eds.)»).

**Pendientes que este trabajo dejó planteados**

1. **Faltan el título definitivo del libro y el nombre del autor**: `_quarto.yml` los tiene como `TODO`. Hoy figura «Filosofía de la ciencia / Representar, intervenir, historizar» y el autor vacío.
2. **Sin Perl, `tlmgr` no corre.** Si en el futuro hace falta otro paquete LaTeX, hay dos caminos: `rpm-ostree install perl-interpreter` (persistente, exige reinicio) o un `toolbox` con Perl, que comparte `$HOME` y por lo tanto puede operar sobre `~/.TinyTeX`. En CI no hace falta: el runner trae Perl.
3. **Decidir si se quiere bibliografía por capítulo también en el PDF.** Hoy el HTML la tiene por capítulo y el PDF una sola al final. Tenerla por capítulo en el PDF exigiría abandonar citeproc por biblatex con `refsection`, y con ello el `.csl` de APA.
4. **Confirmar la licencia.** Se dejó CC BY-SA 4.0.
5. Sigue abierto lo demás de las entradas anteriores: verificar el año de la traducción de Popper, el de Díez y Moulines, la cita de Britannica, y armonizar el capítulo 7 §2 con el capítulo 4.

---

## 2026-09-06 — Capítulos 1 y 2: el sentido de la epistemología y la anatomía de la contrastación

**Archivos modificados**

- `capitulo_01_conocer_cientificamente.md` — de 6 a 7 secciones; de ~5.400 a ~8.400 palabras.
- `referencias_cap01.bib` — de 34 a 35 entradas.
- `capitulo_02_indeterminacion_de_la_prueba.md` — de 5 a 7 secciones; de ~6.400 a ~12.400 palabras.
- `referencias_cap02.bib` — de 21 a 24 entradas.
- `BITACORA.md` — convención de la línea 9 (el plan de la obra pasó de §6 a §7) y nota sobre énfasis.

**Motivo**

Incorporar los dos complementos bibliográficos de la carpeta `complementos_bibcienciasffyh/`, que los alumnos del curso tendrán disponibles, manteniendo el libro **autocontenido**: se usan como inspiración y como anclaje de puntos concretos, con cita textual y página, sin que ninguna afirmación del texto exija haberlos leído. Dos huecos concretos los motivaban. El capítulo 1 pasaba del diagnóstico sobre la imagen de la ciencia a la genealogía del reconstruccionismo sin decir nunca desde qué pregunta se examina una imagen de la ciencia, con lo cual la genealogía se leía como doxografía. El capítulo 2 argumentaba solo por la negativa —tres listas de imposibilidades— y no trabajaba un solo episodio histórico, en contra del *eje histórico-historiográfico* que el capítulo 1 declara.

**Fuentes utilizadas**

- Popper, *Introducción de 1978* a *Los dos problemas fundamentales de la epistemología* (Tecnos), pp. 19-27: §1 completo («Conocimiento científico e ignorancia socrática») y arranque del §2.
- Díez y Moulines, *Fundamentos de filosofía de la ciencia* (Ariel), cap. 3 *Contrastación de hipótesis*, pp. 61-90, y cap. 4 *Los conceptos científicos*, pp. 91 y ss.

**Cambios en el capítulo 1**

- **§2 — NUEVA.** *La epistemología y su pregunta: ignorancia, certeza, búsqueda.* Arco Sócrates → Newton → Kant → Einstein → falibilismo, siguiendo a Popper como planteo del problema y no como solución (se avisa de entrada que el capítulo 2 lo criticará). Las tres posiciones de la teoría del conocimiento y la recuperación del *skeptomai* —comprobar, reflexionar, investigar— frente al uso corriente de «escepticismo»; de ahí el desplazamiento de la certificación a la mejora que justifica que la filosofía de la ciencia no legisle desde fuera. El shock newtoniano y la pregunta kantiana; la respuesta de Kant («el entendimiento no extrae sus leyes de la Naturaleza, sino que se las prescribe») y la enmienda de Popper —las teorías son hipótesis que el entendimiento *intenta* imponer y que pueden fracasar—, leída como la versión en miniatura de la doble articulación representar/intervenir del §4 y como corrección falibilista del enlace rescheriano del capítulo 0. La ecuación heredada (ciencia = conocimiento = certeza + fundamentación), con la observación de Popper de que atraviesa las disputas —Kant y el *Aufbau*, Mill y Whewell—, que convierte la genealogía del §3 en la historia de su caída. Einstein y la ruina de la ecuación, con la fórmula de 1933 sobre falsabilidad y referencia a la realidad, y la observación técnica de que la corroboración no puede ser una probabilidad (remitida al capítulo 8). Falibilismo como retorno socrático, con la deuda que Popper reconoce con Peirce y no paga: se cobra entera, distinguiendo el falibilismo como virtud del investigador solitario del falibilismo peirceano inseparable de la comunidad autocorrectiva, y se anuncia que el libro toma el segundo. Advertencia «falible ≠ arbitrario» (anticipo del capítulo 3). El pasaje contra el cientificismo y contra el anticientificismo, aceptando el diagnóstico del falso dilema y corrigiendo su individualismo: la autoridad de la ciencia descansa en la organización social de la crítica y en la apertura, no en una virtud. Cierre operativo con «ciencia no es posesión de conocimiento, sino búsqueda de verdad» y la definición de trabajo de la epistemología como estudio de las condiciones bajo las cuales una práctica de indagación mejora sus creencias.
- **§3–§7.** Antiguos §2–§6, sin cambios de contenido; solo renumeración.
- **Ediciones menores.** En el §1, la remisión interna «la sección §4 de este capítulo» pasa a «§5» y se anuncia el nuevo §2; en el §3, la presentación de Popper remite ahora también al §2.

**Cambios en el capítulo 2**

- **§1.** La frase de hoja de ruta anuncia las dos secciones nuevas y el paso de la crítica negativa a la reconstrucción positiva; la «doble función» del capítulo pasa a ser triple.
- **§2.** Párrafo nuevo, antes del pasaje sobre instrumentos, con el capítulo 4 de Díez y Moulines: los conceptos clasificatorios, comparativos y métricos como condición de que haya datos; la distinción cualitativo/cuantitativo como epistemológica y no ontológica; la clasificación de los elementos químicos por número de protones como relación de equivalencia teóricamente cargada; el flogisto como «acto epistémico fallido» de un concepto vacío. Remite a la distinción datos/fenómenos del capítulo 6.
- **§4.** Párrafo nuevo con las dos admisiones de Popper en 1978 —que no se atrevería a afirmar que la teoría de Newton haya sido falsada, y que la corroboración no puede interpretarse como probabilidad—, que complican al Popper de manual y refuerzan la objeción de Salmon que sigue.
- **§5 — NUEVA.** *La anatomía de la contrastación: qué se pone a prueba y cómo.* Los cuatro elementos (*H*, *SA*, *CI*, *P*) y la implicación contrastadora, con Halley y Semmelweis. La frontera *H*/*SA* como vaga, contextual y pragmática —fijada por la intención de la contrastación—, con Neptuno y Vulcano como el caso decisivo: misma jugada lógica, dos asignaciones distintas de responsabilidad, y la diferencia no la fija la lógica. Condición C1 y por qué la implicación debe ser lógica y no un condicional material. Condición C2 y el análisis de su estatuto: ni deductiva, ni inductiva (petición de principio por contraposición), ni verdad material comprobable, sino expectativa relativa a las alternativas «en juego». **Tesis propia: C2 es el lugar exacto donde vive la subdeterminación**, y como es relativa al repertorio de alternativas disponibles, la evidencia resulta ser una relación histórica y no una propiedad intrínseca de los enunciados. Los esquemas [REF] y [CONF]: el primero es deductivamente válido pero descansa en una premisa evaluativa sobre *SA* y *CI* —formalización exacta del holismo duhemiano—; el segundo es mixto y descansa además en C2. **Tesis propia: confirmación y refutación son asimétricas, pero fallan en lugares distintos**, no en la oposición popperiana entre lo concluyente y lo nulo. Las fases de Venus como contrastación concluyente contra el geocentrismo clásico e inconcluyente a efectos confirmatorios, porque el sistema mixto de Tycho predecía lo mismo.
- **§6 — NUEVA.** *Rescates, hipótesis ad hoc y el destino del experimento crucial.* Las tres puertas de salida ante una refutación, con cuatro casos de idéntica estructura lógica y suerte dispar: paralaje estelar, flogisto de masa negativa, Millikan/Ehrenhaft y el Tarot. La distinción legítimo/ilegítimo como gradual, contextual y pragmática pero no arbitraria, donde «pragmático» significa dependiente del contexto *científico*, esto es, de las posibilidades de integración teórica. **Respuesta a Grünbaum (§3):** la restricción a ajustes no triviales no puede escribirse de antemano como condición formal porque nombra un juicio; **reencuadre del veto popperiano (§4):** «no introduzcas hipótesis *ad hoc*» no es una regla aplicable; y **rescate del *bon sens* de Duhem (§2):** nombra un juicio con estructura, auditable históricamente aunque no formalizable. Predicciones inadecuadas —vaguedad, disyunción exhaustiva, repetición hasta el acierto—, con el rendimiento de obtener lo que la falsabilidad prometía sin necesitar una frontera nítida entre ciencia y no ciencia. Contrastaciones cruciales como combinación de dos contrastaciones que exige C2 para cada hipótesis, con Venus y Michelson-Morley como fracasos y Foucault 1850 como éxito, más la posición matizada de Hempel. **Tesis propia: ni ilusión baconiana ni negación duhemiana, sino gradación** —los experimentos no deciden solos pero desplazan cargas de la prueba, y ese desplazamiento es un hecho histórico documentable. Cierre con los factores que hacen buena a una contrastación (cantidad, calidad, variedad; simplicidad, belleza, integración teórica) y una **marca explícita de distancia respecto de la fuente**: Díez y Moulines tratan los factores sociales como añadidos externos, y el libro sostendrá en el capítulo 9 que algunos son constitutivos —lo cual la propia reconstrucción exige, porque si C2 se evalúa relativamente a las alternativas en juego, quién decide cuáles están en juego es una cuestión epistemológica.
- **§7.** Antigua §5, renumerada. Párrafo nuevo de apertura: la reconstrucción positiva no disuelve la indeterminación, la **localiza** en tres puntos identificables —C2, la premisa sobre *SA* y *CI*, y el juicio sobre los rescates—, y esa localización la convierte en un programa de investigación histórico en lugar de un escándalo escéptico.

**Bibliografía agregada**

- `referencias_cap01.bib`: `popper1978dos`. Kant y Einstein se citan a través de Popper, sin entradas propias, indicándolo en el texto.
- `referencias_cap02.bib`: `diez1997fundamentos`, `popper1978dos` (misma clave, según la convención del proyecto) y `hempel1966philosophy`.

**Verificaciones hechas**

- Todas las claves citadas en los capítulos 1 y 2 resuelven contra sus `.bib`; ninguna entrada queda sin usar; no hay claves duplicadas (comprobado por `diff` de claves citadas contra claves definidas).
- Los `.bib` tienen llaves balanceadas y tantas entradas como cierres.
- La renumeración no rompe remisiones: se revisaron una a una las 33 apariciones de `§N` en ambos capítulos, y ningún otro capítulo remite a secciones de los capítulos 1 o 2 por número.
- Se corrigieron dos desvíos de convención introducidos al redactar: se eliminaron los siete subtítulos de nivel `##` (ningún otro capítulo de la primera parte los usa) y se convirtieron a cursiva las 20 negritas, respetando los asteriscos escapados del §3.
- Todas las citas textuales de ambas fuentes llevan página.

**Pendientes que este trabajo dejó planteados**

1. **`pandoc` no está instalado en el entorno actual**, de modo que **no pudo ejecutarse la compilación con `--citeproc`** para los capítulos 1 y 2. La verificación de claves se hizo por comparación textual, que detecta claves huérfanas y entradas sin usar pero no errores de sintaxis que solo el lector BibTeX advertiría. **Conviene recompilar ambos capítulos cuando `pandoc` esté disponible.**
2. **Año de la edición castellana de Popper.** La portada escaneada no trae año. La entrada usa 1978, que es la fecha de la *Introducción* —la única parte citada—, y el `note` consigna que el original alemán es de 1979 (Mohr, Tübingen) y que la paginación remite a la edición de Tecnos. **Verificar a mano el año de la traducción de Albisu Aparicio** y decidir si conviene citar como «Popper [1978] AAAA».
3. **Año de Díez y Moulines.** El nombre del archivo dice 1997 (1.ª ed., Ariel) y la portadilla del escaneo dice 1999 (2.ª ed.), de donde procede la paginación citada. La entrada usa 1997 con `note` explicando que se cita por la segunda edición.
4. **Sigue faltando `chicago-author-date.csl`** (pendiente n.º 2 de la entrada anterior), que el encabezado de todos los capítulos declara.
5. El capítulo 3 de Díez y Moulines contiene episodios históricos aún sin usar —esferas homocéntricas, rotación de la Tierra, barómetro de Torricelli y Pascal, ADN, extinción de los dinosaurios, deriva continental, anillo de Einstein— que podrían servir de banco de casos para los capítulos 3, 6 y 8.
6. El capítulo 4 de Díez y Moulines (conceptos clasificatorios, comparativos y métricos) se usó solo en un párrafo del §2 del capítulo 2. Su tratamiento de la medición es material natural para el capítulo 6 y para el capítulo 8, aún pendiente.


## 2026-09-04 — Capítulo 4: ampliación (introducción al explicar, Cartwright, comprensión, evidencia)

**Archivos modificados**

- `capitulo_04_explicacion_cientifica.md` — de 6 a 10 secciones; de ~5.100 a 9.625 palabras.
- `referencias_cap04.bib` — de 21 a 45 entradas.

**Motivo**

El capítulo funcionaba bien como reconstrucción del arco clásico (Hempel → mecanicistas), pero le faltaban cuatro cosas: una distinción inicial entre el explicar cotidiano y el científico (y, dentro de este, entre el relato de causas probables y la apelación a leyes generales abstractas); el puente hacia los modelos por vía de Nancy Cartwright; la dimensión cognitiva (comprensión científica); y la reconfiguración de la noción de evidencia, recuperando elementos del capítulo 3. Todo en registro introductorio: la discusión avanzada queda para la segunda parte.

**Cambios por sección**

- **Título y fecha.** Ahora "de la cobertura legal a los modelos, los mecanismos y la comprensión"; fecha actualizada.
- **§1** (existente). Se agregó un párrafo final de alcance: nivel introductorio explícito, remisión de la discusión contemporánea a la segunda parte, anuncio de los tres hilos añadidos y presentación de las dos panorámicas de referencia (SEP y Kitcher/Britannica).
- **§2 — NUEVA.** *Dar razones y explicar: usos cotidianos, relatos causales y leyes abstractas.* Polisemia del "explicar" ordinario (significados, procedimientos, justificaciones, causas) y recorte del campo a las preguntas *por qué* sobre acontecimientos y regularidades. Distinción entre *dar razones para creer* y *dar razones de que algo ocurra*, con el barómetro anticipando el contraejemplo del §4. Tesis de continuidad: la diferencia entre explicación cotidiana y científica es de *régimen* (explicitación, control público, rastreo sistemático de relevancia), no de especie lógica. Contraste interno entre el polo nomológico y el relato de causas probables (biología, arqueología, sociología), con Martínez —*completabilidad intrínseca* vs. *triangulación jerárquica*— y Richards —*índice de realidad*—. Cierre: es un gradiente y no la dicotomía nomotético/idiográfico (los sistemas complejos exigen ambos registros), más la advertencia de las *just-so stories*, y el mapa del capítulo.
- **§3–§5.** Antiguos §2–§4, sin cambios de contenido; solo renumeración.
- **§6 — NUEVA.** *Del imperio de las leyes al mundo moteado: Cartwright y el puente hacia los modelos.* Las leyes fundamentales que "mienten" y el canje entre alcance y verdad; la concepción del *simulacro* (explicar es construir un modelo que acomode el fenómeno a la teoría); capacidades y cláusulas *ceteris paribus*; *máquinas nomológicas* y mundo moteado, con el vínculo a la creación de fenómenos del capítulo 6. De ahí: los modelos como mediadores parcialmente autónomos y formas estables de hacer ciencia (Morgan y Morrison; el modelo BCS analizado por la propia Cartwright), y su circulación como *zonas de intercambio* entre comunidades científicas y tecnológicas (SIR, elementos finitos, Monte Carlo; el modelo climático como objeto compartido sin acuerdo semántico). Último párrafo: reserva explícita frente al antirrealismo fuerte de Cartwright, remitiendo a los capítulos 5 y 7.
- **§7.** Antiguo §5, renumerado y retitulado *mecanismos, idealización, cómputo*; se ajustaron el párrafo de apertura y el del segundo registro para que continúen el §6 en lugar de repetirlo.
- **§8 — NUEVA.** *La dimensión cognitiva: entender, y saber que se ha entendido.* El exilio hempeliano de la comprensión y su retorno con Friedman; por qué la *sensación* de entender es mal indicador (Trout: fluidez y sesgo retrospectivo; Lombrozo: preferencia por lo simple y amplio, sesgo teleológico, detalle irrelevante seductor, y la cara positiva del autoexplicarse); la inteligibilidad como criterio operativo, contextual y no arbitrario (de Regt y Dieks); convergencia hacia comprender-como-capacidad (Woodward, Strevens, Khalifa, Potochnik); posición del libro: habilidad gradual y distribuida, medida por desempeño. Cierre con la opacidad de los híbridos humano-máquina (capítulos 11–13) y la inteligibilidad como problema institucional (capítulo 16).
- **§9 — NUEVA.** *La evidencia reconfigurada: relevancia, triangulación y cambio teórico.* Cuatro desplazamientos: (1) de la instancia confirmatoria a la evidencia de relevancia e invariancia bajo intervención; (2) correlación *y* mecanismo (tesis Russo–Williamson), con la deriva continental (Oreskes) mostrando que el mecanismo convierte datos en evidencia y que los estándares evidenciales son solidarios de los explicativos; (3) evidencia *para usar* (Cartwright y Hardie: "funcionó allí" ≠ "funcionará aquí"; la validez externa como cuestión explicativa); (4) triangulación y robustez, con la advertencia de que la independencia de las líneas debe argumentarse (capítulo 2). Cierre anudando con el capítulo 3 (círculo reflexivo, no vicioso) y dejando servida la inferencia a la mejor explicación para el capítulo 5.
- **§10.** Antiguo §6, ampliado: el saldo sistemático incorpora a Cartwright y a la explicación narrativa; nuevo párrafo con los tres hilos añadidos (ontológico-metodológico, cognitivo, evidencial) y la advertencia de nivel; se añadió al final una *Nota de lecturas* con las dos entradas de la SEP y el artículo de Kitcher.

**Bibliografía agregada** (24 entradas en `referencias_cap04.bib`)

Cartwright 1983, 1989, 1999 (*Dappled World*), 1999 (capítulo BCS en *Models as Mediators*) y Cartwright & Hardie 2012; Morgan & Morrison 1999; Galison 1997; Martínez 1997; Richards 1992; Gould & Lewontin 1979; Trout 2002; de Regt & Dieks 2005; de Regt 2017; Lombrozo 2006; Strevens 2008; Potochnik 2017; Khalifa 2017; Russo & Williamson 2007; Oreskes 1999; Woodward & Ross 2025 (SEP); Ross & Woodward 2023 (SEP); Kitcher (Britannica); Kuhn 1962 y Laudan 1977 (ya usadas en otros capítulos, con la misma clave).

**Verificaciones hechas**

- `pandoc --citeproc` compila el capítulo sin advertencias.
- Las 45 claves citadas resuelven contra el `.bib`; ninguna entrada queda sin usar; no hay claves duplicadas.
- Ningún otro capítulo remite a las secciones del capítulo 4 por número, de modo que la renumeración no rompe referencias cruzadas.

**Notas sobre las fuentes**

- La entrada "Scientific Explanation" de la *Stanford Encyclopedia of Philosophy* fue retirada y reemplazada, en diciembre de 2025, por **"20th Century Theories of Scientific Explanation"** (Woodward y Ross). Se cita con el título nuevo, y se agrega su continuación, "Causal Approaches to Scientific Explanation" (Ross y Woodward, 2023), como referencia para la segunda parte.
- El artículo de Kitcher en la *Encyclopædia Britannica* devuelve HTTP 403 y no pudo leerse directamente. La entrada bibliográfica va **sin año** y en el texto solo se afirma de él lo verificable por otras vías: la autoría de Kitcher y la existencia de sus secciones sobre explicación/leyes/teorías y sobre cambio científico. **Conviene revisarlo a mano** y, si corresponde, precisar la cita.

**Pendientes que este trabajo dejó planteados**

1. **Armonizar el capítulo 7 §2**: trata la explicación narrativa en biología sin citar a Martínez ni a Richards, que ahora entran en el capítulo 4. Convendría remitir explícitamente y repartir el material para no duplicar.
2. **Falta `chicago-author-date.csl`** en el directorio: el encabezado de todos los capítulos lo declara, pero el archivo no está, de modo que `pandoc --citeproc` falla si no se lo omite. Descargarlo al directorio del libro.
3. **Verificar la cita de Britannica** (ver nota anterior).
4. El capítulo 4 anuncia tratamiento avanzado de la explicación en la segunda parte; conviene decidir **en qué capítulo exactamente** (¿11, 13, 17?) para poder remitir con número en lugar de "la segunda parte".
