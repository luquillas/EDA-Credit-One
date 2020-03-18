# EDA-Credit-One
Exploración inicial de datos ejercicio Calificación de clientes Credit One

Curso Analisys de datos

Modulo 5.

En el último año se incrementó el número de clientes con incumplimiento en los pagos de los créditos. 
La empresa Credit One como calificadora crediticia arriesga a perder el negocio con varios socios por
lo que ha decido implementar una solución a partir del análisis de datos.

Se ha entregado un conjunto de datos con datos personales de los clientes así con histórico de pagos y el estado
de la cuenta en un determinado periodo de tiempo.

Luego de haber generado una exploración de datos inicial, se puede determinar que el mayor porcentaje de incumplimiento 
se da en los créditos menores o iguales los 150,000. De un total de 30,000 créditos incluidos en el conjunto de datos, 16,400 
créditos son menores o iguales a los 150,000, es decir un 54.67%. 

En el caso de los créditos con incumplimiento, de un total de 10069 créditos representando un 33.56% de la totalidad, 
6888 son con montos inferior o igual a los 150,000, representando este un 22.96% del total de los créditos otorgados.

El código puede ser visto en: https://github.com/luquillas/EDA-Credit-One/blob/master/codigo.ipynb

# Construcción, Evaluación y predicción

Para el entrenamiento se utilizaron 4 algoritmos distintos:
  * KNeighborsClassifier
  * SVC
  * GaussianNB
  * DecisionTreeClassifier
  
Se crearon también 4 conjuntos de datos y cada uno de estos conjuntos se evaluó con cada método anterior. Los conjuntos de datos se explican a continuación:
  * Conjunto original: Al conjunto original de datos unicamente se le aplica cambios en el tipo de dato, para ajustarlo de    acuerdo al tipo de problema por resolver.
  * Conjunto sin correlación: Se elimina los atributos que presentan correlación.
  * Conjunto aplicando RFE: Eliminacion recursica de atributos, se seleccionan los atributos con mayor importancia por medio de funciones ya existentes. Para el caso de este ejercicio se seleccionan 4 atributos solamente.
  * Conjunto aplicando PCA: Analisis de componentes principales, se seleccionan los atributos de acuerdo a su varianza. Para este caso se eligen los 8 con mayor varianza, explicando el 74.01% de los datos.
  
Los conjuntos de datos se dividieron en un 75/25 para el entrenamiento y se entrenaron los 4 conjuntos aplicando los 4 modelos indicados, obteniendo un mejor rendimiento con el metodo SVC y el conjunto de datos reducido por medio del PCA.

Se realiza optimización sobre los dos métodos con mejor rendimiento, ajustando los parametros C y gamma para el SVC y var_smoothing y priors para el algoritmo GaussianNB.
El mejor resultado es obtenido con SVC utilizando gamma='auto' y C=3.3, para un nivel de precisión de un 81.34%.

El código con sus salidas puede ser visto en: https://github.com/luquillas/EDA-Credit-One/blob/master/BuildandEvaluateModels.ipynb
