# Plantilla de Tesis/Tesina - Universidad Politécnica de Victoria (UPV)

Plantilla para la elaboración de tesinas y tesis de ingeniería de la Universidad Politécnica de Victoria, basada en
LaTeX. Está organizada por **secciones que se entregan en revisiones incrementales** y es compatible con el sistema de
revisión asistida por IA del programa.

> **Alumnos: empiecen por [`GUIA_ALUMNO.md`](GUIA_ALUMNO.md).**

## Créditos

Plantilla desarrollada y puesta a disposición de la comunidad estudiantil de la UPV por:

* **Dr. Said Polanco Martagón**
* **Dr. Marco Aurelio Nuño Maganda**

## Estructura

```
main.tex                         ensambla el documento (activa/desactiva secciones según el tipo de proyecto)
configuracion/datos.tex          datos del alumno, tipo de proyecto y estilo de citas   <- se edita
configuracion/preambulo.tex      paquetes, estilos y entorno «guia»                     <- no se edita
institucional/                   portada, cartas y evaluación (se generan con los datos)
secciones/00_preliminares.tex    agradecimientos, resumen, summary              [Revisión 4]
secciones/01_introduccion.tex    introducción, problema, objetivos, justificación, alcances   [Revisión 1]
secciones/02_antecedentes.tex    antecedentes, de la empresa, teóricos, tabla comparativa      [Revisión 1]
secciones/03_marco_teorico.tex   temas tentativos [Rev. 1] y marco teórico completo [Rev. 2]
secciones/04_estado_del_arte.tex solo investigación                                 [Revisión 2]
secciones/05_propuesta_solucion.tex                                                  [Revisión 2]
secciones/06_desarrollo_sistema.tex      proyectos de sistema                        [Revisión 3]
secciones/06_diseno_experimentos.tex     proyectos de investigación                  [Revisión 3]
secciones/07_conclusiones.tex    conclusiones y trabajo futuro                       [Revisión 4]
referencias/referencias.bib      bibliografía
ejemplos/ejemplos_latex.tex      ejemplos de tablas, figuras, ecuaciones, algoritmos y citas
```

Cada archivo de `secciones/` incluye una **guía** (recuadro amarillo) con lo que debe contener la sección, las preguntas
que debe responder, la extensión mínima y los errores frecuentes. Se ocultan con `\guiasfalse` en
`configuracion/preambulo.tex`.

## Cómo obtener la plantilla

```bash
git clone https://github.com/<usuario>/<repositorio>.git
cd <repositorio>
```

(Si hay un *fork* propio, clónalo de la misma manera.)

## Compilación

La bibliografía usa **biblatex con biber** (ya no `bibtex`). Se recomienda un editor que lo haga automáticamente
(Overleaf, TeXstudio o VS Code con LaTeX Workshop). Desde la terminal, lo más simple es:

```bash
latexmk -pdf main.tex
```

Equivalente manual:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

Requiere una instalación de TeX Live con los paquetes `biblatex`, `biber`, `csquotes`, `tcolorbox`, `pdfpages`,
`enumitem` y `booktabs` (todos incluidos en TeX Live completo y en Overleaf).

## Para el director de tesis: compatibilidad con el sistema de revisión

El sistema lee los siguientes elementos de la plantilla; **no deben eliminarse**:

* `\newcommand{\TipoProyecto}{...}` y `\newcommand{\NombreProyecto}{...}` en `configuracion/datos.tex`.
* Los comentarios `% audit:req=<id>` junto a los títulos de sección, que identifican cada requisito de la revisión
  (los ids están definidos en `config/revisiones.yaml` del sistema de revisión).
* El entorno `guia`: su contenido se ignora al evaluar (no cuenta como texto del alumno).
* La carpeta `institucional/`, que el sistema no revisa.
