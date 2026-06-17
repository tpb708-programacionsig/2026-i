# Proyecto final

## Fecha y hora límite de entrega

Sábado 20 de junio de 2026, 11:59 p.m.

## Objetivos

Cada estudiante debe mostrar que es capaz de:

1. Integrar, en una sola aplicación web interactiva, las destrezas de procesamiento de datos con **pandas**, de visualización con **matplotlib** o **plotly** y de elaboración de mapas con **folium** o **leafmap**, desarrolladas a lo largo del curso.
2. Desarrollar una aplicación web de datos con la biblioteca **Streamlit**.
3. Publicar la aplicación en Internet mediante **GitHub** y **Streamlit Cloud**.

## Entregables

La entrega debe realizarse a través de la plataforma Mediación Virtual de la UCR e incluye **dos direcciones (URL)**:

- La del **repositorio público de GitHub** con el código de la aplicación (`app.py`), el archivo `requirements.txt` y los datos necesarios (o las URL desde las que se cargan).
- La de la **aplicación publicada en Streamlit Cloud** (con el formato `https://<nombre>.streamlit.app`).

La aplicación debe estar **en funcionamiento** en Streamlit Cloud al momento de la entrega.

## Presentación

El día de la entrega se realizará una **sesión virtual** en la que cada estudiante presentará su aplicación al resto del grupo.

Lineamientos de la presentación:

- Cada exposición tendrá una duración **máxima de 10 minutos**, más **2 minutos** para preguntas y comentarios.
- Como son 13 estudiantes, es importante **respetar el tiempo asignado** para que todas las presentaciones quepan en la sesión.
- La presentación debe hacerse mostrando la **aplicación en funcionamiento** desde su URL pública en Streamlit Cloud (no se requiere una presentación de diapositivas).
- Durante la exposición se sugiere:
  - Describir brevemente el **tema, los datos y su fuente**.
  - Mostrar y explicar la **tabla**, el **gráfico** y el **mapa** de la aplicación.
  - Demostrar el funcionamiento del **filtro interactivo** y cómo actualiza el contenido.
- Se valorarán la **claridad** de la exposición, el **dominio** del contenido y el **manejo del tiempo**.

## Consideraciones adicionales

**Este proyecto es estrictamente individual.**

El proyecto final corresponde al **25 % de la calificación final del curso**.

## Desarrollo

El proyecto final consiste en **convertir la Tarea 3 en una aplicación web interactiva** desarrollada con Streamlit. A partir del mismo conjunto de datos y de los productos que elaboró en esa tarea, la aplicación debe **reutilizar o adaptar**, como mínimo, los siguientes tres elementos:

- **Una tabla** generada con pandas (por ejemplo, la tabla de filtrado, agrupamiento o estadísticas descriptivas de la Tarea 3), mostrada con `st.dataframe()`.
- **Un gráfico estadístico** elaborado con matplotlib o con plotly (uno de los gráficos de la Tarea 3), mostrado con `st.plotly_chart()` (plotly) o `st.pyplot()` (matplotlib).
- **Un mapa interactivo** elaborado con folium o con leafmap (uno de los mapas de la Tarea 3), integrado en la aplicación con la biblioteca `streamlit-folium`.

Además, la aplicación debe implementar **al menos un filtro interactivo** —por ejemplo, con `st.selectbox()`, `st.multiselect()`, `st.slider()` o `st.radio()`— que **modifique el contenido mostrado**. Se recomienda que el filtro afecte a más de uno de los elementos anteriores; por ejemplo, que al seleccionar una categoría se actualicen a la vez la tabla, el gráfico y el mapa.

La aplicación también debe incluir:

- Un **título** y un **texto introductorio** que describan el tema, los datos y su fuente.
- Un **texto breve** que acompañe cada elemento (tabla, gráfico y mapa) e indique qué muestra.

El contenido de la aplicación debe ser **coherente** y estar **bien presentado**.

## Calificación

Entre paréntesis, se muestra el porcentaje correspondiente a cada aspecto que se calificará:

- (10 %) Coherencia, presentación y textos de la aplicación.
- (15 %) Tabla (pandas) integrada correctamente.
- (15 %) Gráfico estadístico integrado correctamente.
- (25 %) Mapa interactivo integrado correctamente.
- (15 %) Filtro interactivo funcional que actualiza el contenido mostrado.
- (10 %) Presentación de la aplicación en la sesión virtual.
- (10 %) Publicación correcta: repositorio público en GitHub y aplicación en funcionamiento en Streamlit Cloud.

## Cómo desarrollar la aplicación

Para el desarrollo de la aplicación puede apoyarse en:

- El capítulo [Streamlit](../v-analisis-visualizacion-avanzados/01-streamlit.md) del curso, en particular la sección **«De la Tarea 3 a una aplicación»**, que explica cómo mostrar una tabla, un gráfico, un mapa y un filtro en Streamlit.
- La aplicación de ejemplo [tpb708-programacionsig/2026-i-app-geoespacial](https://github.com/tpb708-programacionsig/2026-i-app-geoespacial), que integra una tabla (pandas), un gráfico (plotly), un mapa (folium) y un filtro, y que puede utilizarse como **plantilla** para el proyecto.

Se sugiere el siguiente procedimiento:

1. Cree un directorio para la aplicación con un archivo `app.py` y ábralo en VS Code (consulte la sección «Una primera aplicación: "Hola mundo"»).
2. Cargue los datos de su Tarea 3 con pandas (y, si elabora un mapa de coropletas, los datos geoespaciales con geopandas). Use el decorador `@st.cache_data` para no recargarlos en cada interacción.
3. Agregue, uno a uno, la tabla, el gráfico y el mapa, reutilizando el código de su Tarea 3 y adaptándolo a las funciones de Streamlit.
4. Agregue el filtro y haga que la tabla, el gráfico y el mapa se construyan a partir de los datos filtrados.
5. Ejecute la aplicación localmente con `streamlit run app.py` y verifique su funcionamiento.
6. Cree el archivo `requirements.txt`, suba la aplicación a un repositorio **público** de GitHub y publíquela en Streamlit Cloud (consulte la sección «Publicación en Streamlit Cloud»).
