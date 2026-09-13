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
- La numeración de capítulos y secciones es **manual** (`number-sections: false`): las remisiones en prosa dependen de ella.
- Cada capítulo de la primera parte cierra con una *Nota de lecturas* (párrafo que empieza con `*Nota de lecturas.*`), con sugerencias accesibles y con página cuando corresponde.
- Traducciones: la entrada del `.bib` es la edición efectivamente citada y lleva `origdate` con el año del original, de modo que la cita sale «Kuhn (1963/1980)»; la clave usa el año del original. Las citas de segunda mano se hacen a través de la fuente que las recoge, y se lo indica en el texto (Kant y Einstein a través de Popper en el capítulo 1; los textos de Kuhn posteriores a *La estructura* a través de Pérez Ransanz en el capítulo 3).
- Fórmulas en LaTeX de pandoc (`$...$`), usadas por primera vez en el capítulo 8; decimales con coma en prosa y `0{,}9` en fórmulas; porcentajes con espacio duro («90 %»).
- Los recuadros de rememoración («Cuadro clásico N», «Cuadro matemático N») son *callouts* de Quarto (`::: {.callout-note title="..."}`); pandoc suelto los compila como un `div` sin título, y Quarto les pone caja y título.
- El código ejecutable va en cuadernos Jupyter aparte (`cuaderno_NN_tema.ipynb`), fuera de la lista de capítulos, ejecutados a mano y versionados con sus salidas; los capítulos siguen siendo `.md` y el libro no ejecuta código.
- Los borradores de capítulos que todavía no forman parte del libro se guardan en el directorio con su nombre definitivo (`capitulo_1N_tema.md`) pero no figuran en `_quarto.yml`; se anotan aquí como borradores.

## Estado del manuscrito (al 13 de septiembre de 2026 — versión 0.1)

| Cap. | Título breve | Estado |
|---|---|---|
| 00 | Notas para empezar: influencias y deudas | escrito — secciones finales completadas 2026-09-13 |
| 01 | Conocer científicamente | escrito — ampliado 2026-09-06; nota de lecturas y recuadros 2026-09-13 |
| 02 | La indeterminación de la prueba | escrito — ampliado 2026-09-06; nota de lecturas 2026-09-13 |
| 03 | El giro historicista | reescrito 2026-09-13 |
| 04 | La explicación científica | escrito — ampliado 2026-09-04; remisiones 2026-09-13 |
| 05 | El realismo y sus alternativas | escrito — §3 ampliado 2026-09-13 |
| 06 | La experimentación y los instrumentos | escrito — nota de lecturas 2026-09-13 |
| 07 | Narración, selección y modelo | escrito — §2 reescrito 2026-09-13 |
| 08 | Probabilidad e inferencia | escrito 2026-09-13; cuaderno de acompañamiento `cuaderno_08_estadistica.ipynb` |
| 09 | Valores, comunidad y sociedad | escrito — remisiones 2026-09-13 |
| 10–12 | Estilos de razonamiento; simulación; abstracción e infraestructura | borradores 2026-09-13, fuera del libro |
| 13–18 | Resto de la segunda parte + epílogo | pendientes |

---

## 2026-09-13 — Versión 0.1: cierre de la primera parte y cuaderno del capítulo 8

**Archivos modificados**

