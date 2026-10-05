# Guía del alumno: cómo escribir y entregar tu tesina

Esta plantilla organiza tu tesina en **secciones que se entregan por avances (revisiones)**. En cada revisión tu director
revisa solo las secciones que corresponden a esa entrega, apoyado por un sistema automático que verifica cuáles
secciones están completas y cumple con el formato. **La decisión final siempre es de tu director.**

## 1. Primeros pasos

1. Copia esta carpeta completa (o clónala) y ábrela con tu editor de LaTeX (Overleaf, TeXstudio, VS Code + LaTeX Workshop).
2. Abre `configuracion/datos.tex` y llena **todos** tus datos: nombre, matrícula, título, empresa, asesores, fechas.
3. En ese mismo archivo define `\TipoProyecto`:
   - `sistema` → página web, sistema web, API, sistema de escritorio o app móvil.
   - `investigacion` → algoritmo, modelo de aprendizaje de máquina u otra investigación.
   - Y el estilo de citas `\EstiloCitas`: `ieee` (por defecto) o `apa`, según indique tu director.
4. Si tu proyecto es de **investigación**, en `main.tex` activa `04_estado_del_arte` y `06_diseno_experimentos` (y comenta
   `06_desarrollo_sistema`). Las instrucciones están como comentarios en `main.tex`.
5. Compila: `latexmk -pdf main.tex` (o el botón de compilar de tu editor). La bibliografía usa **biber**.

## 2. Qué hay en cada carpeta

| Carpeta o archivo | Para qué sirve | ¿Lo editas? |
|---|---|---|
| `configuracion/datos.tex` | Tus datos, tipo de proyecto y estilo de citas | **Sí** |
| `secciones/*.tex` | El contenido de tu tesina, una sección por archivo | **Sí** (aquí escribes) |
| `referencias/referencias.bib` | Tu bibliografía | **Sí** |
| `img/` | Tus figuras e imágenes | **Sí** |
| `main.tex` | Ensambla todo; solo activas/desactivas secciones según tu tipo de proyecto | Poco |
| `configuracion/preambulo.tex` | Paquetes y estilos | No |
| `institucional/` | Portada, cartas y evaluación (se generan con tus datos) | No |
| `cartas/`, `membretes/`, `logos/` | Documentos institucionales | Solo sustituir las cartas por las tuyas |
| `ejemplos/ejemplos_latex.tex` | Ejemplos de tablas, figuras, ecuaciones, algoritmos y citas para copiar | No (consulta) |

## 3. Qué entregar en cada revisión

Todas las revisiones son **acumulativas**: la siguiente incluye lo anterior (ya corregido).

| Revisión | Secciones (archivo) | Mínimos que se verifican |
|---|---|---|
| **1** | Introducción, Planteamiento del problema, Objetivo general y específicos, Justificación, Alcances y limitaciones (`01_introduccion`); Antecedentes del problema, de la empresa, teóricos y **tabla comparativa** (`02_antecedentes`); **Temas tentativos** del marco teórico (`03_marco_teorico`) | Introducción 150 palabras · Planteamiento 120 · Objetivos 40 · Justificación 100 · Alcances y limitaciones 60 · Antecedentes del problema 120 · de la empresa 100 · teóricos 150 · tabla comparativa presente · temas tentativos 25 |
| **2** | Marco teórico completo (`03`); Propuesta de solución (`05`). **Solo investigación:** Estado del arte con tabla comparativa y conclusión (`04`) | Marco teórico 400 palabras · Propuesta 150 · Estado del arte 300 palabras, **≥ 10 artículos de revista** (`@article`), **sin artículos de congreso** (`@inproceedings`), tabla comparativa y conclusión |
| **3 (sistema)** | Desarrollo del sistema (`06_desarrollo_sistema`): casos de uso, base de datos, actividades, secuencia y pantallas con su explicación | Desarrollo 300 palabras · cada diagrama con **al menos una figura** y explicación · pantallas 150 palabras |
| **3 (investigación)** | Diseño de experimentos, Resultados experimentales y sus Conclusiones (`06_diseno_experimentos`) | Diseño 250 · Resultados 200 · Conclusiones de resultados 60 |
| **4** | **Todas** las secciones anteriores, revisadas y terminadas, sin excepción, más Conclusiones y Trabajo futuro (`07`) y Resumen/Summary (`00_preliminares`) | Conclusiones 150 · Trabajo futuro 50 · Resumen 120 palabras |
| **Final** | Documento completo con todas las correcciones | Todo lo anterior |

