![README](vis/0.jpg)

# Proyecto Individual 2 D.A.
## Siniestros Viales Ciudad Autónoma de Buenos Aires

En el presente repositorio se desarrolla un **análisis** de la problematica de siniestralidad en la capital de Argentina desde el rol de **Analista de Datos** para la Subsecretaría de Planificación de La Movilidad.
---
![Int](vis/11.jpg)

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

---

![r2](vis/12.jpg)

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

---

![r13](vis/13.jpg)

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

    - **Titulos**: Se definió la fuente Arial Rounded, ya que es la fuente oficial del gobierno de la ciudad.

    - **Objetivo de la presentación**: 
    
        Presentar la información encontrada que permita conocer y comprender la realidad de los siniestros viales y sus victimas en la Ciudad de Buenos Aires, entre los años 2019 y 2021.

    - **Definición de la audiencia**: 
    
        La presentación está dirigida a la Secretaría de Planificación de la Movilidad de la ciudad de Buenos Aires y a la ciudadanía en general que requiera información sobre la siniestralidad vial.

    - **Estructura de la historia**

        La presentación se estructura bajo la creación de preguntas orientadoras que se buscan responder en cada una de las páginas del tablero.

        - *Saludo de Bienvenida*:

            - Presentarse adecuadamente.
            - ¿Quién soy?
            - Usar información para impactar a la audiencia y llamar su atención a la presentación ( Cada día mueren 40 personas en Colombia por esto.....)

        - *Introducción al problema*:

            - ¿Qué son los siniestros viales? ¿Qué diferencias existen?
            - ¿Actores? ¿Modos? ¿Niveles de gravedad?
            - Contextualizar rápidamente.
            - Dos datos de impacto.

        - *El problema en el tiempo*:

            - ¿Qué evolución ha tenido el problema de la siniestralidad?
            - ¿Qué hechos se identificaron como inusuales?
            - ¿Qué analisis se puede hacer sobre la frecuencia de los siniestros?

        - *El problema en el espacio*:

            - ¿Qué relación tiene la siniestralidad con el espacio en el que se mueven los ciudadanos?
            - ¿Tiene alguna relación el tamaño de la via?
            - ¿Qué analisis se puede hacer sobre la frecuencia de los siniestros?
            - **KPI:** Reducir en un 15% la cantidad de siniestros en la comuna 1 en el ultimo año.

        - *El problema en los medios*:

            - ¿Qué relación tiene la siniestralidad con el modo de transporte que usan los actores viales?
            - ¿Quiénes ocasionan más siniestros?
            - ¿Quiénes son las mayores víctimas?
            - **KPI:** Reducir en un 7% la cantidad de siniestros mortales de motociclistas en el ultimo año, respecto al año anterior.

        - *El problema desde las victimas*:

            - ¿Quienes son los actores más perjudicados? ¿Son más indefensos?
            - ¿El problema de la siniestralidad es un problema de género?
            - ¿La edad tiene algo que ver?
            - **KPI:** Reducir en un 10% la tasa de victimas muertas en siniestros viales de los últimos 6 meses. En comparación con el semestre anterior.
    