- `capitulo_00_notas_para_empezar.md` — se escribieron las dos secciones que estaban vacías, «Historia de la ciencia y la tecnología» y «Algo de metafísica» (~900 palabras en total), en la voz confesional del capítulo; erratas del primer párrafo.
- `capitulo_01_conocer_cientificamente.md` — los dos marcadores `[Cuadro clasicoso 1]` y `[Cuadro matematicoso 1]` del §7 se reemplazaron por recuadros reales: «Cuadro clásico 1. Lo que los antiguos pedían del saber» (*Teeteto*, *Menón*, *Analíticos segundos*) y «Cuadro matemático 1. Dos formas válidas y una falacia» (*modus ponens*, *modus tollens*, afirmación del consecuente, con remisión al capítulo 2 §5 y al 8 §6); la frase que los anuncia se corrigió («dosis», «exclusivamente») y dice ahora que en esta versión son los únicos.
- `capitulo_02_indeterminacion_de_la_prueba.md` — §6: los subíndices Unicode (`P₁`, `Pₙ`, `Pᵢ`) pasan a fórmulas (`$P_1$`, `$P_n$`, `$P_i$`); desaparecen las advertencias de glifos ausentes en Pagella itálica.
- `capitulo_08_probabilidad_inferencia.md` — la nota de lecturas remite al cuaderno de acompañamiento.
- **`cuaderno_08_estadistica.ipynb` — nuevo.** Cuaderno Jupyter de acompañamiento del capítulo 8: introducción a la probabilidad y la estadística para estudiantes de filosofía, 34 celdas en diez secciones, cada una referida al § del capítulo que ilustra: frecuencia relativa y los cálculos de Salmon y De Méré (§2-3); teorema de Bayes con el cribado médico (posterior 0,0089) y los dos mazos (3/8) (§3); lavado de las probabilidades previas con distribuciones Beta (§6); error estándar, cobertura de intervalos de confianza y el *Literary Digest* (§7); regresión a la media (§7); paradoja de Simpson con una población ficticia del tipo del caso israelí (§5); la dama del té, valor *p*, errores de tipo I y II y potencia (§8); comparaciones múltiples y detención opcional (§9); la crisis de replicación como cálculo de tasa de base (§9); y ejercicios. No repite el argumento filosófico: lo ilustra. Se distribuye ejecutado, con seis figuras incrustadas.
- `requirements.txt` — nuevo: `numpy`, `matplotlib`, `scipy`, solo para el cuaderno.
- `referencias.bib` — de 195 a 221 entradas: cuatro para el capítulo 0 (`lakatos1976proofs`, `rescher1996process`, `vincenti1990what`, `whitehead1929process`) y veintidós que solo usan los borradores de la segunda parte (ver abajo).
- `_quarto.yml` — `author: "Andrés A. Ilcic"` (era un `TODO` vacío); comentario sobre el cuaderno y sobre los borradores.
- `index.qmd`, `README.md`, `ENTORNO.md`, `.github/workflows/render.yml`, `.gitignore` — estado «versión 0.1», el cuaderno y sus requisitos, `.ipynb_checkpoints/` ignorado.
- **Borradores fuera del libro**: `capitulo_10_estilos_de_razonamiento.md` (~9.800 palabras), `capitulo_11_simulacion_computacional.md` (~9.100) y `capitulo_12_abstraccion_infraestructura.md` (~9.900) se escribieron en esta misma sesión, antes de que se decidiera cerrar solo la primera parte. Compilan con `pandoc --citeproc` y sus claves están en `referencias.bib`, pero **no figuran en `_quarto.yml` y no forman parte de la versión 0.1**. Fuentes: Crombie, Hacking (1992, 2002, *La domesticación del azar*), Ruphy, Galison (caps. 8 y 9), Lenhard (*Calculated Surprises*), Durán, Winsberg y Harvard, Turner, Tedre, Rieder, Tanenbaum y Bos, y las entradas del *Glosario de filosofía de la técnica*. Quedan como punto de partida de la segunda parte y deben revisarse antes de incorporarse.

**Motivo**

Cerrar una primera versión publicable de la primera parte (versión 0.1): sin marcadores ni secciones vacías, con autor, con el capítulo 8 acompañado por un cuaderno de estadística separado del texto, y con una pasada de coherencia sobre los capítulos 0 a 9.

**Pasada de coherencia**