Los mínimos son para que el sistema detecte que **escribiste** la sección; no garantizan buena calidad. Escribe lo que
haga falta para responder todas las preguntas de la guía.

## 4. Cómo usar las guías de cada sección

Cada archivo de `secciones/` trae recuadros amarillos **«Guía»** que dicen qué debe ir en la sección, qué preguntas debes
responder, la extensión mínima, los errores más comunes y cómo se revisa.

- Escribe tu texto **fuera** del recuadro (en el lugar marcado `% >>> ESCRIBE AQUÍ ... <<<`).
- El sistema de revisión **ignora todo lo que esté dentro de `\begin{guia} ... \end{guia}`**, así que escribir ahí no cuenta.
- Para ocultar las guías en el PDF cambia `\guiastrue` por `\guiasfalse` en `configuracion/preambulo.tex`. Puedes
  borrarlas al final, pero no es obligatorio.
- **No cambies los títulos** de las secciones ni borres los comentarios `% audit:req=...` junto a ellos: con eso el sistema
  sabe qué sección es cuál. Puedes agregar subsecciones propias donde las necesites.

## 5. Reglas de formato que se verifican automáticamente

Revisa esta lista antes de cada entrega:

- [ ] Toda **figura y tabla** tiene `\caption` y `\label`, y se menciona en el texto con `\ref` (por ejemplo
      `Figura~\ref{fig:arquitectura}`). **No escribas «Figura 3» a mano.**
- [ ] Toda cita `\cite{clave}` existe en `referencias/referencias.bib`, y no tienes referencias sin citar.
- [ ] Las **tablas** usan `booktabs` (`\toprule`, `\midrule`, `\bottomrule`), sin líneas verticales.
- [ ] Todas las imágenes existen en `img/` y se ven legibles al imprimir.
- [ ] No hay marcadores pendientes (`TODO`, `FIXME`, `PENDIENTE`) ni secciones vacías.
- [ ] Los archivos de imagen y de código tienen nombres sin espacios ni acentos.
- [ ] El documento compila sin errores.

## 6. Referencias bibliográficas

- Agrega cada fuente a `referencias/referencias.bib` (dentro hay ejemplos comentados por tipo).
- Usa `@article` para **revistas científicas**, `@inproceedings` para congresos, `@book` para libros y `@online` para
  páginas de Internet (con `urldate`).
- Cita en el texto con `\cite{clave}` (IEEE) o `\parencite{clave}` / `\textcite{clave}` (APA).
- Prefiere fuentes arbitradas y recientes; evita depender de blogs y de páginas comerciales.

## 7. Cómo entregar un avance

1. Compila y revisa que no haya errores.
2. Comprime la carpeta completa (sin los archivos temporales `.aux`, `.log`, etc.) o comparte tu proyecto de Overleaf.
3. Indica a qué **Revisión** corresponde.
4. Recibirás un reporte con: el **cumplimiento** de cada sección solicitada (cumple, parcial o falta), el **dictamen** de la
   revisión, las **correcciones prioritarias** (cada una con archivo y línea) y las recomendaciones para la siguiente.
5. Corrige y vuelve a entregar cuando tu director lo indique.

## 8. Preguntas frecuentes

**¿Puedo agregar más secciones?** Sí, como subsecciones dentro de las existentes o como secciones nuevas. No cambies los
títulos ni el orden de las obligatorias.

**¿Qué pasa si mi proyecto no encaja en «sistema» o «investigación»?** Consulta con tu director cuál es el más cercano.

**¿Puedo usar inteligencia artificial para escribir?** Sigue la política de tu director y de la universidad. El texto debe
ser tuyo y debes poder explicarlo; las fuentes deben existir y haber sido leídas por ti.

**El sistema dice que una sección «no tiene contenido escrito» pero sí escribí.** Revisa que tu texto esté fuera del
recuadro de la guía y que no hayas cambiado el título de la sección.
