<h1 align="center"> Proyecto Integral: Telecomunicaciones: identificar operadores ineficaces ☎️  </h1>

## Descripción
***
En este proyecto se trabaja en el servicio de telefonía virtual CallMeMaybe, el cual está desarrollando una nueva función que brindará a los supervisores y las supervisoras información sobre los operadores menos eficaces. 
Los clientes son organizaciones que necesitan distribuir gran cantidad de llamadas entrantes entre varios operadores, o realizar llamadas salientes a través de sus operadores. Los operadores también pueden realizar llamadas internas para comunicarse entre ellos. Estas llamadas se realizan a través de la red de CallMeMaybe.
Por regla de negocio entenderemos que un operador es ineficaz si tiene una gran cantidad de llamadas entrantes perdidas (internas y externas) y un tiempo de espera prolongado para las llamadas entrantes. 
Las tareas llevadas a cabo son:
*	Llevar a cabo el análisis exploratorio de datos
*	Identificar operadores ineficaces
*	Prueba de hipótesis estadísticas
*	Realización de clústeres para identificar características de operadores

Así mismo se realiza un presentación que se encuentra en formato PDF para que los stakeholders del proyecto logren obtener los datos, conclusiones y recomendaciones de su interés.

## Descripción de los datos 
El dataset comprimido `telecom_dataset_us.csv` contiene las siguientes columnas:

- `user_id`: ID de la cuenta de cliente
- `date`: fecha en la que se recuperaron las estadísticas
- `direction`: "dirección" de llamada (`out` para saliente, `in` para entrante)
- `internal`: si la llamada fue interna (entre los operadores de un cliente o clienta)
- `operator_id`: identificador del operador
- `is_missed_call`: si fue una llamada perdida
- `calls_count`: número de llamadas
- `call_duration`: duración de la llamada (sin incluir el tiempo de espera)
- `total_call_duration`: duración de la llamada (incluido el tiempo de espera)


El conjunto de datos `telecom_clients_us.csv` tiene las siguientes columnas:

- `user_id`: ID de usuario/a
- `tariff_plan`: tarifa actual de la clientela
- `date_start`: fecha de registro de la clientela


## Tareas 
### 1. Preprocesamiento de datos 
* Explorar los dato sy hacer correcciones a los tipos de datos
* Realizamos limpieza de datos analizando valores nulos y duplicados
* Exploramos outliers en los datos mediante numpy
### 2. Análisis exploratorio
Primero realizamos las gráficas generales para observar la distrubución de los datos;
como por ejemplo la cantidad de llamdas a través del tiempo, la duración de las mismas y la dsitribución de llamadas perdidas. 

Después agrupamos los datos por operadores para saber que operadores tienen más llamadas perdidas y saber si se sigue algún patrón. 

El siguiente insight es para conocer si los clientes tenían alguan influencia dentro de la atención, ya que como observamos a continuación se tienen diferentes tarifas las cuales puede ser que influyan en la rapidez o eficiencia del servicio. 
![grafica_clientes](https://github.com/user-attachments/assets/b3909710-d5c0-4cd7-b2c2-0b2721b3a6e1)

Posteriormente realizamos un análsis de cohortes para saber si es que la antigüedad de los clienetes es también un factor determinante. Dentro del notebook esto se visualiza medainte un heatmap como el que se ve a continuación: 
![heatmap](https://github.com/user-attachments/assets/0e0c4282-bcf6-4713-9c8b-d848b149f1e6)

### Análisis estadístico 
Primero calculamos la diferencia entre la media y otros valores atípicos como puede ser el número de llamadas perdidas, duración de llamadas o tiempo de espera de llamadas. 

Realizamos las pruebas de hipótesis correspondientes para analizar las siguientes hipótesis:

* La duración de llamdas de operadores eficaces y poco eficaces es la misma en cuanto a aquellos con varias llamadas perdidas
* La duración de llamdas de operadores eficaces y poco eficaces es la misma con tiempos de espera largos

### Pronóstico y predicciones 
Utilizamos la función de pandas `pd.get_dummies(df)`  para lograr convertir las variables de dataframe a tipo numérico y realizar una evaluación de algoritmos que nos permita seleccionar un modelo de machine learning que en un futuro podría ayudarnos a predecir si un operador tendría tendencia a la ineficacia, por ejemplo, con las llamadas perdidas o tiemposd e espera, los modelos seleccionados para este caso son: 

Regresión logística y Bosque de clasificación aleatorio.

Posterioemte mediante un dendrograma y una g´rafica de método del codo realizamos uan agrupación por clústeres con variables del dataset y conocer las características de operadores ineficaces dichas, agrupaciones se muestran mediante graficas de dispersión.

A continuación, se muestra el dendrograma y el gráfico de método del codo el cual nos indica el umero de clústeres a realizar: 

![dendrograma](https://github.com/user-attachments/assets/3c508d58-5363-4429-b8b8-1d587a5979d0)


![metodo del codo](https://github.com/user-attachments/assets/4ac3fb78-c707-411a-8267-52f9a963fed6)


## Tecnologías
Los recursos utilizados en este proyecto son:
* Librerías de Python 
	* Pandas 
	* Numpy
	* Matplotlib
	* Seaborn
  	* Plotly
  	* Scipy stats
	* Scikit Learn

* Jupyter Notebooks

Utilizamos las librería de Pandas y Numpy   para el preprocesamiento de los datos tratando valores ausentes  y duplicados así como identificando outliers. 

Para temas de visualización de gráficas se utilizaron las librerías de Matplotlib y Seaborn, principalmente para la distribución de los datos, y gráficos de dispersión, esto debido al poco espacio de memoria que utilizan, se utilizó plotly para aquellas gráficas que específicamente requerían de interactividad. 

Para lograr la realización de las pruebas de hipótesis realizamos los cálculos mediante scipy, tanto con stats como con las fucnioens de z test, esto debido al tamaño de los datos. 

Finalmente, se utilizó la librería de Scikit Learn para obtener la información de los clústeres así como la agrupación de los mismos y la relación entre las diferentes variables. 


  ## Uso del código
  Todos los bloques de código se encuentran en el archivo .ipynb y el set de datos en el arhivo .csv. Para utilizarlo descargar los archivos csv, copie el cuaderno y ejecute los bloques de código.
