# Streamlit: marco de trabajo para desarrollo de aplicaciones web de ciencia de datos y aprendizaje automatizado

## Trabajo previo

### Lecturas

Streamlit Inc. (s. f.). *Streamlit documentation — Get started*. [https://docs.streamlit.io/get-started](https://docs.streamlit.io/get-started)
\
\
Streamlit Inc. (s. f.). *Create an app*. [https://docs.streamlit.io/get-started/tutorials/create-an-app](https://docs.streamlit.io/get-started/tutorials/create-an-app)

## Introducción

[Streamlit](https://streamlit.io/) es un marco de trabajo (*framework*) para el desarrollo de aplicaciones web basadas en el lenguaje de programación Python. El desarrollo en Streamlit no requiere de conocimientos de tecnologías web como HTML, CSS o JavaScript.

La plataforma [Streamlit Cloud](https://streamlit.io/cloud) permite compartir y publicar aplicaciones Streamlit, conjuntamente con el mantenimiento del código fuente en [GitHub](https://github.com/). Las aplicaciones Streamlit también pueden ser puestas en producción en otras plataformas, como [Heroku](https://www.heroku.com/) y [AWS](https://aws.amazon.com/).

Streamlit es especialmente adecuado para publicar, en una interfaz interactiva, los productos de análisis de datos desarrollados a lo largo del curso. Una aplicación Streamlit puede integrar, en una sola página web, las **tablas** de datos elaboradas con [pandas](https://pandas.pydata.org/), los **gráficos** generados con bibliotecas como [Matplotlib](https://matplotlib.org/) y [Plotly](https://plotly.com/python/), y los **mapas** interactivos producidos con [folium](https://python-visualization.github.io/folium/) y [leafmap](https://leafmap.org/). De esta forma, las destrezas adquiridas en las tareas anteriores —procesamiento de datos con pandas, visualización con Plotly y elaboración de mapas con folium y leafmap— se combinan en el desarrollo de una aplicación interactiva completa.

## Instalación

Puede instalarse mediante pip, conda o mamba:

```shell
# Con pip
pip install streamlit

# Con conda
conda install -c conda-forge streamlit

# Con mamba
mamba install -c conda-forge streamlit
```

Se recomienda crear un entorno virtual con Streamlit y otras bibliotecas requeridas. El siguiente bloque de código contiene los comandos necesarios para crear un ambiente conda para desarrollo de aplicaciones geoespaciales. Las bibliotecas [streamlit-folium](https://folium.streamlit.app/) y [leafmap](https://leafmap.org/) permiten incorporar mapas interactivos en las aplicaciones.

```shell
# Actualización de Conda (opcional, puede tomar varios minutos)
# conda update conda

# Creación del ambiente
conda create -n streamlit

# Activación del ambiente
conda activate streamlit

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de mamba
conda install -c conda-forge mamba

# Instalación de módulos
mamba install -c conda-forge python pandas altair plotly geopandas leafmap streamlit streamlit-folium

# Desactivación del ambiente (al finalizar la sesión de trabajo)
conda deactivate
```

## Aplicaciones de ejemplo

Se proporciona el código fuente de dos aplicaciones Streamlit de ejemplo en repositorios de la organización del curso en GitHub.

La primera despliega un [tablero de control](https://es.wikipedia.org/wiki/Cuadro_de_mando) (también llamado cuadro de mando o *dashboard*) con datos de la pandemia de COVID-19 compartidos por [Our World in Data](https://ourworldindata.org/). Integra tablas y gráficos de Plotly:

[https://github.com/tpb708-programacionsig/2026-i-app-covid](https://github.com/tpb708-programacionsig/2026-i-app-covid)

La segunda muestra registros de presencia de felinos (*Felidae*) de Costa Rica, a partir de datos de [GBIF](https://www.gbif.org/), e integra los tres tipos de salida desarrollados en las tareas del curso: una tabla (pandas), un gráfico de cantidad de registros por especie (Plotly) y un mapa de registros de presencia (folium):

[https://github.com/tpb708-programacionsig/2026-i-app-geoespacial](https://github.com/tpb708-programacionsig/2026-i-app-geoespacial)

Esta segunda aplicación sirve como base para el desarrollo de aplicaciones interactivas que combinan tablas, gráficos y mapas.

### Ejecución en la computadora local

Para ejecutar una aplicación en su computadora, clone o descargue el repositorio con el código fuente y, desde la línea de comandos del sistema operativo, ingrese al directorio y ejecute:

```bash
# Ejecución de la aplicación Streamlit
streamlit run app.py
```

Este comando inicializa un servidor web de desarrollo y abre la aplicación Streamlit.

### Publicación en Streamlit Cloud

Para publicar una aplicación en Streamlit Cloud, primero debe crear un archivo llamado `requirements.txt` con la lista de las bibliotecas que usa la aplicación. Por ejemplo:

```
streamlit
pandas
plotly
geopandas
folium
streamlit-folium
branca
```

Luego, debe incluir la aplicación, y los archivos asociados (ej. datos locales), en un repositorio en GitHub.

Por último, debe ingresar a [Streamlit Cloud](https://streamlit.io/cloud) y crear una cuenta gratuita (puede usar su cuenta de GitHub). Ahí debe seleccionar el repositorio de GitHub en el que se encuentra la aplicación y publicarla.

## Otros recursos

- [Sitio principal](https://streamlit.io/)
- [Guía de inicio](https://docs.streamlit.io/get-started)
- [Documentación](https://docs.streamlit.io/)
- [Streamlit Cloud](https://streamlit.io/cloud)
- [Referencia del API](https://docs.streamlit.io/develop/api-reference)
- [Galería de aplicaciones](https://streamlit.io/gallery)