- Todas las remisiones «capítulo N (§M)» de los capítulos 0 a 9 apuntan a secciones existentes (comprobación automática). Las remisiones a los capítulos 10-18 se conservan: el capítulo 1 y la portada declaran que la segunda parte está pendiente.
- Los dos recuadros del capítulo 1 usan las mismas letras que el capítulo 2 (*H*, *P*) y remiten a las secciones donde los esquemas se complican (2 §5) y donde la confirmación recibe forma probabilística (8 §6).
- Las secciones nuevas del capítulo 0 citan solo obras ya usadas en la primera parte (Kuhn, Crombie, Hacking, Shapin y Schaffer, Galison, Losee, Simondon, Simon, Dewey) más las cuatro nuevas; sus tesis coinciden con los compromisos del capítulo 1 §7 (procesual) y del capítulo 5 §5 (realismo de efectos).
- Los números del cuaderno reproducen los del capítulo: 91/216, 0,491, 0,1008 y 0,0089, 2/9 y 3/8, 1/70; la cobertura simulada de los intervalos del 95 % da 0,949; la tasa de falsos positivos simulada con α = 0,05 da 0,052.

**Verificaciones hechas**

- `pandoc --citeproc` compila los diez capítulos sin advertencias.
- Las 199 claves citadas en los capítulos 0-9 resuelven; las 22 restantes del `.bib` solo las citan los borradores 10-12.
- PDF de prueba de la primera parte entera (capítulos 0-9 concatenados, `scrbook`, `xelatex`, `preamble.tex`): 204 páginas, sin caracteres ausentes en el registro de xelatex (antes había 22 avisos por los subíndices del capítulo 2), sin errores; solo quedan `Overfull \hbox` de cabeceras.
- El cuaderno se ejecutó de principio a fin en un entorno virtual limpio (Python 3.14, numpy 2.5, matplotlib 3.11, scipy 1.18): 34 celdas, 0 errores, 6 figuras, 14 segundos.
- Los recuadros compilan como *callouts* en Quarto (sintaxis estándar) y como `div` sin título en pandoc suelto; en el PDF de prueba el contenido aparece sin caja.

**Publicación**

- El repositorio se copió a `~/Documents/gits_self/libro-filo-ciencia` (fuera de Nextcloud, como pedía `ENTORNO.md`) y se creó el remoto público `github.com/ailcic/libro-filo-ciencia`. La copia de Nextcloud queda como respaldo y no debe editarse.
- `quarto render --to html` corrió por fin (Quarto 1.10.18 descomprimido en `~/Applications`): el sitio compila y los dos *callouts* del capítulo 1 aparecen como cajas.
- Deploy: GitHub Actions compila HTML y PDF y publica en GitHub Pages con el dominio `manual.delaciencia.org` (archivo `CNAME` + `site-url` en `_quarto.yml`; DNS en Cloudflare). Detalles en `ENTORNO.md`, §4.

**Pendientes que este trabajo dejó planteados**

1. ~~Ver el PDF que produce CI y adjuntarlo al *release*~~ — hecho el mismo día: el primer *run* de CI compiló y desplegó sin errores; el *release* `v0.1` lleva adjunto el PDF compilado localmente con Quarto 1.10.18 y TeX Live 2026 (322 páginas, bibliografía única, recuadros del capítulo 1 como cajas). Queda comparar con el PDF del artefacto de CI (TinyTeX) por si difieren en tipografía.
2. ~~DNS~~ — `manual.delaciencia.org` ya apuntaba a GitHub Pages a través del proxy de Cloudflare y sirvió el libro desde el primer despliegue. GitHub no emite certificado propio mientras el dominio esté *proxied* (el HTTPS lo da Cloudflare): no activar «Enforce HTTPS» en GitHub salvo que se pase el registro a DNS only. Zenodo y DOI siguen pendientes (`ENTORNO.md`, pendiente 5).
3. **Copia de Nextcloud**: borrar o marcar como respaldo `~/Nextcloud/2026/libro-filosofia-ciencia` para no editar dos copias.
4. **Borradores 10-12**: revisarlos antes de incorporarlos; el 12 cita cuatro obras que no están en la biblioteca local (Star y Ruhleder 1996, Ziemann et al. 2016, Eklund et al. 2016, Spolsky 2002) y cuyas referencias deben verificarse; el 10 y el 11 se cotejaron contra las fuentes.
5. **Cuaderno**: probarlo en el entorno en que lo usarán los estudiantes (Colab o Binder) y decidir si conviene un `environment.yml` o un enlace directo; considerar cuadernos análogos para los capítulos 2 (contrastación) y 11 (simulación) cuando exista.
6. **Verificaciones de edición pendientes de la entrada anterior**: Teorema 1979/1980, datos de Taylor, Britannica, año de Popper y de Díez y Moulines.

