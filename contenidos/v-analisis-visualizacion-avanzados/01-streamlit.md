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

Estos comandos deben ejecutarse en una terminal con conda habilitado. En **Windows**, abra **Anaconda Prompt** desde el menú Inicio (no use CMD ni PowerShell, ya que no tienen conda habilitado por defecto); en **macOS** o **Linux**, use la terminal del sistema. Es necesario tener [conda](https://docs.conda.io/) instalado: al inicio del curso se instaló mediante [Miniconda](https://docs.anaconda.com/miniconda/), que puede descargarse desde ese sitio en caso de ser necesario.

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

## Una primera aplicación: «Hola mundo»

Para verificar que la instalación funciona y conocer el flujo básico de trabajo, en esta sección se desarrolla y ejecuta, paso a paso, una aplicación Streamlit muy sencilla.

Se asume que está instalado el editor [Visual Studio Code (VS Code)](https://code.visualstudio.com/), que puede descargarse desde su sitio web en caso de ser necesario. Se recomienda tener instalada también la [extensión de Python para VS Code](https://marketplace.visualstudio.com/items?itemName=ms-python.python). Además, debe haberse creado el ambiente `streamlit` con la biblioteca Streamlit, tal como se indicó en la sección anterior.

1. **Crear un directorio para la aplicación.** En la ubicación de su preferencia (por ejemplo, en el directorio del usuario), cree un directorio para el proyecto, llamado `hola-streamlit`. Puede crearlo con el explorador de archivos del sistema operativo o, desde una terminal, con el comando:

    ```shell
    mkdir hola-streamlit
    ```

2. **Abrir el directorio en VS Code.** En VS Code, seleccione **File > Open Folder** (Archivo > Abrir carpeta) y elija el directorio `hola-streamlit` recién creado.

3. **Crear el archivo del programa.** Dentro del directorio, cree un archivo llamado `app.py`. En VS Code puede hacerlo con el botón **New File** (Nuevo archivo) del panel del explorador, o con el menú **File > New File**. La extensión `.py` indica que es un archivo de código fuente en Python.

4. **Escribir el código de la aplicación.** Copie el siguiente código en el archivo `app.py`:

    ```python
    import streamlit as st

    st.title("Hola mundo")
    st.write("Esta es mi primera aplicación desarrollada con Streamlit.")

    nombre = st.text_input("Escriba su nombre:")

    if nombre:
        st.write(f"¡Hola, {nombre}!")
    ```

    La función [`st.title()`](https://docs.streamlit.io/develop/api-reference/text/st.title) muestra un título, [`st.write()`](https://docs.streamlit.io/develop/api-reference/write-magic/st.write) muestra texto y [`st.text_input()`](https://docs.streamlit.io/develop/api-reference/widgets/st.text_input) crea una casilla de texto que el usuario puede completar de forma interactiva.

5. **Guardar el archivo.** Guarde los cambios con `Ctrl + S` (en macOS, `Cmd + S`).

6. **Abrir una terminal con conda habilitado.** Abra la terminal integrada de VS Code con **Terminal > New Terminal** (Terminal > Nueva terminal). En **Windows**, asegúrese de que la terminal tenga conda habilitado; si no, use **Anaconda Prompt** y, desde ahí, ingrese al directorio del proyecto con `cd hola-streamlit`.

7. **Activar el ambiente.** En la terminal, active el ambiente creado en la sección anterior:

    ```shell
    conda activate streamlit
    ```

8. **Ejecutar la aplicación.** Desde el directorio del proyecto, ejecute:

    ```shell
    streamlit run app.py
    ```

    Este comando inicia un servidor web de desarrollo y abre la aplicación en el navegador, normalmente en la dirección [http://localhost:8501](http://localhost:8501). Escriba su nombre en la casilla de texto para ver cómo la aplicación responde de forma interactiva.

9. **Detener la aplicación.** Para detener el servidor, regrese a la terminal y presione `Ctrl + C`.

Mientras la aplicación está en ejecución, cada vez que guarde cambios en `app.py`, Streamlit detecta la modificación y ofrece volver a ejecutar la aplicación para reflejar los cambios.

## Publicación en Streamlit Cloud

[Streamlit Cloud](https://streamlit.io/cloud) permite publicar una aplicación en internet de forma gratuita, a partir del código alojado en un repositorio de [GitHub](https://github.com/). A continuación se explica, paso a paso, cómo publicar la aplicación «Hola mundo» creada en la sección anterior.

1. **Crear el archivo `requirements.txt`.** En el directorio de la aplicación (`hola-streamlit`), cree un archivo llamado `requirements.txt` con la lista de las bibliotecas que utiliza la aplicación. Streamlit Cloud lo usa para instalar las dependencias necesarias. Para la aplicación «Hola mundo» basta con una línea:

    ```
    streamlit
    ```

    En aplicaciones más complejas se agregan las demás bibliotecas, una por línea (por ejemplo, `pandas`, `plotly`, `geopandas`, `folium`, `streamlit-folium`).

2. **Subir la aplicación a un repositorio de GitHub.** Streamlit Cloud publica la aplicación a partir del código alojado en GitHub. Si no tiene una cuenta, créela de forma gratuita en [github.com](https://github.com/). Luego:

    - Cree un repositorio nuevo (por ejemplo, `hola-streamlit`).
    - Agregue al repositorio los archivos `app.py` y `requirements.txt`. Puede hacerlo desde la interfaz web de GitHub con la opción **Add file > Upload files**, o mediante git si está familiarizado con su uso.

3. **Configurar Streamlit Cloud por primera vez.** Ingrese a [Streamlit Cloud](https://streamlit.io/cloud) y seleccione **Continue with GitHub** para iniciar sesión con su cuenta de GitHub. La primera vez, GitHub solicitará autorizar a Streamlit Community Cloud para acceder a sus repositorios; acepte para continuar.

4. **Publicar la aplicación.** En el panel de Streamlit Cloud, haga clic en **Create app** (o **New app**) y seleccione la opción para publicar una aplicación a partir de un repositorio existente. Indique:

    - el **repositorio** de GitHub (por ejemplo, `su-usuario/hola-streamlit`),
    - la **rama** (normalmente `main`),
    - el **archivo principal** (`app.py`).

    Haga clic en **Deploy**. Streamlit Cloud instalará las bibliotecas indicadas en `requirements.txt` y ejecutará la aplicación. Después de unos instantes, la aplicación quedará disponible en una dirección pública con el formato `https://<nombre>.streamlit.app`, que puede compartir con cualquier persona.

5. **Actualizar la aplicación.** Cada vez que suba cambios al repositorio de GitHub, Streamlit Cloud vuelve a publicar la aplicación automáticamente con la nueva versión.

## Aplicaciones de ejemplo

Se proporciona el código fuente de dos aplicaciones Streamlit de ejemplo en repositorios de la organización del curso en GitHub.

La primera despliega un [tablero de control](https://es.wikipedia.org/wiki/Cuadro_de_mando) (también llamado cuadro de mando o *dashboard*) con datos de la pandemia de COVID-19 compartidos por [Our World in Data](https://ourworldindata.org/). Integra tablas y gráficos de Plotly:

[https://github.com/tpb708-programacionsig/2026-i-app-covid](https://github.com/tpb708-programacionsig/2026-i-app-covid)

La segunda muestra registros de presencia de felinos (*Felidae*) de Costa Rica, a partir de datos de [GBIF](https://www.gbif.org/), e integra los tres tipos de salida desarrollados en las tareas del curso: una tabla (pandas), un gráfico de cantidad de registros por especie (Plotly) y un mapa de registros de presencia (folium):

[https://github.com/tpb708-programacionsig/2026-i-app-geoespacial](https://github.com/tpb708-programacionsig/2026-i-app-geoespacial)

Esta segunda aplicación sirve como base para el desarrollo de aplicaciones interactivas que combinan tablas, gráficos y mapas. Cada repositorio puede ejecutarse en la computadora local siguiendo los pasos de la sección «Una primera aplicación: "Hola mundo"», y publicarse en Streamlit Cloud como se explicó en la sección anterior.

## Otros recursos

- [Sitio principal](https://streamlit.io/)
- [Guía de inicio](https://docs.streamlit.io/get-started)
- [Documentación](https://docs.streamlit.io/)
- [Streamlit Cloud](https://streamlit.io/cloud)
- [Referencia del API](https://docs.streamlit.io/develop/api-reference)
- [Galería de aplicaciones](https://streamlit.io/gallery)
