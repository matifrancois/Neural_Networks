## Diabetes Detector 

----

En este proyecto se realizará una red neuronal sintética que permita la detección de diabetes en pacientes, basándose para esto en el dataset: "Pima Indians Diabetes Dataset". Se implementan de esta manera dos clasificadores:

- Clasificador de Diabetes utilizando regresión logística + Features Polinomiales. 

- Clasificador de Diabetes utilizando un MLP (Multilayer Perceptron). Para esto se desarrollan diferentes modelos de la red variando en cada modelo la cantidad de capas y la cantidad de neuronas en cada capa.

En todos los casos de estudio la métrica principal será el area bajo la curva ROC, y se busca además el umbral para la clasificación de forma tal que de maximizar el F2 score.

Luego se informan las siguientes métricas secundarias.

*   Especificidad
*   Sensibilidad
*   Valor Predictivo Positivo
*   Valor Predictivo Negativo

De esta manera se pudo obtener que en ninguno de los casos analizados con MultiLayer se obtuvieron mejores resultados que los obtenidos anteriormente utilizando regresión logística por lo tanto utilizamos un sistema de una sola neurona (regresión logística). Así, se opta por seleccionar al modelo final con los siguientes hiperparámetros:

- Reemplazo de valores nulos por la mediana.
- Eliminación de columnas Age y SkinThickness.
- PolynomialFeatures.
- Grado de PolynomialFeatures: 4.
- Learning Rate: 0.0001
- Learning Rate Decay: 0.0001
- Momentum: 0.99
- Regularización L2.