---

## 2026-09-13 — Primera parte: capítulo 8 nuevo, capítulo 3 reescrito y coherencia interna desde la carpeta de lecturas

**Archivos modificados**

- `capitulo_08_probabilidad_inferencia.md` — **nuevo**: 10 secciones, ~14.000 palabras.
- `capitulo_03_giro_historicista.md` — de 6 a 9 secciones; de ~4.800 a ~11.700 palabras.
- `capitulo_07_modelos_evolucion.md` — §2 reescrito (de ~600 a ~2.500 palabras); retoques en §1 y §6; nota de lecturas.
- `capitulo_05_realismo.md` — párrafo nuevo en §3; nota de lecturas.
- `capitulo_01`, `capitulo_02`, `capitulo_04`, `capitulo_06`, `capitulo_09` — remisiones cruzadas, páginas y notas de lecturas.
- `referencias.bib` — de 183 a 195 entradas; `kuhn1977essential` pasa a describir la edición castellana (FCE, 1982), que es la que ahora se cita con página.
- `apa.csl` — término castellano `original-work-published` («trabajo original publicado en»).
- `_quarto.yml` — el capítulo 8 entra en la lista de capítulos como `.md`.
- `README.md`, `index.qmd`, `ENTORNO.md` — estado del capítulo 8 y decisión sobre `.md`/`.qmd`.

**Motivo**

El pedido fue usar los textos de la carpeta `refs/filosofia de la ciencia/` (quince PDF) como guía y como sugerencias de lectura para ordenar la coherencia interna de la primera parte, con tres indicaciones precisas: que el capítulo 8 se apoyara principalmente en la inferencia estadística de Salmon (*The Foundations of Scientific Inference*) y de Potochnik, Colombo y Wright (*Recipes for Science*); que el capítulo 3 se apoyara de manera sustantiva en Pérez Ransanz (*Kuhn y el cambio científico*); y que la noción de explicación narrativa se fundara en Martínez (*De los efectos a las causas*, cap. 8). El pedido nombraba la carpeta vieja `book_filosofiadelaciencia/`, pero su `LEEME` indica que está desactualizada y que no se edite: los cambios se hicieron en este repositorio.

Además de esas tres indicaciones, la lectura del libro entero mostró huecos de coherencia concretos: el capítulo 8 estaba prometido en los capítulos 1 (§2), 2 (§4), 7 (§6) y 9 (§1, §4 y §6) y no existía; el capítulo 1 prometía que el 3 mostraría por qué las lecturas relativistas del historicismo fallan, y el 3 no trataba el relativismo; el capítulo 7 §2 duplicaba el tema de la explicación narrativa del capítulo 4 §2 sin su fuente (pendiente de la entrada del 2026-09-04).

**Fuentes utilizadas**

- Salmon, *The Foundations of Scientific Inference* (ed. del cincuentenario, 2017), caps. I-VII y conclusión, pp. 1-132, y el ensayo introductorio de Hitchcock, pp. ix-xxxv.
- Potochnik, Colombo y Wright, *Recipes for Science* (2.ª ed., 2024), caps. 7-11 (pp. 161-290), con pasajes de los caps. 3 (aleatorización, crisis de replicación) y 9-10 (estadística descriptiva e inferencial).
- Pérez Ransanz, *Kuhn y el cambio científico* (FCE, 1999), caps. I-VI y VIII.
- Kuhn, «La función del dogma en la investigación científica» (Cuadernos Teorema, 1980), pp. 3-44, y «Las relaciones entre la historia y la filosofía de la ciencia», en *La tensión esencial* (FCE, 1982), pp. 27-45.
- Taylor, «Comprensión y etnocentrismo», en *La libertad de los modernos* (Amorrortu, 2005), pp. 199-222.
- Martínez, *De los efectos a las causas*, cap. 8, pp. 145-158, y la primera página del cap. 9.
- Losee, *Introducción histórica a la filosofía de la ciencia* (Alianza, 3.ª ed., 1981), caps. 2, 6 y 10.
- Earman y Salmon, Lennox, McGuire, Glymour y W. Salmon, capítulos del manual colectivo *Introduction to the Philosophy of Science* (Prentice Hall 1992; Hackett 1999).
- Hacking, *Representar e intervenir* (Paidós/UNAM, 1996), para las notas de lectura; Díez y Moulines y la introducción de Popper de 1978 ya estaban incorporados.

