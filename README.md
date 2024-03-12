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

La plataforma de datos abiertos de la ciudad de Buenos Aires en el apartado de [Siniestros Viales](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales) tiene bases de datos que contienen registros de indicentes viales comprendidos entre los años 2016 y 2021. A Continuación se hace una descripción de los mismos:

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

    En primera medida el analista hace una revisión de los productos a entregar con el fin de establecer un cronograma ajustado a las necesidades de entrega.
    
    | Día       | Tareas a realizar                                               | Actividad              |
    |:----------|:----------------------------------------------------------------|:----------------------:|
    | Miercoles | Revisión de los requerimientos, las solicitudes y los datasets  | Organización           | 
    | Jueves    | Transformación de los datos y modelo relacional                 | ETL                    | 
    | Viernes   | Análisis Exploratorio de los datos                              | EDA                    | 
    | Sábado    | Definición de paleta de colores y estructura de la presentación | Storytelling           | 
    | Domingo   | Creación de gráficos base y elección de gráficos                | Visualización de datos |
    | Lunes     | Creación de KPIs, revisión general del proyecto                 | KPIs                   | 
    | Martes    | Detalle de los gráficos y creación de iconos                    | Visualización de datos | 


- ### Extracción, Transformación y Carga (ETL)

    Con el fin de realizar un trabajo organizado y debidamente documentado, el proceso de transformación de los datos se documentó en el cuadernillo [ETL](01_ETL.ipynb). Este cuadernillo tiene 5 outputs guardados en la carpeta dataout:

    - **actores.csv**: Este [dataset](dataout/actores.csv) tiene la lista de los actores identificados durante el proceso de ETL, los actores viales se refieren a las personas que interactúan en la vía y no a los modos o vehiculos que ellos usan.

    - **modos.csv**: Este [dataset](dataout/modos.csv) tiene la lista de los modos o medios de transporte que usan los actores para movilizarse.

    - **siniestrosCABA.csv**: Este [dataset](dataout/siniestrosCABA.csv) tiene la lista de siniestros compilada de los datasets originales y que incluye una nueva columna determinada como Gravedad, que establece la gravedad del siniestro dependiendo de la gravedad de sus victimas.

    - **siniestrosLocs.csv**: Este [dataset](dataout/siniestrosLocs.csv) es una extensión del dataset siniestrosCABA y que permite detallar la ubicación de los siniestros por geolocalización y otros datos como la comuna.

    - **victimasCABA.csv**: Este [dataset](dataout/victimasCABA.csv) tiene la lista de victimas compilada de los datasets originales y que incluye una columna sobre la Gravedad de la Victima, así como una aclaración sobre el tipo de actor.

- ### Análisis Exploratorio de Datos (EDA)

    Es importante mencionar que en los archivos ETL se realizó un EDA inicial, ya que el analistas del proyecto considera estos dos procesos como sincrónicos. En el EDA inicial se exploran las variables y sus tipos, las relaciones de las variables y un conteo de valores nulos y duplicados.
    
    Sin embargo, en este [cuadernillo](02_EDA.ipynb) se realiza un EDA usando librerías como Matplotlib y Seaborn para visualizar los datos gráficamente y entender mejor los patrones.

    De este proceso no surgen datasets, solo el cuadernillo con los hallazgos de este proceso.

- ### Creación del dashboard

    Con el fin de crear una visualización profesional, se establece una estructura de la presentación y se definen algunos parametros clave para seguir durante el diseño de la presentación. Por un lado se establece la gama de colores a utilizar y un diseño que resalte a la vista lo que se desea mostrar usando herramientas como el patrón Z. Se establecen las fuentes de cada uno de los textos y su tamaño.

    - **Paleta de colores**: Para esta presentación se usaron tonos azules y rojos, el azul con dar a la presentación seriedad y profesionalismo. Y los tonos rojos para destacar aspectos importantes y descubrimientos que se quiere mostrar al espectador.

    ![r1](vis/1.jpg)

    - **userData(idUsuario)**: Esta función recibe como argumento el id del usuario y devuelve un diccionario con la cantidad de dinero gastado por ese usuario en la adquisición de aplicaciones, el porcentaje de recomendación de las apps que compró y la cantidad de apps que adquirió.

    - **userForGenre(genero)**: Esta función recibe como argumento el genero o clasificación de la aplicación y devuelve un diccionario con el usuario que tiene mayor número de horas de interacción con aplicaciones de esa clasificación, distribuidas a través de los años.

    - **bestDeveloper(año)**: Esta función recibe como argumento un año y devuelve un diccionario con el top 3 de desarrolladores que más recomendaciones positivas recibieron.

    - **developerReviewsAnalysis(desarrollador)**: Esta función recibe como argumento el nombre de un desarrollador y devuelve un diccionario la cantidad de recomendaciones negativas y la cantidad de recomendaciones positivas.

    Los datasets resultantes se guardaron en la carpeta datafunc en formato parquet, un formato de archivos que utiliza menos espacio en memoria y es fácil de extraer desde **Pandas**.



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