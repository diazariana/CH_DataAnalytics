# Coder House, Data Analytics
Proyecto del curso Data Analytics 2021

# Objetivo
Se analizarán los lugares en Roma donde hay más disponibilidad de Airbnb, los precios por áreas y la capacidad promedio por Airbnb, entre otras variables que nos permitirán entender en mayor profundidad las características principales de los Airbnb en Roma.  

# Alcance
El análisis va a describir las características de los Airbnb en Roma: el tipo de alojamiento, la capacidad promedio, los rangos de precios, además analizaremos atributos de los hosts y de las reviews.

# Usuario Final y nivel de aplicación del análisis
Este proyecto está orientado a todos los usuarios interesados en conocer información sobre los Airbnb en Roma. No es necesario contar con un glosario adicional para entender los conceptos que se utilizan en el proyecto.

# Breve Descripción de la Temática de los datos
Para esta temática se cuenta con un dataset con datos de los Airbnb de Roma. Tiene información de las ubicaciones, los hosts, precios, tipo de alojamiento, reviews y el requerimiento mínimo de noches de hospedaje, cantidad de camas y capacidad por Airbnb. Estos tres últimos datos no fueron utilizados ya que no se consideraron relevantes para el proyecto.

# Transformación de datos
En este apartado se detallarán los cambios realizados en los datos importados:<br>
● Se borraron las filas repetidas en la tabla Host, lo que permitió establecer la relación N:1 de Airbnb a Host.<br>

● Se cambió el tipo de número a datos de texto de:<br>
○ Airbnb: id_airbnb.

● Se cambió el tipo de datos de texto a número entero de:<br>
○ Airbnb: precio, mínimo noches, camas y capacidad.<br>
○ Reviews: cantidad_reviews y promedio_reviews.<br>
○ Coordenadas: coordenada_x y coordenada_y.<br>

● Se cambió el tipo de dato de texto a número decimal de: <br>
○ Coordenadas: se crearon las coordenadas correctas debido a que no contaban con el formato correspondiente, en algunos casos no se importaron los ceros y en otros se importaron números de más. Ejemplo una coordenada que debería ser 41.8900 se importó como 4189, y 41.8911 se importó como 418911. Esto se solucionó generando unas nuevas columnas de tipo número decimal llamadas Nueva_x y Nueva_y con las correcciones correspondientes. Además, a Nueva_x se le asignó la categoría de datos Latitud, y a Nueva_y Longitud. <br>
○ Reviews: Algo similar ocurrió con promedio_reviews, por lo que se generó una nueva columna llamada Promedio_Reviews_corregido.<br>

● Se agregaron las siguientes columnas a la tabla Airbnb: <br>
○ Precio por persona: Se dividió el precio por la capacidad del airbnb para encontrar el precio por persona, es un número decimal.<br>
○ Tipo Agrupado: se agruparon las propiedades en las categorías más destacadas y abarcativas con la función Switch.<br>
○ Rango precios: Se agruparon los precios en distintos rangos para poder graficarlos de manera sencilla. Se utilizaron las funciones de PowerQuery. Se utilizó la función “Grupos de datos” de Power Bi para que cada rango tenga un valor asociado, y de esta forma poder ordenarlos de menor a mayor en el gráfico “Rango de Precios” en la solapa Precios.<br>
○ Capacidad agrupada: Se agrupó la capacidad en grupos para poder graficarlos de manera sencilla. Se utilizaron las funciones de PowerQuery.<br>

● Se agregaron la siguiente columna a la tabla Host: <br>
○ Propiedades del host: se utilizó la función if para indicar si el host tiene una, dos, tres o más de tres propiedades, para poder generar un gráfico de torta más simplicado.<br>

● Se agregó la siguiente columna a la tabla Lugar: <br>
○ Para poder identificar los 5 barrios más caros, y los 5 más baratos y poder usarlos como filtro en la Solapa Precios_2, se utilizó la función Switch agrupando los barrios correspondientes.<br>

● Se agregó la siguiente columna a la tabla Reviews: <br>
○ Promedio redondeado: se agrupan las reviews en tres grupos; <4, 4 y 5. Para esto se utilizó la función if y las reviews fueron redondeadas para abajo con la función Rounddown.<br> 

●Respecto a la tabla calendario, creamos una tabla calendario usando la fecha de última review. Se crearon dos columnas calculadas, una de año y otra de mes.<br>

# Análisis Funcional del Tablero
En este apartado se explicará la información incluida en cada solapa.<br>

● Solapa Número 1: Inicio<br>
En la primera solapa se encuentra el Inicio con botones a las distintas solapas. <br>

● Solapa Número 2: Ubicación<br>
Se analiza la ubicación, se agregó una tarjeta con la cantidad de Airbnb disponibles en Roma y un mapa de dichos lugares con los siguientes filtros:<br>
○ Barrios.<br>
○ Tipo.<br>
○ Rango de Precios.<br>
Utilizando los distintos filtros se puede ver la disponibilidad de Airbnb y la ubicación en el mapa. Además, se agregó un gráfico de distribución que se mantiene fijo, que analiza la cantidad de Airbnb por el tipo.

