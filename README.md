![README](src/port.jpg)

# Proyecto Individual 2 D.A. Siniestros Viales Ciudad Autónoma de Buenos Aires

En el presente repositorio se desarrolla un **análisis** de la problematica de siniestralidad en la capital de Argentina desde el rol de **Analista de Datos** para la Subsecretaría de Planificación de La Movilidad.

![Int](src/R1.jpg)

## Introducción

La Subsecretaría de Planificación de la Movilidad ha solicitado al analista de datos extraer los datos de siniestros viales de Lesiones y Homicidios ocurridos en la ciudad que se encuentran disponibles en la página oficial de datos del gobierno de Buenos Aires, y a partir de esta extracción, transformar los datos adecuadamente para encontrar información valiosa sobre los hechos ocurridos y sus victimas. Luego de esta transformación, el analista realiza una exploración inicial de los datos para encontrar patrones en los datos y tomar decisiones de como representarlos. Finalmente, el analista diseña un dashboard que le permita a la ciudadanía de Buenos Aires y al Secretario de Movilidad extraer información y tomar decisiones al respecto sobre lo que debe hacer para mejorar el problema.

### - Objetivos del proyecto

- Extraer, transformar y cargar los datos en un dataset usando la librería de **Pandas**.
- Realizar un análisis exploratorio de los datos, para observar patrones y tendencias estadísticas usando la librería de **Seaborn y matplotlib**.
- Crear un dashboard en **PowerBi** con los principales insights de los datos recopilados.
- Crear **Indicadores Clave de Rendimiento (KPI)** que permitan evaluar el comportamiento y avance de las metas planteadas por la Subsecretaría de Planificación de la Movilidad para reducir los niveles de siniestralidad en los últimos periodos.


### Funciones desde el rol

- Extraer los datos en un formato que facilite la consulta (**csv**)
- Transformar los datos (primarios), identificando valores nulos, vacíos y errores que afecten el análisis de los mismos y tomar medidas con argumentos bien justificados.
- Cargar los datos limpios.
- Realizar un análisis exploratorio de los datos para identificar patrones, anomalías, outliers, medidas relevantes y comparar comportamientos de los datos.
- Crear un tablero de presentación dinámico, con tonos de color apropiados y excelentes visualizaciones que permitan extraer información rápidamente.


![r2](src/r2.jpg)

## Descripción de la fuente de los datos

La plataforma de datos abiertos de la ciudad de Buenos Aires en el apartado de ![Siniestros Viales](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales) tiene bases de datos que contienen registros de indicentes viales comprendidos entre los años 2016 y 2021. A Continuación se hace una descripción de los mismos:

- ### Lesiones.xlsx

    Este [dataset](datasets/lesionesCABA.xlsx) contiene toda la información asociada a los hechos de siniestros donde hubo victimas con **lesiones personales**, contiene dos tablas (Hechos) y (Victimas).

    - Hechos: Contiene los registros de cada uno de los siniestros presentados entre 2019 y 2021 en el perimetro de la ciudad con localización, fecha y actores involucrados.

    - Victimas: Contiene los registros de cada una de las victimas registradas en la base de datos que fueron victimas de los hechos con información importante como su genero, edad y actor.

- ### Homicidios.xlsx

    Este [dataset](datasets/homicidiosCABA.xlsx) contiene toda la información asociada a los hechos de siniestros donde hubo victimas **fallecidas**, contiene dos tablas (Hechos) y (Victimas).

    - Hechos: Contiene los registros de cada uno de los siniestros presentados entre 2016 y 2021 en el perimetro de la ciudad con localización, fecha y actores involucrados.

    - Victimas: Contiene los registros de cada una de las victimas registradas en la base de datos que fallecieron con información importante como su genero, edad y actor.


![r3](src/r3.jpg)

## El proceso

A continuación se hace una descripción y resumen de la metodología de trabajo para llegar al producto solicitado.

