# Miniconda

## Descripción

Miniconda es un instalador mínimo para el sistema de gestión de paquetes y entornos virtuales [conda](https://docs.conda.io). Es una versión reducida de [Anaconda](https://www.anaconda.com/) que incluye solamente conda, Python, los paquetes de los que ambos dependen y unos pocos paquetes adicionales.

## Instalación

1. Ingrese al sitio web de [Miniconda](https://docs.anaconda.com/miniconda/) y descargue el instalador correspondiente a su sistema operativo.
2. Ejecute el instalador y siga las instrucciones. Se recomienda:
    - Elegir la opción **Just Me** (para que se instale en el directorio del usuario).
    - Aceptar las demás opciones que presenta por defecto el instalador.
3. Al finalizar la instalación, abra una terminal con conda habilitado:
    - **Windows**: abra **Anaconda Prompt** desde el menú Inicio (no use CMD ni PowerShell directamente, ya que no tienen conda habilitado por defecto).
    - **macOS / Linux**: abra la terminal del sistema.

## Creación de un entorno virtual

Ejecute los siguientes comandos en una terminal con conda habilitado (Anaconda Prompt en Windows).

```shell
# Actualización de conda
conda update -n base conda

# Instalación de mamba (gestor de paquetes más rápido que conda)
conda install -n base -c conda-forge mamba

# Creación del entorno
conda create -n geopython

# Activación del entorno
conda activate geopython

# Configuración del canal conda-forge como prioritario
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict
```

Una vez creado y activado el entorno, instale los paquetes necesarios para el curso:

```shell
# Paquetes generales
mamba install git python jupyter jupyter-book ghp-import

# Ciencia de datos
mamba install numpy pandas matplotlib seaborn plotly

# Datos geoespaciales vectoriales
mamba install gdal fiona shapely geopandas pyarrow

# Datos geoespaciales raster
mamba install rasterio xarray rioxarray earthpy xarray-spatial

# Bases de datos
mamba install duckdb

# Mapas interactivos y aplicaciones web
mamba install pystac-client python-graphviz folium leafmap lonboard streamlit
```

Al finalizar la sesión de trabajo, desactive el entorno:

```shell
conda deactivate
```

## Instalación de paquetes adicionales

Si durante el curso necesita instalar paquetes adicionales, active el entorno y use `mamba install`:

```shell
# Activación del entorno
conda activate geopython

# Instalación de paquetes (ejemplo)
mamba install nombre-del-paquete

# Desactivación del entorno (al finalizar la sesión de trabajo)
conda deactivate
```

## Otros comandos de conda

```shell
# Información general sobre conda
conda info

# Ayuda general sobre los comandos de conda
conda --help

# Ayuda sobre un comando
# Sintaxis: conda <COMANDO> --help
# Ejemplo:
conda install --help

# Lista de entornos instalados
conda env list

# Lista de paquetes instalados en el entorno activo
conda list

# Almacenamiento de un entorno en un archivo de texto
# Sintaxis: conda list --explicit > <NOMBRE_ARCHIVO>
# Ejemplo:
conda list --explicit > miambiente.txt

# Creación de un entorno a partir de un archivo de texto
# Sintaxis: conda create --name <NOMBRE_ENTORNO> --file <NOMBRE_ARCHIVO>
# Ejemplo:
conda create --name miambiente --file miambiente.txt

# Borrado de un entorno y de todos sus archivos
# Sintaxis: conda env remove --name <NOMBRE_ENTORNO> --all
# Ejemplo:
conda env remove --name miambiente --all
```

Hay una lista completa de comandos de conda en:
[Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)
