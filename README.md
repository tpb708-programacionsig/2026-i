# TPB708 - Programación SIG - 2026-I

Sitio web del curso TPB708 Programación de Sistemas de Información Geográfica, de la Maestría en Sistemas de Información Geográfica y Teledetección de la Universidad Nacional y la Universidad de Costa Rica.

## Enlace al sitio web

[https://tpb708-programacionsig.github.io/2026-i/](https://tpb708-programacionsig.github.io/2026-i/)

## Desarrollo local

Crear el ambiente Conda:

```bash
conda create -n tpb708-programacionsig -c conda-forge --strict-channel-priority mamba
conda activate tpb708-programacionsig
mamba install -c conda-forge --strict-channel-priority python jupyter jupyter-book nodejs
```

Iniciar el servidor de desarrollo:

```bash
conda activate tpb708-programacionsig
jupyter-book start
```

Construir el sitio:

```bash
conda activate tpb708-programacionsig
jupyter-book build .
```

## Licencia

Este contenido se comparte bajo la licencia [Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.es).