- ### Requerimientos y cronograma

    En primera medida el equipo de trabajo hace una revisión de los productos a entregar con el fin de establecer un cronograma ajustado a las necesidades de entrega.
    
    | Variable            | Definición                                               |Tipo de Dato| Tipo de Variable       |
    |:--------------------|:---------------------------------------------------------|:----------:|:-----------------------|
    | IdSiniestro         | Identificador único del siniestro                        | Integer    | Categórica(nominal) PK |
    | Gravedad            | Si el siniestro tuvo muertos, heridos o solo daños       | Integer    | Categórica(nominal)    |
    | NumeroVictimas      | Cantidad total de personas afectadas por el siniestro    | Integer    | Numérica(discréta)     |
    | Año                 | Año en el que sucedió el siniestro                       | String     | Categórica(ordinal)    |
    | Mes                 | Mes en el que sucedió el siniestro                       | String     | Categórica(ordinal)    |
    | Dia                 | Día en el que sucedió el siniestro                       | String     | Catégorica(ordinal)    |
    | Hora                | Hora del día en que sucedió el siniestro                 | String     | Categórica(ordinal)    |
    | IdTransporteVictima | Id del vehículo que fue víctima del accidente            | Integer    | Categórica(Nominal) FK |
    | IdTransporteAcusado | Id del vehículo acusado como causante del accidente      | Integer    | Categórica(Nominal) FK |
    | Fecha               | Fecha completa                                           | DateTime   | Categórica(ordinal)    |
    | DiaSemana           | Dia de la semana en que sucedió el siniestro             | String     | Categórica(nominal)    |

    - **Día 1** : Revisión de los datasets entregados,  opciones de descompresión, limitaciones de procesamiento y estructura de los datos.

    - **Día 2 y 3** : Extracción, Carga y Transformación de los datos brutos, toma de decisiones con respecto a valores nulos, atípicos y valores vacíos. Análisis Exploratorio de Datos también se realiza en esta etapa ya que son procesos sincrónicos.
    - **Día 4** : Se revisan las solicitudes de consulta para la API y se construyen las funciones localmente para evaluar su funcionamiento.
    - **Día 5** : Se realiza el despliegue de la API localmente, para revisar estructura y outputs.
    - **Día 6 y 7**: Fin de semana.
    - **Día 8**: Evaluación de los deploys en nube y carga de la API en línea.
    - **Día 9**: Ajustes, documentación y carga de los archivos a gerencia.
    - **Día 10**: Presentación del producto.

- ### Extracción, Transformación y Carga (ETL)

    Con el fin de realizar un trabajo organizado y debidamente documentado, el ETL se dividió en los 3 conjuntos de datos entregados.

    - **01_ETL_Steam_games**: Proceso [ETL](01_ETL_Steam_games.ipynb) para el dataset que contiene información asociada a los videojuegos. Este archivo tiene tres outputs: **out_games.parquet**, **out_genres_games.parquet** y **out_metadata_games.parquet**.

    - **02_ETL_Users_items**: Proceso [ETL](02_ETL_Users_items.ipynb) para el dataset que contiene información asociada a las actividades de los usuarios. Este archivo tiene dos outputs: **out_users_items.parquet** y **out_users.parquet**.

    - **03_ETL_Users_reviews**: Proceso [ETL](03_ETL_Users_reviews.ipynb) para el dataset que contiene información asociada las reseñas de las aplicaciones. Este archivo tiene dos outputs: **out_users_reviews.parquet** y **out_feelings.parquet**, este último es el resultado de un análisis de sentimientos 

    Los datasets resultantes se guardaron en la carpeta dataout en formato parquet, un formato de archivos que utiliza menos espacio en memoria y es fácil de extraer desde **Pandas**.

- ### Análisis Exploratorio de Datos (EDA)

    Es importante mencionar que en los archivos ETL se realizó un EDA inicial, ya que el equipo del proyecto considera estos dos procesos como sincrónicos. En el EDA inicial se exploran las variables y sus tipos, las relaciones de las variables y un conteo de valores nulos y duplicados.
    
    Sin embargo, en este [cuadernillo](04_EDA.ipynb) se realiza un EDA usando librerías como Matplotlib y Seaborn para visualizar los datos gráficamente y entender mejor los patrones.

    De este proceso no surgen datasets, solo el cuadernillo con los hallazgos de este proceso.

- ### Creación de Funciones

    Con el fin de documentar el proceso de creación de cada una de las funciones que ejecutarán las consultas de la API, se crea este [documento](05_Funciones.ipynb).

    En este cuadernillo se importan los datasets de la carpeta dataout para ser procesados y mejorar su rendimiento en función de las necesidades de las consultas.

    Se crearon cada una de las funciones solicitadas por la gerencia, estableciendo los datasets que se usan y creando un dataset único para las necesidades de la funciones  de consulta. 

    - **developer(developerName)**: Esta función recibe como argumento el nombre de un desarrollador y devuelve un diccionario con la cantidad de Apps lanzadas por año y el porcentaje de contenido gratis sobre el total de aplicaciones lanzadas por año.

    - **userData(idUsuario)**: Esta función recibe como argumento el id del usuario y devuelve un diccionario con la cantidad de dinero gastado por ese usuario en la adquisición de aplicaciones, el porcentaje de recomendación de las apps que compró y la cantidad de apps que adquirió.

    - **userForGenre(genero)**: Esta función recibe como argumento el genero o clasificación de la aplicación y devuelve un diccionario con el usuario que tiene mayor número de horas de interacción con aplicaciones de esa clasificación, distribuidas a través de los años.

    - **bestDeveloper(año)**: Esta función recibe como argumento un año y devuelve un diccionario con el top 3 de desarrolladores que más recomendaciones positivas recibieron.

    - **developerReviewsAnalysis(desarrollador)**: Esta función recibe como argumento el nombre de un desarrollador y devuelve un diccionario la cantidad de recomendaciones negativas y la cantidad de recomendaciones positivas.

    Los datasets resultantes se guardaron en la carpeta datafunc en formato parquet, un formato de archivos que utiliza menos espacio en memoria y es fácil de extraer desde **Pandas**.

