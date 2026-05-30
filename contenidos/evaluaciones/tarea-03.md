# Tarea 3

## Fecha y hora límite de entrega

Martes 9 de junio de 2026, 11:59 p.m.

## Objetivos

Cada estudiante debe mostrar que es capaz de:

1. Procesar y transformar datos tabulares en Python con la biblioteca **pandas**.
2. Generar visualizaciones de datos con la biblioteca **matplotlib** o con la biblioteca **plotly**.
3. Elaborar mapas interactivos con la biblioteca **folium** o con la biblioteca **leafmap**.
4. Presentar los resultados en un cuaderno de notas (*notebook*) de Jupyter.

## Entregables

La entrega debe realizarse a través de la plataforma Mediación Virtual de la UCR, mediante **una** de las siguientes opciones:

- **Opción A**: dirección de un cuaderno de notas publicado en **Google Colab** que cargue los datos desde un repositorio de GitHub.
- **Opción B**: archivo `.ipynb` (desarrollado en VS Code) junto con los archivos de datos correspondientes.

## Consideraciones adicionales

**Esta tarea es estrictamente individual**.

## Desarrollo

Esta tarea es una **extensión de la Tarea 2**. A partir del mismo conjunto de datos utilizado en las tareas anteriores, debe desarrollar un cuaderno de notas (*notebook*) de Jupyter que contenga, como mínimo, los siguientes elementos:

- Una **introducción** breve sobre el tema y los datos (puede reutilizar texto de tareas anteriores), con descripción de las variables principales.
- **Carga de los datos** con pandas (desde un archivo alojado en GitHub o desde un archivo local). Si elabora un mapa de coropletas, cargue también los datos geoespaciales necesarios (por ejemplo, polígonos por región).
- **Al menos una tabla** generada con pandas que muestre filtrado, agrupamiento (`groupby`) o estadísticas descriptivas. *Puede reutilizar la tabla de la Tarea 2.*
- **Al menos dos gráficos** desarrollados en la biblioteca elegida (matplotlib **o** plotly). Cada gráfico debe incluir un **título descriptivo** y **etiquetas en los ejes**; además, los dos gráficos deben ser de **tipo diferente** y mostrar **variables distintas**. *Puede reutilizar los gráficos de la Tarea 2.*
- **Al menos dos mapas** elaborados con la biblioteca **folium** o con la biblioteca **leafmap**. Cada mapa debe:
  - Mostrar datos de su propio conjunto de datos (por ejemplo, puntos a partir de columnas de latitud y longitud, o un mapa de coropletas que una datos tabulares con polígonos).
  - Incluir un **mapa base**, la **simbología y leyenda** apropiadas y, cuando corresponda, **ventanas emergentes (*popup*) o etiquetas (*tooltip*)**.
  - Aportar **valor analítico**: los dos mapas deben ser de **tipo diferente** (por ejemplo, un mapa de puntos y un mapa de coropletas) o mostrar **variables o aspectos distintos** entre sí, de modo que cada uno revele algo de interés sobre los datos.
- **Texto interpretativo** que acompañe cada tabla, cada gráfico y cada mapa, indicando qué muestra y qué se observa en los datos (en el caso de los mapas, qué patrón espacial se observa en relación con las preguntas o problemas planteados desde la Tarea 1).

El contenido del *notebook* debe ser **coherente** y estar **bien presentado**.

## Calificación

Entre paréntesis, se muestra el porcentaje correspondiente a cada aspecto que se calificará:

- (10%) Coherencia y presentación general del *notebook*.
- (20%) Procesamiento con pandas (carga de los datos, transformaciones y tabla).
- (20%) Gráficos en la biblioteca elegida (corrección, variedad, calidad e interpretación).
- (45%) Mapas en la biblioteca elegida (corrección, valor analítico, simbología y leyenda, e interpretación).
- (5%) Entrega correcta (cuaderno de Colab funcional con acceso a los datos, o archivo `.ipynb` ejecutable junto con los datos).

## Cómo elaborar los mapas

Para la elaboración de los mapas puede apoyarse en los capítulos del curso sobre las dos bibliotecas:

- [folium](../iv-procesamiento-datos-geoespaciales/08-folium.ipynb): mapas de puntos a partir de un CSV con columnas de latitud y longitud, marcadores, agrupamiento de marcadores y mapas de coropletas.
- [leafmap](../iv-procesamiento-datos-geoespaciales/09-leafmap.ipynb): métodos como `add_points_from_xy()` (puntos desde un *data frame*), `add_gdf()` (geodataframes) y `add_data()` (mapas de coropletas), entre otros.

Para elaborar un **mapa de puntos** basta con que su conjunto de datos tenga columnas de latitud y longitud. Para elaborar un **mapa de coropletas** necesita, además, polígonos por región (por ejemplo, los polígonos de países de Natural Earth del repositorio del curso) que se unan a los datos tabulares mediante una columna común.

## Cómo subir un CSV a GitHub y cargarlo en un *data frame* de pandas

A continuación se describe el procedimiento para subir un archivo CSV a un repositorio de GitHub usando la **interfaz web** del sitio (sin necesidad de la línea de comandos), y luego cargarlo desde un cuaderno de Jupyter en un *data frame* de pandas.

### 1. Subir el archivo CSV a GitHub

1. Ingrese a [https://github.com](https://github.com) e inicie sesión con su cuenta.
2. Cree un nuevo repositorio (botón **New** en la esquina superior izquierda) o ingrese a un repositorio existente (por ejemplo, el repositorio de la Tarea 1).
   - Asegúrese de que el repositorio sea **público** (`Public`) para que el archivo sea accesible desde un cuaderno de Colab sin autenticación.
   - Marque la opción **Add a README file** si está creando un repositorio nuevo.
3. Una vez dentro del repositorio, haga clic en el botón **Add file** (esquina superior derecha del listado de archivos) y elija **Upload files**.
4. Arrastre el archivo CSV al recuadro de carga, o utilice el enlace **choose your files** para seleccionarlo desde el explorador de archivos de su computadora.
5. En la parte inferior de la página, en la sección **Commit changes**:
   - Escriba un mensaje breve (ej. `Agregar archivo de datos`).
   - Seleccione la opción **Commit directly to the `main` branch**.
   - Haga clic en el botón **Commit changes**.
6. Una vez cargado, haga clic sobre el nombre del archivo CSV en el listado del repositorio para abrirlo.
7. En la vista del archivo, haga clic en el botón **Raw** (esquina superior derecha de la previsualización). Esto abrirá el contenido del archivo en formato sin procesar.
8. Copie la dirección URL que aparece en la barra de direcciones del navegador. Esta URL tendrá la forma:

   ```text
   https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/archivo.csv
   ```

   donde `USUARIO` es su nombre de usuario de GitHub, `REPOSITORIO` es el nombre del repositorio y `archivo.csv` es el nombre del archivo.

### 2. Cargar el CSV en un *data frame* de pandas

En una celda de código del cuaderno de Jupyter (en VS Code o Google Colab), use la función `read_csv()` de pandas con la URL copiada en el paso anterior:

```python
import pandas as pd

url = "https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/archivo.csv"
datos = pd.read_csv(url)

datos.head()
```

El método `head()` muestra las primeras filas del *data frame* y permite verificar que los datos se cargaron correctamente.

### Recomendaciones

- Use nombres de archivo **sin espacios ni caracteres especiales** (por ejemplo, `datos_clima.csv` en lugar de `datos clima.csv`).
- Si el archivo CSV usa un separador distinto a la coma (por ejemplo, punto y coma), especifíquelo con el parámetro `sep`:

  ```python
  datos = pd.read_csv(url, sep=";")
  ```

- Si el archivo contiene caracteres en español (tildes, eñes) y observa que se cargan incorrectamente, especifique la codificación con el parámetro `encoding`:

  ```python
  datos = pd.read_csv(url, encoding="utf-8")
  ```

- Cada vez que actualice el archivo CSV en GitHub, la URL `raw` reflejará automáticamente la última versión, por lo que no es necesario modificar el cuaderno.