- ## Reporte de lo encontrado

    A continuación se realiza un resumen de los principales hallazgos del análisis de los datos:

    ![r6](vis/6.jpg)

    - Se puede determinar que el año con mayor numero de siniestros es el 2019, con un promedio de siniestros por dia de 28.
    - Se observa un decrecimiento en el número de siniestros a inicios del año 2020 por razones de la pandemia y las restricciones de movilidad inpuestas.
    - El número de victimas siempre es mayor o igual al número de siniestros
    - A partir de Mayo 2020 el número de siniestros volvió a subir hasta llegar a los 800 siniestros por mes.

    ![r7](vis/7.jpg)

    - Se puede determinar que las horas de mayor número de siniestros se encuentran en las horas pico de la tarde, siendo las 5 de la tarde la hora con mayor número de siniestros.
    - Adicionalmente se puede observar que los días viernes, son los días con mayor numero de siniestros. Así como existe una tendencia de alta siniestralidad en los días laborales, en comparación con los fines de semana.

    ![r8](vis/8.jpg)

    - Acorde a la división política de la ciudad en Comunas podemos observar las comunas por niveles de siniestralidad, la comuna 1 es la zona con mayor número de accidentes en la ciudad. Esto puede suceder debido a que es la zona del centro de la ciudad y puede haber mayor tráfico. 
    - Existe una tendencia de mayor numero de siniestros entre más cerca se esté del centro de la ciudad.

    ![r9](vis/9.jpg)

    - En este mapa podemos observar la distribución de los siniestros en la ciudad y podemos ver una mayor densidad de siniestros en el centro de la ciudad.
    - Si observamos el número de siniestros en vías de alto tráficos podemos observar como la tendencia se desplaza hacia los límites de la ciudad, especialmente en la Avenida General Paz.
    - Si observamos el número de siniestros en vías de trafico medio, podemos observar la malla principal de la ciudad y las conexiones entre los limites, con un mayor número de siniestros en la zona centríca de la ciudad y con una tendencia de siniestralidad en los cruces de vias intermedias.
    - Si observamos el número de siniestros en vías de trafico bajo, podemos ver una mayor dispersión de los sientros en todas las zonas de la ciudad pero una mayor densidad en el centro de la ciudad. 

    ![r5](vis/5.jpg)

    - En este gráfico podemos observar la distribución de los siniestros identificando que las vias de tráfico medio son las vías con mayor número de siniestros, esto puede debersea a sus niveles de trafico y su extensión en toda la ciudad.

    - Adicionalmente, podemos ver que las 3 vías con mayor número de siniestros son: La Avenidad Paz General con 590 siniestros registrados, y las vias Rivadavia y Corrientes.

    ![r4](vis/4.jpg)

    - Este gráfico es muy interesante por que nos permite comparar los modos de transporte en función de su culpabilidad o vicitimización, encontramos que el automóvil sigue siendo el vehículo con mayor número de siniestros provocados o determinado como culpable con más de 4000 siniestros registrados.

    - Por otro lado podemos observar que la motocicleta es el vehículo con mayor número de siniestros reportados como la victima del suceso, con más de 5000 siniestros reportados.

    - También podemos observar una alta tendencia de victimas en las personas que se movilizan a pie y en bicicleta, con más de 4.500 casos.

    ![r3](vis/3.jpg)

    - Desde una visión del genero de las victimas podemos observar que el mayor número de fallecidos son los hombres con más del 70% de los casos, en el tema de victimas podemos observa como hay un fuerte impacto en el número de victimas por los hombres.

    - El porcentaje de victimas que son hombres es del 68%, dos terceras partes de la población total. Las mujeres representan el 32% de las victimas.

      ![r2](vis/2.jpg)

    - En este gráfico podemos observar el número de victimas de acuerdo a los rangos de edad, es importante mencionar que la población de Adultos Jovenes comprendidas sus edades entre los 18 y 29 años, representan el mayor número de víctimas. Por lo que sería bueno abordar políticas con un enfoque en esta población.

    - Con respecto a los actores viales podemos observar la misma tendencia que vimos anteriormente, con un mayor número de motociclistas registrados como victimas de siniestros viales. Posteriormente a los motociclistas, siguen los conductores con más de 2000 victimas.

    - Adicionalmente podemos observar que los hombres son los que mayor número de victimas representan, por lo que es importan abarcar el problema de la siniestralidad desde la masculinización del tráfico, para entender patrones psicologicos o comportamientos que afecta a esta medida.

![r14](vis/14.jpg)

- ## Conclusiones

    El análisis de los datos revela varios aspectos significativos sobre la siniestralidad vial en la ciudad:

    El año 2019 se destaca por registrar el mayor número de siniestros, con un promedio diario de 28. Sin embargo, a principios del año 2020, se observa una disminución en el número de siniestros, atribuida a las restricciones de movilidad durante la pandemia. A partir de mayo de 2020, los siniestros vuelven a aumentar, alcanzando hasta 800 por mes. Adicionalmente, se identifican las horas pico de la tarde, particularmente a las 5:00 p.m., como el momento con mayor número de incidentes. Además, los viernes destacan como los días con mayor cantidad de siniestros, mostrando una tendencia de siniestralidad más alta en los días laborales en comparación con los fines de semana.

    El análisis por comunas revela que la Comuna 1, ubicada en el centro de la ciudad, presenta el mayor número de accidentes. Esta tendencia sugiere una mayor incidencia de siniestros en zonas con mayor tráfico vehicular, como el centro de la ciudad. Adicionalmente se observa una mayor concentración en el centro de la ciudad y en vías de alto tráfico como la Avenida General Paz. Además, se identifican patrones de siniestralidad en función del nivel de tráfico de las vías, con una alta densidad de siniestros en las zonas céntricas y en los cruces de vías intermedias.

    En términos de modos de transporte, los vehículos automóviles son los más frecuentemente culpables en los siniestros y las motocicletas son las víctimas más comunes en los siniestros, junto con los peatones y ciclistas.

    Por último, el análisis de género y edad revela que los hombres representan la mayoría de las víctimas, especialmente en el grupo de adultos jóvenes entre 18 y 29 años. Esta información destaca la necesidad de abordar la seguridad vial desde una perspectiva de género y edad para implementar medidas más efectivas de prevención de siniestros.


- ## Autor
    [Duván Robayo Roa](https://github.com/duvanroarq/)
    [LinkedIn](https://www.linkedin.com/in/duvanroarq/)