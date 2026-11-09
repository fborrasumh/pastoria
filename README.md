# PastorIA

Agroecología pecuaria: pastoreo rotacional, insumos orgánicos e indicadores de sostenibilidad. Aplicación web de un solo fichero, sin servidor.

**Usar la app:** https://fborrasumh.github.io/pastoria/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24093769.svg)](https://doi.org/10.5281/zenodo.24093769)

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **Temas del sílabo.** Los catorce temas de Agroecología Pecuaria en el orden de las sesiones, agrupados por bloque, cada uno con una pregunta para el trabajo de campo y, cuando procede, lecturas con DOI comprobado.
- **Planificador.** Pastoreo rotacional (unidades animales, carga animal, capacidad de carga sostenible, demanda diaria, número y área de potreros, días que alimenta un potrero, nitrógeno excretado por hectárea), mezcla de compost (relación C/N y kilos de material que faltan para el objetivo) y sistema silvopastoril (árboles por hectárea, cobertura de copas, forraje de ramoneo), con avisos de sobrecarga, déficit de forraje, C/N fuera de rango y exceso de sombra.
- **Indicadores de sostenibilidad.** El proyecto de aula del sílabo: quince indicadores en cinco dimensiones (biodiversidad funcional, salud del suelo, bienestar animal, integración árbol-animal-suelo, económica y social), puntuados de 1 a 5 para dos fincas. El código calcula los índices por dimensión y el global, dibuja el radar y marca los puntos críticos. Exporta a Word y CSV.
- **Retos con solución calculada.** Diez tipos de problema (biomasa por el método del marco, demanda del hato, número de potreros, días de ocupación, carga animal, capacidad de carga, C/N de una mezcla, nitrógeno por hectárea, árboles por hectárea, punto de equilibrio). Cada estudiante recibe datos propios a partir de su código; la app reconoce la solución y diagnostica los errores típicos. El profesorado imprime las hojas y descarga las soluciones en CSV.
- **Práctica adaptativa.** 28 preguntas trilingües por unidad y nivel de Bloom. Un modelo de dominio por unidad (tipo Elo, con olvido) elige la siguiente pregunta, intercala unidades y repasa las falladas; la app explica por qué toca cada pregunta.
- **Ensayo argumentativo.** Con la estructura del sílabo (introducción, metodología, resultados, análisis, conclusiones y referencias). Comprueba la forma de las referencias (año, DOI, formato APA) y cuenta las de los últimos cinco años (el sílabo pide al menos cinco). Las tablas de indicadores y, si se usaron, los cálculos de planificación se insertan solos en el Word.
- **Revisión formativa con IA (opcional).** La IA comenta fortalezas y mejoras citando el ensayo; no pone nota.
- **Sílabo.** Ficha literal, resultado de aprendizaje, calendario con la próxima sesión marcada, evaluación, bibliografía comentada, revisión crítica del documento y propuesta de resultados de aprendizaje medibles.
- **Datos y profesorado.** Exportación anónima del registro de práctica, analítica de ítems (dificultad, discriminación, distractores que nadie elige) y banco de ítems para Moodle (GIFT).

## Qué calcula el código y qué hace la IA

Todos los números (planificador, índices, soluciones y diagnóstico de los retos, modelo de dominio) los calcula el código con fórmulas explícitas; la IA no calcula nada. La IA solo interviene en la revisión del ensayo, con la clave de cada persona (OpenAI, Google Gemini o Anthropic Claude). El código comprueba que cada cita existe en el ensayo, señala las cifras que no están ni en el ensayo ni en los cálculos y descarta los comentarios que ponen nota.

## Privacidad

Todo se guarda en el navegador (IndexedDB). Solo sale información si se pide la revisión con IA: el texto del ensayo, con correos, documentos y teléfonos enmascarados, tras un aviso que muestra lo que se va a enviar. La exportación de datos de práctica usa un seudónimo aleatorio y no contiene nombres ni texto libre.

## Límites

- Los valores de referencia (consumo, eficiencia de utilización, crecimiento del pasto, contenidos de C y N, nitrógeno excretado) son orientativos: dependen del clima, la altitud, las especies y el manejo. No sustituyen el criterio técnico ni las mediciones de cada finca.
- La escala de indicadores es de observación para aprender, inspirada en el marco MESMIS; no es un instrumento validado.
- La comprobación de referencias es solo de forma: la app no consulta ninguna base de datos.
- La app no se ha probado todavía con estudiantes reales ni con una clave de IA real (la IA se probó simulada). Su efecto en el aprendizaje está por medir. Para publicar con los datos que exporta hacen falta aprobación de un comité de ética, consentimiento informado y, idealmente, un diseño preregistrado con grupo de comparación.

## Pruebas realizadas

29 437 comprobaciones de lógica en Node (300 variantes por tipo de reto: solución, redondeo, errores típicos diagnosticados y sin colisiones, determinismo; valores conocidos del planificador e índices; modelo de dominio: mismos eventos, misma ruta) y una prueba de punta a punta en Chromium: IA simulada de los tres proveedores (con una cita inventada, una cifra inventada y un comentario con nota), error 429, idioma pedido a la IA, exportaciones Word/CSV/JSON/GIFT sin red, persistencia, funcionamiento sin conexión, cobertura de traducciones (estáticas y dinámicas), móvil (390 px) en los tres idiomas y accesibilidad con axe-core (WCAG 2.2 A/AA, cero infracciones). Primera pantalla útil en unos 0,3 s con la CPU ralentizada ×4.

## Adaptarla a otra asignatura o universidad

El currículo está en datos: `src/datos.js` (temas, herramientas, indicadores, sílabo), `src/items.js` (preguntas) y `src/calc.js` (`RETOS`). Se cambian esos ficheros, se traduce en `src/i18n.js` y se monta con `python3 build.py`.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Hernán Rigoberto Benavides Rosales (Universidad Politécnica Estatal del Carchi).

Origen de la idea: a partir del sílabo de Agroecología Pecuaria (Itinerario 2, 0811BIT1AP6UP-AJ2025, nivel 6, Carrera de Agropecuaria, UPEC) del profesor Hernán Rigoberto Benavides Rosales: sus bloques de diseño de sistemas pecuarios sostenibles, insumos orgánicos, ganadería mayor y menor ecológica, el proyecto de aula de caracterización agroecológica de una unidad pecuaria y el ensayo argumentativo.

Roles (CRediT): Hernán Rigoberto Benavides Rosales, conceptualización y recursos (sílabo y contenidos de la asignatura); Fernando Borrás Rocher, software y metodología.

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Hernán Rigoberto Benavides Rosales [0000-0001-9236-3076](https://orcid.org/0000-0001-9236-3076)

## Cómo citar

Borrás Rocher, F. y Benavides Rosales, H. R. (2026). *PastorIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.24093769](https://doi.org/10.5281/zenodo.24093769)

## Licencia

MIT. Véase [LICENSE](LICENSE). Los contenidos pedagógicos se publican con la misma licencia.
