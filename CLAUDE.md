# CLAUDE.md

Guía para Claude Code (y para cualquier persona) que actualice este repositorio.

## Qué es

Curso **Geotecnia para geólogos** (Ingeniería Geológica, Universidad Nacional de Colombia, sede Medellín, Prof. Edier Aristizábal). Un solo repositorio contiene tres productos:

| Producto | Fuente en `main` | URL publicada |
|---|---|---|
| Página del curso (Jekyll, tema minimal) | `index.md`, `_config.yml`, `Programa_GEOTECNIA.pdf`, `assets/` | https://edieraristizabal.github.io/Geotecnia/ |
| Diapositivas (Reveal.js) | `html/Geotecnia.html`, `html/images/`, `html/dist/`, `html/plugin/` | https://edieraristizabal.github.io/Geotecnia/html/Geotecnia.html |
| Libro (Jupyter Book 1.x) | `libro/` | https://edieraristizabal.github.io/Geotecnia/libro/ |

Remoto: https://github.com/edieraristizabal/Geotecnia

## Ramas: dónde hacer pull y push

**Siempre se trabaja en `main`.** Ese es el único lugar donde se edita, se hace `git pull` y `git push`, tanto para cambios de la página como de las diapositivas o del libro.

**Nunca editar ni hacer push a `gh-pages` a mano.** Esa rama la genera el workflow `.github/workflows/deploy.yml` en cada push a `main`: construye Jekyll en `_site/`, construye el libro y lo copia en `_site/libro/`, y publica todo en `gh-pages` con `force_orphan` (cualquier cambio manual en `gh-pages` se pierde en el siguiente despliegue).

¿Por qué no "main = página y gh-pages = libro"? GitHub Pages sirve un solo sitio por repositorio desde una sola fuente. Si el libro se publicara solo en `gh-pages`, la página del curso dejaría de verse. Por eso ambos se combinan en el Action.

Flujo normal:

```bash
git pull origin main
# ... editar ...
git add -A
git commit -m "Descripción del cambio"
git push origin main      # el Action publica en 2 a 4 minutos
```

Para revisar el despliegue: pestaña **Actions** del repositorio. En **Settings → Pages** la fuente debe ser *Deploy from a branch*, rama `gh-pages`, carpeta `/ (root)`.

## Estructura

```
Geotecnia/
├── CLAUDE.md                  # este archivo
├── README.md
├── _config.yml                # Jekyll: tema minimal; excluye libro/, build/, *.tex
├── index.md                   # página del curso: descripción, enlaces, contenido, evaluación
├── Programa_GEOTECNIA.tex     # programa en LaTeX (fuente)
├── Programa_GEOTECNIA.pdf     # programa compilado (se publica; se enlaza desde index.md y las diapositivas)
├── assets/img/unal2.png       # logo UNAL (programa, diapositivas)
├── html/
│   ├── Geotecnia.html         # presentación Reveal.js única, un bloque <section> por tema
│   ├── images/<código>/*.webp # figuras extraídas de las presentaciones de CLASES (código = prefijo del pptx: 0, 1A, 1B, ..., 13B, RESISTENCI, NSR10)
│   ├── dist/, plugin/         # motor Reveal.js 4 (menu, math, notes, ...), copiado del curso de Geomorfología
├── libro/
│   ├── _config.yml            # Jupyter Book 1.x (no 2.x): bibtex, MyST, baseurl .../Geotecnia/libro/
│   ├── _toc.yml               # partes y capítulos
│   ├── requirements.txt       # jupyter-book>=1.0.2,<2 y sphinxcontrib-bibtex
│   ├── references.bib         # bibliografía citada con {cite:t}`clave` / {cite:p}`clave`
│   ├── intro.md
│   ├── 01_introduccion.md ... 15_empujes.md, A_ensayos.md, referencias.md
│   └── images/<código>/*.webp, images/logo.png
├── .github/workflows/deploy.yml
└── build/                     # salida de pdflatex (ignorada por git)
```

Fuera del repo, en la carpeta del curso (`C:\Users\edier\Documents\CATEDRA\GEOTECNIA`), está el material fuente que **no** se sube: `CLASES/` (pptx originales), `LIBROS GUIA_Geotecnia/` (≈1 GB, con derechos de autor), `DOCUMENTOS DE REFERENCIA/`, `LECTURAS/`, `PARCIALES/` y el programa original en Word. No copiar estos archivos al repo.

## Correspondencia de temas

| # | Tema | Diapositivas (pptx de CLASES) | Capítulo del libro |
|---|---|---|---|
| 1 | Introducción | 0_INTRODUCCION, NSR-10 | 01_introduccion |
| 2 | Mecánica de suelos | 1A, 1B | 02_suelos |
| 3 | Mecánica de rocas | 2A, 2B | 03_rocas |
| 4 | Agua en suelo y macizo | 3A, 3B, 3C | 04_agua |
| 5 | Estado de esfuerzos | 4 | 05_esfuerzos |
| 6 | Esfuerzos efectivos | 5 | 06_esfuerzos_efectivos |
| 7 | Distribución de esfuerzos | 6 | 07_distribucion |
| 8 | Compactación | 7 | 08_compactacion |
| 9 | Consolidación | 8 | 09_consolidacion |
| 10 | Cimentaciones | 9A, 9B | 10_cimentaciones |
| 11 | Resistencia al cortante | 10A, 10B | 11_resistencia_corte |
| 12 | Resistencia de rocas | RESISTENCIA DE ROCAS | 12_resistencia_rocas |
| 13 | Movimientos en masa | 11 | 13_movimientos_masa |
| 14 | Estabilidad de laderas | 12A–12D (+ diapositiva pseudoestática) | 14_estabilidad |
| 15 | Empujes y muros | 13A, 13B | 15_empujes |
| — | Ensayos geotécnicos | — | A_ensayos |

