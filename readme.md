Webtoon-Análisis y recomendaciones
==================================

 Webtoon es una platafomra donde se publican comics o historietas que se publican en formato digital y en forma de tiras verticales, optimizadas para su lectura en dispositivos móviles y navegadores web, a este tipo de comic se le atribuye el nombre de webtoon. Estos son una evolución moderna de los cómics tradicionales, diseñados para el consumo en línea y la lectura en dispositivos móviles. Con su variedad de géneros y recomendaciones, ofrecen una experiencia de lectura envolvente y accesible para los amantes de las historias visuales en todo el mundo.  
 Ofrecer recomendaciones para cada género, significa que los lectores pueden recibir sugerencias basadas en sus preferencias de lectura . Esto facilita la exploración de nuevos títulos y géneros, permitiendo a los usuarios descubrir historias emocionantes y cautivadoras que de otra manera podrían haber pasado por alto.  
 Para el siguiente trabajo se empleó el dataset [webtoon\_final.xlsx](https://github.com/lucero-huaman/Webtoon-analysis-and-recomendations/blob/main/webtoon_final.xlsx) que tiene como diccionario de datos a [link](https://github.com/lucero-huaman/Webtoon-analysis-and-recomendations/blob/main/Diccionario%20de%20datos.png)

 ![Frame 4](https://iili.io/HtSp0DN.png)
 
Carga de datos
--------------

 Primero se importaron las bibliotecas necesarias para el manejo de datos y la generación de gráficas, posteriormente se importa el archivo xlsx.

 ![2](https://iili.io/HtUmz0u.jpg)
 
Limpieza y tratamiento de datos
-------------------------------

 En esta sección se busco realizar un analisis más profundo de los datos y realizar correcciones o crear nuevos campos de ser necesarios.

### Reducción de autores por cantidad de obras de un mismo género 

 Se encontró que algunos artistas poseen más de una obra las cuales pueden o no pertenecer a un mismo género, si esto no se soluciona puede ocurrir inconvenientes al momento de contabilizar a los artistas.

 ![22](https://iili.io/HDH2gaV.jpg) 
 
 Debido a lo anterior se eliminaron los duplicados de autor y género, estos resultados fueron guardados en un nuevo dataframe, para posteriormente contabilizar la cantidad de artistas por género. Siendo ROMANCE con 121 el género que posee la mayor cantidad de artistas.

 ![20](https://iili.io/HDH2lQs.jpg) !
 
 ### Identificación y corrección de nulos

 Para poder identificar problemas con los datos se emplean comandos como .info y .describe que nos dan un vistazo general del estado actual de los datos. Se identificó un nulo en la columna authors.

 ![3](https://iili.io/HtUmWeR.jpg) 
 
 Se cargan las filas con datos nulos en la cual podemos identificar el nombre del autor que se visualiza como NaN. Investigando se identifico que alias del autor es NA, sin embargo, python lo esta considerando como nulo, por lo que se reemplazara por otro nombre

 ![4](https://iili.io/HtUpuEX.jpg)
 
 Se ingresa el nombre del autor como Na en la fila 90 de la columna authors para que con ello se pueda realizar el calculo correcto de la cantidad de autores por género, más vistos, entre otros.

 ![5](https://iili.io/HtUpap4.jpg)
 
 ### Cálculo de actualizaciones por día

 Tras contar los valores por dia se identifico que los días de publicación se almacenan como un todo incluso si son varios días, ello dificulta el cálculo de los días de publicación u otros similares.

 ![6](https://iili.io/HtUp1QS.jpg) 
 
 Se creo un nuevo dataframe a partir de una función para separar los días si hay más de uno en el dataframe principal y se contabilizó los días de publicación, siendo el sábado el días con más actualizaciones de obras.

 ![7](https://iili.io/Htg9jzQ.jpg)
 
 ### Actualizaciones por género

 El procedimiento anterior se realizó nuevamente pero para el cálculo de días de publicación por género, los resultados se agruparon en un solo dataframe, siendo el género de romance el mayor con 186 actualizaciones durante la semana.

 ![11](https://iili.io/HtgH1Qp.jpg)
 
 Análisis de correlación
-----------------------

 El análisis de correlación es una herramienta esencial para comprender y sacar el máximo provecho de los datos. Sirve para identificar patrones y hacer predicciones informadas, sin emabrgo, esto no implica causalidad. En los resultados podemos observar que la mayor correlación positiva con 0.97 es entre los likes y views, en este caso los views son mayor a los likes debido a omisiones de selección o disminusión del grado de aceptación en el capítulo. También existe una correlación positiva entre la cantidad de suscriptores y views con 0.91 y suscritores con cantidad de likes por capítulo de 0.89.

 ![9](https://iili.io/Htg96IR.jpg)EDA
---

### Cantidad de actualizaciones por dia

 Se identificó que el día con más actualizaciones son los Sábados, seguido de los Lunes con 76 y Viernes con 75, cabe mencionar que el promedio de actualizaciones por día es de 72.

 ![10](https://iili.io/Htg9mkG.jpg)
 
 ### Cantidad de likes por género

 El género de THRILLER ocupa el cuarto puesto de cantidad de obras en la plataforma de Webtoon en Español, sin embargo a diferencia de los tres primeros que igualan sus posiciones en relación a la cantidad de likes recibidos , este es reemplazado por el género de comedia, de igual manera el género de Acción que ocupa el sexto puesto en la cantidad de obras publicadas, sin embargo, SLICE OF LIFE ocupa esta misma posición en con respecto a su cantidad de likes.

 ![12](https://iili.io/HtgHV4t.jpg)
 
 ### Cantidad de autores en cada género

 Está es una gráfica en donde se puede observar a mayor detalle lo hallado en la limpieza de datos en donde podemos observar que Webtoon en español cuenta con solo 2 artistas que abarcaron el género HISTORICAL, mientas que en ROMANCE hay 121.

 ![21](https://iili.io/HDH2vGj.jpg)
 
 ### Diagramas relacionados a los datos numéricos y al tipo de pase

 El Daily pass es una forma de promocionar y aumentar la cantidad de suscriptores y views de webtoons, en donde colocan algunos capítulos gratuitos en webtoons de pago. Podemos observar que estos no se aplican para webtoons con más de 30 capítulos, además ayudan a aumentar el rating hasta un 9. 
 
 ![14](https://iili.io/HtgH4ae.jpg)

### Diagramas relacionados a los datos numéricos y estado de publicación

 Existen 3 diferentes tipos de status de las obras en donde HIATUS significa que está en pausa, mientras de ONGOING significa que se encuentra en estado de publicación, por otro lado completed señala una obra culminada. La gráfica nos cuenta que ninguno de los webtoons en pausa(HIATUS) incluso si cuentan con pocos o muchos capítulos no pueden acceder a un daily\_pass, además los artistas suelen considerar el hiatus una vez superen el 8 de rating. La mayoría de los webtoons de los webtoons completos han contado con un daily pass como apoyo para la promoción de su obra, cabe recalcar que los únicos webtoons que cuentan con daily pass son los que estan finalizados, por otro lado los webtoons en publicación que tienen apartir de un promedio de 30 capítulos poseen un rating entre 9,5-10.

 ![15](https://iili.io/HtgHPyb.jpg)
 
 ### Cantidad de vistas por días 

 El día que cuenta con más vistas es el sábadoel al cual le sigue el jueves, también podemos mencionar que cada día existen más de 900.000M de vistas.

 ![16](https://iili.io/HtgHDMB.jpg)
 
 Recomendación de webtoons en cada género
----------------------------------------

### TOP 10 por género

 Webtoon cuenta con una sección de recomendaciones por género en donde se ordenan las obras según la preferencia del usuario, sin embargo, no se pueden aplicar múltiples restricciones para el orden, en este caso se ordenaron los 10 mejores webtoons según el género digitado, considerando el mayor rating, cant de likes, views y cantidad de capítulos como criterio de orden, siendo Relatos fantasmas el que cuenta con la mayor posición.

 ![17](https://iili.io/HtgJJ9a.jpg)
 
 ### El mejor en cada género

 Python cuenta con librerías que facilitan el acceso a la información al menor tiempo posible, por ello se creo un código para facilitar la visualización del mejor webtoon del género digitado con descripciones claves para conocer más sobre este.

 ![18](https://iili.io/HtgJoSn.jpg)
 
 Conclusiones
------------

 Webtoon es una plataforma que posee cómics modernos con diferentes formatos a los cuales se les atribuye el mismo nombre de la plataforma, estos han acumulado una gran cantidad de usuarios que los consumen con regularidad estos puede ser obras de pago o no, además cuenta con un función llama daily pass diseñada para atraer a los usuarios a consumir una obra que tiene capítulos de pago, pero que momentáneamente se encuentran de libre acceso.  
 Algo que se pudo identificar es que el daily pass solo se le otorga a webtoons que se encuentran finalizados y no cuentan con más de 30 capítulos, por otro lado también se halló que los artistas pueden considerar entrar en HIATUS una vez que superan un promedio de 8 de rating ya que su obra cuenta con una cantidad considerable de suscriptores que continuarán apoyando la obra apesar de una breve ausencia, también puede deberse a la presión por cumplir una fecha de entrega fija para cada nuevo episodio u factores externos.  
 En cuanto a las obras podemos decir que el género con más webtoons es ROMANCE el cual de igual manera es el que posee una mayor cantidad de likes, por el contrario el género de THRILLER es el que el cuarto con más obras, sin embargo, es superado por COMEDY en la cantida de likes, esto mismo ocurre con ACTION al cual lo supera SLICE OF LIFE en cantidad de likes. Esto implica potencial en dichos géneros que pese a no tener tantas obras publicadas supera en likes a otros género con mayor cantidad de webtoons. También podemos mencionar que los géneros con mayores días de publicación son DRAMA y FANTASY. Finalmente, se puede resaltar la sección que cuenta webtoon para la búsqueda y filtrado de obras, sin embargo, se recomienda el uso de filtros avanzados par ala visualización de obras segpun criterios como el rating, estado actual, cantidad de capitulo, entre otros.