**Capítulo 8 — *Probabilidad e inferencia: el azar, la estadística y el peso de la evidencia***

- **§1.** Abre con el anuncio del bosón de Higgs y la cifra «una vez en tres millones», para distinguir la probabilidad de los datos bajo el ruido de la probabilidad de la hipótesis. **Tesis propia: la probabilidad y la estadística son la forma que la ciencia moderna dio a la condición C2 del capítulo 2**; no disuelven su relatividad a las alternativas en juego, la vuelven explícita y discutible. Salda las deudas de los capítulos 1 (corroborar no es hacer probable) y 2 (la objeción de Salmon a Popper).
- **§2.** Hume reformulado con Salmon: inferencia ampliativa; el problema de la inducción como problema de la evidencia (las tres reglas del dado); coincidencia frente a regularidad genuina (el distrito de Maryland).
- **§3.** El cálculo: De Méré, Pascal y Fermat; los tres usos de la probabilidad; axiomas de Kolmogorov; teorema de Bayes con el término $\Pr(E \mid \neg H)$; los dos mazos de Salmon y el cribado médico de Potochnik (falacia de la tasa de base).
- **§4.** Criterios de admisibilidad, determinabilidad y aplicabilidad; interpretaciones clásica (paradoja del auto), subjetiva, lógica (diálogo del hipódromo, invariancia lingüística), personalista (apuesta holandesa, tolerancia de absurdos), frecuentista (vindicación pragmática de Reichenbach y reglas asintóticas) y de propensiones (paradoja de Humphreys); pluralismo articulado; el caso *Challenger*.
- **§5.** Caso único y clase de referencia; relevancia estadística (enlace con el capítulo 4 §4); paradoja de Simpson (vacunación en Israel); aceptar frente a asignar probabilidad (Strawson, paradoja de la lotería), enlace con el riesgo inductivo del capítulo 9.
- **§6.** Bayes como estructura de la confirmación: Hanson y Popper reconciliados; Poisson y Arago frente a la dianética; **C2 como la verosimilitud bajo la hipótesis comodín, y la advertencia de Kuhn sobre las teorías probabilistas**; dos sentidos de «confirmar» (respuesta al capítulo 1); Neptuno y Vulcano como redistribución de probabilidad; probabilidades previas, lavado, criterios de plausibilidad de Salmon; eliminación y variedad de instancias; límites (Hume sigue en pie; evidencia vieja y el perihelio de Mercurio).
- **§7.** Estadística: origen estatal y eugenesia (Galton, Pearson, Spearman, Fisher); descriptiva frente a inferencial; errores de medición y de muestreo; regresión a la media; correlación; estimación e intervalos de confianza; *Literary Digest* 1936; la aleatorización como respuesta al límite del método de la diferencia de Mill (Losee).
- **§8.** Contraste de hipótesis nula: el té de Fisher, valor p, tamaño del efecto, errores de tipo I y II, el umbral como juicio (enlace con Douglas y el capítulo 9); frecuentistas y bayesianos: **ninguna escuela elimina el juicio, difieren en dónde lo ponen y cuán visible lo dejan**; límite: la «omnivoría metodológica» de la paleontología.
- **§9.** Coincidencias y comparaciones múltiples: la ley de Bode (Losee), los ingredientes y el cáncer, riesgo relativo y absoluto, Reinhart y Rogoff, inconsistencias en psicología, crisis de replicación.
- **§10.** Balance en tres registros; **Kuhn frente a Bayes: el bayesianismo modela bien el razonamiento dentro de un espacio de alternativas estabilizado y mal los episodios en que el espacio se rehace** (racionalidad no instantánea, reducción al absurdo de Kuhn); la estadística como teoría de efectos (Martínez, Lennox); prolongaciones en los capítulos 11, 12, 13 y 16; nota de lecturas.