- ### Modelo Machine Learning (Sistema de Recomendación)

    Con el fin de documentar el proceso de creación de modelo de aprendizaje basado en recomendaciones se crea este [cuadernillo](06_Modelo_ML.ipynb) que contiene los pasos para la creación de este modelo.

    Se crea este modelo en base a la similitud del coseno, se realiza una revisión de referencias a este tema, como el siguiente [video](https://www.youtube.com/watch?v=NlNH4AmIF5o&pp=ygUUc2ltaWxpdHVkIGRlbCBjb3Nlbm8%3D):

    Se utiliza el dataframe Genres y Games que contienen información relevante para este proceso.

    El dataset resultante similitudes es una matriz de similitud que contiene tanto en columnas como en filas cada uno de los IdAPP únicos y establece un porcentaje de similitud con cada una de las apps.

- ### Creación API localmente

    Antes de desplegar la API en la nube, se creó la API en local usando FastAPI, un poderoso framework que permite crear apis de forma rápida.

    Si desea probar la API localmente, se recomienda seguir los siguientes pasos:

    - Descargar el respositorio a sus archivos locales o haciendo uso de git clone.
    - Abrir la carpeta en donde guardó los archivos.
    - Desde allí abrir la ventana de comandos.
    - Ejecutar: python -m venv apiEnv
    - Activar el entorno virtual: ./apiEnv/Scripts/activate
    - Instalar las dependencias del archivo requirements.txt : pip install -r requirements.txt
    - Incializar la API: uvicorn main:app --port 8080 --reload
    - Se creará una dirección tipo ip, que debe copiar y pegar en su navegador.
    - Una vez abierta la pagina escribir /docs en la barra de navegación.
    - En ese momento ya se encuentra en la API.
    - De clic en alguna de las funciones y de clic en la opción try out.
    - Escriba el parametro solicitado y de clic en ejecutar.

- ### API en la nube

    Con el fin de hacer disponible las funcionalidades de la API desde cualquier dispositivo, se creó una API usando un servidor de Railway.

    Esta plataforma permite crear APIs disrectamente desde el repositorio de GitHub y se sincroniza al instante cada vez que existe un nuevo commit en el repositorio.

    Para ingresar a la api desde la web, por favor de clic en el siguiente enlace y no olvide al final de la dirección web escribir: /docs para ingresar a la API.

    [API STEAM HOME](https://mlopssteam.up.railway.app/)
    [API STEAM DIRECTO](https://mlopssteam.up.railway.app/docs)

- ### Video tutorial

    Como una forma de explicar el funcionamiento de la API, se ha creado un [vídeo](https://youtu.be/ZqGyMtjRZC8) en Youtube desde el cual puede ver de manera detallada el funcionamiento de la API.

![r4](src/r4.jpg)

- ## Conclusiones

    Durante el desarrollo de este proyecto es importante destacar la planeación de cada una de las actividades en función de los requerimientos que se hiceron al equipo de trabajo, si bien hubo algunos desajustes en tiempo por errores en código, fue una buena práctica desde el incio establecer unos tiempos limite para llevar a buen termino el proyecto.

    La ejecución de este proyecto se realiza con base a los conocimientos adquiridos durante la carrera de Data Science y la investigación realizada. Se usaron fundamentalmente librerías como **Pandas**, **Sci-kit learn** y **Matplotlib**. Son librerías que permiten manipular eficientemente grandes volumenes de datos.

    Las decisiones tomadas al momento de eliminar y mantener registros se hicieron con base a garantizar información lo más cercana a la realidad, en este caso priorizando más el volumen de datos sobre el procesamiento y almacenamiento, para que el momento en que el usuario requiera hacer una consulta, la información sea lo más real y ajustada a los datos.

    Esto fue costoso en almacenamiento y rendimiento, haciendo múltiples pruebas para que la API en la nube funcionara. No se eliminó información que puede ser considerada irrelevante para este análisis, solo se dividió en otros datasets para que en algún futuro sea usada.

- ## Autor
    [Duván Robayo Roa](https://github.com/duvanroarq/)
    [LinkedIn](https://www.linkedin.com/in/duvanroarq/)