• Solapa Número 3: Precios<br>
Se crearon dos tarjetas, una de precio promedio por persona (La medida se llama Precio_prom_persona) y otra de precio promedio (Precio_promedio). Además, se sumaron tres gráficos:<br>
○ Gráfico de columnas 1 (Precio promedio): se pueden ver el precio promedio de los cinco barrios principales por Cantidad Airbnb. En este caso filtramos los primeros cinco barrios y agregamos una línea de constante con el precio promedio ($122) para poder comparar.<br>
○ Gráfico de columnas 2 (Precio promedio por persona): se pueden ver el precio promedio por persona de los cinco barrios principales por Cantidad Airbnb. En este caso filtramos los primeros cinco barrios y agregamos una línea de constante con el precio promedio ($39) para poder comparar.<br>
○ Gráfico circular: Realizamos este gráfico para poder ver la distribución de precios en los Airbnb según Rango Precio. <br>
Mediante marcadores se puede seleccionar ver el gráfico de Precio promedio o el de Precio Promedio por persona.<br>
Esta solapa fue pensada para que se pueda ver principalmente los precios, tanto sea por áreas como el precio promedio, el precio promedio persona y que proporción ocupa cada rango de precios. 

● Solapa Número 4: Precios_2<br>
Se incluyeron dos gráficos de embudo. <br>
o Gráfico de embudo 1 (Top 5 barrios más caros): Indica los precios promedio para una familia tipo de los cinco barrios más caros.<br>
o Gráfico de embudo 2 (Top 5 barrios más baratos): Indica los precios promedio para una familia tipo de los cinco barrios más baratos.<br>

● Solapa Número 5: Hosts<br>
Se muestran las diferentes características de los hosts, una tarjeta con la cantidad total, un gráfico lineal donde se muestra la cantidad de cuentas creadas como host desde 2008 a 2020, y un gráfico circular con la cantidad de propiedades que alquila un host.<br>

● Solapa Número 6: Capacidad<br>
Se busca analizar la capacidad de los lugares de Airbnb, para ello se agregó un filtro con la columna Tipo Agrupado. Además, se agregaron dos gráficos:<br>
○ Gráfico de barra 1(Capacidad promedio): Es un gráfico que se mantiene fijo al filtro. En este se puede observar la capacidad promedio por tipo de Airbnb, y se agregó una línea de constante con la capacidad promedio (3 personas) para poder comparar.<br>
○ Gráfico de barra 2 (Capacidad total): Incluye la capacidad total por barrio. Se utilizó un Tool Tip que permite ver la composición de aquella capacidad por Tipo (en cantidad de Airbnb y en porcentaje).<br>
○ Gráfico de líneas: Varía cuando se cambia el filtro de tipo de Airbnb. En este se puede ver el precio según la capacidad.<br>

Se analizó la capacidad promedio por tipo de Airbnb, la capacidad total por barrio y el precio promedio según la capacidad, esta última filtrando el tipo de Airbnb.<br>
Mediante marcadores se puede seleccionar ver el gráfico de Capacidad promedio o el de Capacidad total.<br>

●	Solapa Número 7: Reviews<br>
En la última solapa se analizaron los reviews con las que cuenta el database. Por un lado, se creó un filtro con los barrios de Roma. Se agregaron 3 elementos para analizar y todos ellos varían con el filtro:<br>

○ Gráfico de circular: En este gráfico se puede observar el puntaje de reviews utilizando la columna Promedio Redondeado.<br>
○ Medidor 1: Se puede ver el porcentaje de Airbnb sin reviews. Es necesario contar con este dato para saber que hay muchos airbnb nuevos o que nunca tuvieron una review, para ello creamos una medida llamada “Porcentaje sin reviews”.<br>
○ Medidor 2: En este medidor se puede observar los airbnb que recibieron reviews en los últimos dos años. Contemplamos dos años como plazo, debido a la pandemia de 2020 que generó menor turismo en la zona y por lo tanto, menor alquiler y reviews de airbnb. Este último medidor sirve para entender el porcentaje de Airbnb que se encuentra actualizado en términos de las reviews que recibió.<br>

# Medidas Calculadas
●	Medida calculada que contenga una variable y una función de agregación.<br>
○	Capacidad promedio (solapa 6)<br>
Para analizar la capacidad de los Airbnb, se creó una variable que sea el promedio de la capacidad de Airbnb, se redondeó para bajo y como número entero. En el caso de que la capacidad promedio sea 3,7 esto sería incorrecto, a lo sumo puede haber 3 personas en dicho caso. <br>

●	Medida calculada que contenga dos variables, una función de agregación y una función de inteligencia de tiempo.<br>
○	Reviews2019y2020(solapa 7)<br>
En este inciso se buscó ver qué cantidad de lugares de Airbnb tienen la última review en los últimos dos años. Para ello, se crearon dos variables, i, que es la cantidad de Airbnb que recibieron la última review en 2019 y 2020 y j que es la cantidad total de Airbnb. <br>

●	Cantidad Airbnb: cuenta los Airbnb con la función Count en función de id_airbnb de la tabla Airbnb.

●	Cantidad host: cuenta los Airbnb con la función Count en función de id_host de la tabla Host.

●	Precio_prom_persona: Precio promedio por persona, se utilizó la función Average en la columna calculada precio_por_persona (que resulta de dividir el precio por la capacidad).

●	Precio_promedio: Precio promedio de los Airbnb, se utilizó la función Averga en la columna precio.

●	Promedio_familia: Se utilizó la función Calculate, donde se calculará el promedio para aquellos Airbnb con capacidad igual a 4.

●	Porcentaje sin reviews: se calculó el porcentaje de Airbnb que no tienen dato de review (o sea que es cero), contando aquellas reviews igual a cero y diviendolas por la cantidad de Airbnb que si tienen reviews (puntaje de review mayor a cero).

●	Promedio reviews: Promedio del puntaje de las reviews con al función average sobre la columa promedio_reviews_corregido.

●	Host_con_airbnb: Permite ver qué cantidad de Airbnb tiene cada host. Se calculó esto agrupándolos con un Allexcept y diviendolo por la cantidad total de hosts.




