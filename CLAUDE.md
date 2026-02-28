# CLAUDE.md

Este archivo proporciona orientación a Claude Code (claude.ai/code) para trabajar con el código de este repositorio.

El idioma principal del proyecto es **español**. Todo el contenido, mensajes de commit y comunicación deben estar en español.

## Descripción del proyecto

Sitio web del curso TPB708 - Programación SIG (Sistemas de Información Geográfica), curso de maestría de la Universidad Nacional y la Universidad de Costa Rica.

## Sistema de construcción

Sitio de documentación basado en **Jupyter Book v2** (que usa MyST Markdown internamente) con la plantilla `book-theme`, desplegado en GitHub Pages.

```bash
# Crear ambiente Conda
conda create -n tpb708-programacionsig -c conda-forge --strict-channel-priority mamba
conda activate tpb708-programacionsig
mamba install -c conda-forge --strict-channel-priority python jupyter jupyter-book nodejs

# Construir el sitio
jupyter-book build .

# Iniciar servidor de desarrollo local
jupyter-book start
```

La salida de la construcción se genera en `_build/html/`.

## Configuración

- `myst.yml` — Configuración principal: tabla de contenidos del proyecto, plantilla del sitio y opciones. Las entradas de la tabla de contenidos pueden ser archivos locales o URLs externas (ej. cuadernos de Google Colab).

## Despliegue

Automatizado mediante GitHub Actions (`.github/workflows/deploy.yml`). Los push a `main` ejecutan la construcción y el despliegue a GitHub Pages. Requiere Node.js 18.x.

## Estructura del contenido

- `index.md` — Página principal
- `contenidos/` — Contenido del curso organizado por secciones temáticas (ej. `contenidos/informacion-general/`)
- El contenido externo se enlaza mediante URLs en la tabla de contenidos de `myst.yml` (cuadernos de Google Colab)
