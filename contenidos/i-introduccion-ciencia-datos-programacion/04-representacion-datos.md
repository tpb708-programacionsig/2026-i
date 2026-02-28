# Representación de datos: observaciones, variables y sus tipos

## Trabajo previo

### Lecturas

Çetinkaya-Rundel, Mine, & Hardin, Johanna (2021). *Chapter 1: Hello data* en *Introduction to Modern Statistics* (1st ed.). OpenIntro, Inc. https://openintro-ims.netlify.app/data-hello
\
\
Wickham, Hadley; Çetinkaya-Rundel, Mirne; & Grolemund, Garret (2023). *Introduction* en *R for Data Science: Import, Tidy, Transform, Visualize, and Model Data* (2nd ed.). O'Reilly Media. https://r4ds.hadley.nz/intro

## Introducción

La presentación y descripción efectivas de los datos constituyen el primer paso en un análisis (Çetinkaya-Rundel & Hardin, 2021). Una de las formas más comunes de representar datos es mediante tablas en las cuales cada fila es una **observación** y cada columna es una **variable**. Una observación corresponde a un elemento de datos que ha sido estudiado y cada variable a una característica de ese elemento. Por ejemplo, la tabla 1 muestra una tabla con observaciones correspondientes a registros de presencia de especies.

<table border="0" cellspacing="10" class="dataframe">
  <style>
    .dataframe {
        border-spacing: 10px 10px;
    }
    .dataframe td, .dataframe th {
        padding-left: 5px;
        padding-right: 5px;
        padding-top: 2px;
        padding-bottom: 2px;
    }
  </style>
  <caption><strong>Tabla 1. Registros de presencia de especies.</strong></caption>
  <thead>
    <tr>
      <th>Nombre científico</th>
      <th>Longitud</th>
      <th>Latitud</th>
      <th>Fecha</th>
      <th>Sexo</th>
      <th>Edad (años)</th>
      <th>Peso (g)</th>
      <th>Longitud (cm)</th>
      <th>Estado de conservación</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><i>Panthera onca</i></td>
      <td>-84.5678</td>
      <td>10.1234</td>
      <td>2024-05-12</td>
      <td>Macho</td>
      <td>5</td>
      <td>56700</td>
      <td>170</td>
      <td>Casi amenazada (NT)</td>
    </tr>
    <tr>
      <td><i>Ara macao</i></td>
      <td>-83.2345</td>
      <td>9.8765</td>
      <td>2024-06-18</td>
      <td>Hembra</td>
      <td>3</td>
      <td>1000</td>
      <td>85</td>
      <td>Preocupación menor (LC)</td>
    </tr>
    <tr>
      <td><i>Dendrobates auratus</i></td>
      <td>-82.1234</td>
      <td>8.5432</td>
      <td>2024-07-22</td>
      <td>Macho</td>
      <td>1</td>
      <td>2</td>
      <td>4</td>
      <td>Preocupación menor (LC)</td>
    </tr>
    <tr>
      <td><i>Cebus imitator</i></td>
      <td>-85.4321</td>
      <td>10.6543</td>
      <td>2024-08-30</td>
      <td>Hembra</td>
      <td>8</td>
      <td>3000</td>
      <td>45</td>
      <td>Vulnerable (VU)</td>
    </tr>
    <tr>
      <td><i>Iguana iguana</i></td>
      <td>-84.7890</td>
      <td>9.3456</td>
      <td>2024-09-15</td>
      <td>Macho</td>
      <td>4</td>
      <td>4000</td>
      <td>150</td>
      <td>Preocupación menor (LC)</td>
    </tr>
    <tr>
      <td><i>Basiliscus basiliscus</i></td>
      <td>-83.4567</td>
      <td>8.9876</td>
      <td>2024-10-05</td>
      <td>Hembra</td>
      <td>2</td>
      <td>200</td>
      <td>80</td>
      <td>Preocupación menor (LC)</td>
    </tr>
    <tr>
      <td><i>Ateles geoffroyi</i></td>
      <td>-84.1234</td>
      <td>10.2345</td>
      <td>2024-11-12</td>
      <td>Macho</td>
      <td>6</td>
      <td>7000</td>
      <td>50</td>
      <td>En peligro (EN)</td>
    </tr>
    <tr>
      <td><i>Boa imperator</i></td>
      <td>-82.3456</td>
      <td>9.8765</td>
      <td>2024-12-01</td>
      <td>Hembra</td>
      <td>10</td>
      <td>12000</td>
      <td>300</td>
      <td>Preocupación menor (LC)</td>
    </tr>
    <tr>
      <td><i>Sotalia fluviatilis</i></td>
      <td>-83.9876</td>
      <td>8.1234</td>
      <td>2024-12-20</td>
      <td>Macho</td>
      <td>12</td>
      <td>35000</td>
      <td>210</td>
      <td>En peligro (EN)</td>
    </tr>
    <tr>
      <td><i>Chelonia mydas</i></td>
      <td>-84.1234</td>
      <td>9.6543</td>
      <td>2025-01-05</td>
      <td>Hembra</td>
      <td>50</td>
      <td>150000</td>
      <td>120</td>
      <td>En peligro (EN)</td>
    </tr>
  </tbody>
</table>

## Tipos de variables

Las variables de los datos de la tabla 1 son de varios tipos, cuya jerarquía se muestra en la figura 1.

<figure style="text-align: center;">
  <img
    src="https://raw.githubusercontent.com/datos-geoespaciales-biodiversidad/python/refs/heads/main/img/tipos-variables-estadisticas.png"
    alt="Tipos de variables"
  >
  <figcaption><strong>Figura 1</strong>. Tipos de variables. Fuente: (Çetinkaya-Rundel & Hardin, 2021).</figcaption>
</figure>

#### Numéricas

Corresponden a números a los cuales se les pueden aplicar operaciones como suma, resta, multiplicación, división y otras similares. Las variables numéricas puden ser discretas o continuas.

##### Discretas

Toman valores específicos que se pueden contar. La variable `edad`, en este caso, es discreta.

##### Continuas

Pueden tomar cualquier valor dentro de un intervalo o rango continuo. Estas variables se caracterizan por su capacidad para representar medidas precisas y pueden asumir un número infinito de valores, incluso dentro de un rango limitado (ej. entre 0 y 1). Las variables `peso` y `longitud` son continuas.

#### Categóricas

Las variables categóricas (también llamadas cualitativas), son aquellas que describen una característica o cualidad de una observación y pueden utilizarse para clasificar las observaciones en grupos o categorías. A diferencia de las variables numéricas, que expresan cantidades, las variables categóricas expresan atributos no numéricos. Las variables categóricas pueden ser nominales u ordinales.

##### Nominales

No existe un orden inherente o jerarquía entre las categorías. Las variables `nombre científico` y `sexo` son nominales.

##### Ordinales

Hay un orden o jerarquía clara entre las categorías, como en el caso de la variable `estado de conservación`.

## Referencias bibliográficas

Çetinkaya-Rundel, Mine, & Hardin, Johanna (2021). *Chapter 1: Hello data* en *Introduction to Modern Statistics* (1st ed.). OpenIntro, Inc. https://openintro-ims.netlify.app/data-hello