## Cómo actualizar

**Página del curso.** Editar `index.md` (horario y aula están "por definir"). Si cambia la evaluación, actualizarla en los tres lugares donde aparece: `index.md`, `Programa_GEOTECNIA.tex` (y recompilar el PDF) y la diapositiva "Evaluación" al inicio de `html/Geotecnia.html`.

**Programa.** Editar `Programa_GEOTECNIA.tex` y compilar desde la raíz del repo:

```bash
pdflatex -interaction=nonstopmode -output-directory=build Programa_GEOTECNIA.tex
cp build/Programa_GEOTECNIA.pdf .
```

Se hace commit del `.pdf` (el Action no compila LaTeX).

**Diapositivas.** Editar `html/Geotecnia.html` directamente. Cada tema es un `<section>` horizontal con una portada `<h1>` y diapositivas verticales `<section>`; las diapositivas generadas desde los pptx llevan `data-src="<código>:<n.º de diapositiva>"` para ubicar su origen. Ecuaciones con MathJax: `\( ... \)` en línea y `$$ ... $$` en bloque. Clases CSS disponibles (definidas en el `<head>`): `figs`, `cols2`, `txt`, `txt small`, `tabla`, `nota`, `fuente`. Nuevas imágenes: convertirlas a `.webp` (ancho máximo ~1400 px) y guardarlas en `html/images/<código>/`. Previsualizar con un servidor local desde la raíz del repo (`python -m http.server`) y abrir `http://localhost:8000/html/Geotecnia.html`.

**Libro.** Los capítulos son MyST Markdown en `libro/`. Convenciones: cada capítulo empieza con una etiqueta `(cap-xxx)=` y un bloque `:::{important}` de objetivos; los ejemplos resueltos van en `:::{admonition} Ejemplo resuelto: ... ` con `:class: note`; las figuras con ```` ```{figure} images/<código>/<archivo>.webp ```` y leyenda con la fuente; las citas con `{cite:t}` / `{cite:p}` y la clave debe existir en `references.bib`. Un capítulo nuevo debe agregarse a `_toc.yml`. El público son geólogos: priorizar la interpretación geológica y los ejemplos con números verificados. Para compilar localmente:

```bash
# entorno ya creado en C:\Users\edier\.jbenv (Jupyter Book 1.0.4)
C:\Users\edier\.jbenv\Scripts\jupyter-book.exe build libro
# abrir libro/_build/html/index.html
```

El Action compila con `--warningiserror` y, si hay advertencias, vuelve a compilar sin esa opción para no bloquear la publicación; conviene revisar el log y corregirlas.

## Preferencias del autor

- Proponer los cambios de contenido del curso y esperar aprobación antes de editarlos.
- Prosa en párrafos, español, sin rayas (em dash): usar comas o paréntesis.
- Las figuras nuevas se buscan primero en los tableros de Pinterest del autor o en los pptx de `CLASES/`.

## Pendientes conocidos

- Horario y aula del curso están "por definir" en `index.md`, el programa y las diapositivas.
- Las diapositivas se generaron desde los pptx de `CLASES/` con un script; las figuras que contienen texto en inglés (copiadas de libros) no se pueden traducir.

## Registro de cambios

Cada cambio al repositorio se anota aquí, el más reciente primero, con el formato `- **AAAA-MM-DD**: qué se cambió y por qué (archivos principales).` Esta sección es la memoria del curso entre sesiones: leerla antes de empezar a trabajar.

- **2026-10-24**: Interfaz en español: `_layouts/default.html` traducido ("Ver el proyecto en GitHub", "Este proyecto es mantenido por", `lang` = es), reemplaza el texto en inglés del tema minimal de Jekyll. Si git falla con `bad object refs/desktop.ini`, borrar los `desktop.ini` dentro de `.git/` (`find .git -name desktop.ini -delete`): los crea Windows/Google Drive.
- **2026-10-24**: Revisión de idioma: la única diapositiva con texto en inglés (cita "Geotechnical Engineering is the art...", diapositiva `0:5`) se tradujo al español. Se mantienen en inglés los títulos de lecturas y referencias bibliográficas. Se agregaron a este archivo las secciones de pendientes y registro de cambios.
- **2026-10-24**: `_config.yml` con `url` y `baseurl: /Geotecnia` para que el tema de Jekyll cargue el CSS y el logo (la página se veía sin estilos).
- **2026-10-24**: Nueva evaluación (trabajo 1 sobre el perfil de meteorización de una ladera: escrito 10 % y presentación 20 %; trabajo 2 de análisis de estabilidad de la misma ladera con escenarios de agua y sismo: escrito 10 % y presentación 20 %; parcial teórico 30 %; participación 10 %) en `index.md`, `Programa_GEOTECNIA.tex/.pdf` y diapositivas; sección de análisis pseudoestático en `libro/14_estabilidad.md` y diapositiva correspondiente.
- **2026-10-24**: Creación del repositorio: página Jekyll, programa en LaTeX, presentación Reveal.js generada desde los pptx de `CLASES/`, libro de 15 capítulos y apéndice de ensayos, y GitHub Action que publica página y libro en `gh-pages`.
