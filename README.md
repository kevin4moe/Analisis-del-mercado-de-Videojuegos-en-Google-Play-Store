# Análisis del mercado de Videojuegos en Google Play Store: Clasificación por Rating de los usuarios

## Introducción

En este análisis del mercado de aplicaciones se busca encontrar la relación entre 16 categorías de videojuegos, contar con anuncios dentro de la app, el precio, poder comprar dentro de la app, ser una app seleccionada por Google, y el número de instalaciones. Para cumplir con nuestro objetivo realizamos un modelo de clasificación tipo Random Forest, el cual nos permite encontrar los factores más relevantes y dependiendo del nivel de precisión de nuestro modelo, predecir el comportamiento del rating de las apps de videojuegos por medio de sus características aquí analizadas.


### Setup

En el documento requeriments.txt, podrán encontrar que librerías utilizamos para este análisis, las principales librerías fueron:
-	Polars: Para realizar el manejo de datos y parte del análisis exploratorio.
-	Altair: Para la creación de graficas.
-	Scikit Learn: Para la implementación del modelo de machine learning y el uso de herramientas de soporte.


### Dataset
La base de datos utilizada fue [Google Play Store Apps](https://www.kaggle.com/datasets/gauthamp10/google-playstore-apps/data)


## Análisis exploratorio de datos

Primero analizamos el contenido del dataset, al tener más de 2 millones de registros necesitamos reducir su tamaño para poder manejarlo con mayor facilidad,  además de que agrupamos datos relevantes para mejorar la efectividad de nuestro modelo.

### Limpieza y segmentación de los datos

Eliminamos los valores perdidos, al ser en su mayoría las principales columnas que vamos a analizar se considero que eliminarlos era el mejor método para mantener la integridad de nuestro análisis sin incrementar el sesgo de nuestros datos rellenando los datos faltantes.


Se agruparon dos tipos de datos para mejorar la efectividad de nuestro modelo:
-	Instalaciones: Se agruparon en rangos de exponenciales con base 10 (1 al 10, 11 al 100, 101 al 1000, así sucesivamente hasta el 100 millones), aunque por falta de información se eliminaron los dos primeros rangos, debido a que en su mayoría no tenían datos sobre el rating de la app o era poco fiable por el bajo número de reseñas.
-	Rating: Se agruparon en rangos del 1 al 5, siendo los datos entre dos enteros agrupados al entre más grande entre los 2.

