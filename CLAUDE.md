# CLAUDE.md

Este archivo proporciona orientación a Claude Code (claude.ai/code) para trabajar con el código de este repositorio.

El idioma principal del proyecto es **español**. Todo el contenido, mensajes de commit y comunicación deben estar en español.

## Descripción del proyecto

Sitio web del curso TPB708 - Programación en SIG (Sistemas de Información Geográfica), curso de maestría de la Universidad Nacional y la Universidad de Costa Rica.

## Sistema de construcción

Sitio de documentación basado en **Jupyter Book v2** (que usa MyST Markdown internamente) con la plantilla `book-theme`, desplegado en GitHub Pages.

```bash
# Crear ambiente Conda
conda create -n tpb708-programacionsig -c conda-forge --strict-channel-priority mamba
conda activate tpb708-programacionsig
mamba install -c conda-forge --strict-channel-priority python jupyter jupyter-book nodejs

# Construir el sitio HTML estático
jupyter-book build --html

# Iniciar servidor de desarrollo local (puerto 3000; pasa a 3001 si está ocupado)
jupyter-book start
```

La salida de la construcción se genera en `_build/html/`.

## Configuración

- `myst.yml` — Configuración principal: tabla de contenidos del proyecto, plantilla del sitio y opciones. Las entradas de la tabla de contenidos pueden ser archivos locales o URLs externas.

## Despliegue

Automatizado mediante GitHub Actions (`.github/workflows/deploy.yml`). Los push a `main` ejecutan la construcción y el despliegue a GitHub Pages. Requiere Node.js 24.x.

## Estructura del contenido

- `index.md` — Página principal
- `contenidos/` — Contenido del curso organizado por secciones temáticas:
  - `contenidos/informacion-general/` — Programa del curso
  - `contenidos/i-introduccion-ciencia-datos-programacion/` — Sección I del curso
  - `contenidos/software/` — Guías de instalación de software
- Las imágenes locales se almacenan en subdirectorios `img/` dentro de cada sección (ej. `contenidos/i-introduccion-ciencia-datos-programacion/img/`)

## Convenciones de formato

- Las figuras se definen con HTML `<figure>` y `<figcaption>`, no con sintaxis de imagen Markdown. Ejemplo:

  ```html
  <figure style="text-align: center;">
    <img src="img/nombre.png" alt="Texto alternativo">
    <figcaption><strong>Figura N</strong>. Descripción.</figcaption>
  </figure>
  ```

- Las referencias bibliográficas se separan con `\` + `\` entre cada una
- Evitar enlaces con `doi.org` en las URLs, ya que MyST los detecta y auto-genera una sección "References". Usar la URL directa del editor (ej. `https://dl.acm.org/doi/...` en lugar de `https://doi.org/...`)