**Capítulo 3**

- **§1.** Se agregan el supuesto clásico que identifica Pérez Ransanz («todos los sujetos que manejan la misma evidencia deben llegar a la misma decisión») y el testimonio de Hempel; declaración de fuente y de la regla de citas de segunda mano.
- **§2 — reorganizada.** Kuhn (I): la conferencia de 1961 sobre la función del dogma; ciencia normal; la contrastación de aplicaciones y los tres esquemas de Putnam aplicados a Urano y Neptuno (enlace con el capítulo 2 §5); crisis, perigeo lunar y relatividad del contraejemplo; matriz disciplinar, ejemplar y esquema de ley.
- **§3 — nueva.** Inconmensurabilidad: de la formulación global a la semántica (la hipotenusa) y a la taxonómica y local; el caso de Aristóteles; traducción, interpretación y aprendizaje del lenguaje; «la racionalidad solo supone la posibilidad de comprensión».
- **§4 — nueva.** Racionalidad sin algoritmo: comparación global, desacuerdo racional, distribución del riesgo, comunidad y racionalidad no instantánea, frónesis, consensos racionales y Lysenko, evolución de los valores; el caso Galileo.
- **§5 y §6.** Lakatos y Laudan (antiguos §3 y §4), con el rechazo lakatosiano de la «racionalidad instantánea».
- **§7 — nueva.** Relativismo: el triple relativismo que Laudan atribuye a Kuhn y su respuesta («relativismo acotado»); Kuhn y Taylor; el lenguaje de contrastes transparentes; **seis pautas contra el relativismo**, que cumplen la promesa del capítulo 1, incluida la disolución de la pregunta por la demarcación.
- **§8.** Problema historiográfico (antiguo §5) con la circularidad de la metametodología, el intuicionismo revisable, el circuito de retroalimentación de Kuhn (enlace con el capítulo 0) y **la autonomía de la narración histórica, cuyas reglas limitan sin determinar, como los valores en la elección de teorías**; se precisa que la espiral de Mill está en el capítulo 2.
- **§9.** Balance ampliado y nota de lecturas.

**Capítulo 7 y armonización con el capítulo 4**

- El §2 se funda ahora en Martínez: definición de explicación histórica; historicidad ontológica (del diseño a la individuación genealógica) y epistemológica (narrativa, índice de realidad, abejas y elefantes, metáforas y analogías, asimetría entre pasado y presente); refuerzo mutuo y robustez; leyes y generalizaciones (Hull, Mayr, los caballos en América, los molares); completabilidad intrínseca frente a triangulación jerárquica; la disciplina de las narrativas (filogenias, molares de caballos según Lennox, *just-so stories*); paralelo con la narración histórica de Kuhn. **Queda cerrado el pendiente n.º 1 de la entrada del 2026-09-04.**
- El capítulo 4 remite al 7 (§2) y al 3 (§8), precisa páginas de Martínez y anuncia el tratamiento probabilístico de la relevancia estadística y de los ensayos aleatorizados (capítulo 8 §5 y §7).
- El §6 del capítulo 7 anuncia el 8 con Lennox (la teoría de Darwin como teoría estadística) y Martínez (las teorías estadísticas como teorías de efectos).

**Otros cambios**

- Capítulo 5 §3: genealogía del empate entre realismo y antirrealismo con Losee (Gémino, Ptolomeo, Osiander, Clavius, Kepler) y la versión kuhniana de la meta-inducción.
- Capítulo 2 §5: remisión al capítulo 8 sobre la forma probabilística de C2.
- Capítulo 9: §1 ya no afirma ser el capítulo más extenso (no lo era); §3 remite al 3 §7; §4 remite al 8 §8.
- Capítulo 1 §5: la cita de Kuhn sobre historia y filosofía lleva páginas.
- Notas de lecturas en los capítulos 1, 2, 3, 5, 6, 7, 8 y 9; la del capítulo 4 se amplió.

**Bibliografía agregada** (12 entradas)

`perezransanz1999kuhn`, `kuhn1963funcion`, `taylor1983comprension`, `salmon1967foundations`, `hitchcock2017introductory`, `potochnik2024recipes`, `losee1972introduccion`, `earman1992confirmation`, `lennox1992philosophy`, `mcguire1992scientific`, `glymour1992realism`, `salmon1992explanation`. Se modificó `kuhn1977essential` (ahora la edición castellana, con `origdate`).

**Verificaciones hechas**

- `pandoc --citeproc` compila los capítulos 0 a 9 sin advertencias (HTML con MathJax).
- Las 195 claves del `.bib` están citadas; no hay claves faltantes ni duplicadas.
- Un PDF de prueba de la primera parte entera, con `xelatex`, `scrbook` y `preamble.tex`, compila; las únicas advertencias son glifos de subíndice (₁, ₂, ₙ, ᵢ) ausentes en Pagella itálica, que ya estaban en el capítulo 2 §6.
- Las citas textuales llevan página y se cotejaron con las fuentes: Pérez Ransanz contra una extracción con la paginación corregida (el PDF repite un pliego, las pp. 88-89); Martínez contra las imágenes de sus páginas; Losee contra la edición de 1981, cuya paginación coincide con los extractos de la carpeta; Salmon contra la edición del cincuentenario.
- Los ejemplos numéricos del capítulo 8 se recalcularon: $1-(5/6)^3=91/216$; $1-(35/36)^{24}\approx 0{,}491$; 3/8 en los dos mazos; posterior 0,0089 en el cribado; $0{,}5^8=1/256$; factor de Bayes ≈ 3,95.
- Sin negritas ni subtítulos de nivel 3 en los capítulos 1 a 9; las remisiones «capítulo N (§M)» apuntan a secciones existentes.

**Pendientes que este trabajo dejó planteados**

1. **Correr `quarto render`**: Quarto no está instalado en la máquina donde se hizo este trabajo. Revisar en especial las fórmulas del capítulo 8, las primeras del libro.
2. **Ubicación del repositorio.** En esta máquina el repositorio está en `~/Nextcloud/2026/libro-filosofia-ciencia`, dentro de Nextcloud, lo que contradice la decisión documentada (repositorio en `~/proyectos/libro-filosofia-ciencia`, fuera de Nextcloud, para no corromper el `.git`). No se movió nada.
3. **Extensión del capítulo 8** (~14.000 palabras, el más largo del libro). Evaluar recortes o si conviene convertirlo en `.qmd` con simulaciones (lavado de probabilidades previas, comparaciones múltiples), lo que exigiría los cambios de CI descritos en `ENTORNO.md`.
4. **Verificar datos de edición**: el año del cuadernillo de Teorema con la conferencia de Kuhn (el cuadernillo dice 1980; la bibliografía de Pérez Ransanz, 1979) y los datos de *La libertad de los modernos* de Taylor (Amorrortu, 2005, trad. Horacio Pons, verificados en catálogos; el PDF no trae portada).
5. Potochnik y sus coautores escriben «Ronald Fischer» en su recuadro 9.1; el libro usa la grafía correcta, Fisher.
6. Los recuadros «[Cuadro clasicoso 1]» y «[Cuadro matematicoso 1]» del capítulo 1 §7 siguen vacíos; los capítulos 2 y 6 de Losee y el §3 del capítulo 8 podrían proveer material.
7. Los glifos de subíndice del capítulo 2 §6 no existen en Pagella itálica: conviene escribirlos como fórmulas.
8. Del manual colectivo de Pittsburgh quedan sin usar capítulos útiles para la segunda parte, en particular el de Glymour sobre epistemología androide (capítulo 13).

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
