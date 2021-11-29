# Clasificador con naive bayes

En el presente proyecto se realizará un detector para predecir la aparición de diabetes en base a diferentes valores utilizados para el diagnóstico, para eso se hace uso de una red neuronal artificial basada en el dataset Pima Indians Diabetes Dataset 
Este conjunto de datos es del National Institute of Diabetes and Digestive and Kidney Diseases. 

En particular el dataset en el que se basa, son todos pacientes femeninos de al menos 21 años de edad de herencia Pima Indian.

Las variables:

*   Pregnancies (embarazos): Número de embarazos
*   Glucose: Concentración de glucosa en sangre a 2 horas de una prueba de tolerancia de glucosa oral.
*   BloodPresure (Presión sanguinea): Presión diastólica (mm Hg)
*   SkinThickness: Tamaño del pliege de la piel del triceps
*   Insulin: Insulina en sangre a 2 horas (mu U/ml)
*   BMI: Indice de masa corporal (peso en kg / (altura en metros)^2)
*   DiabetesPedigreeFunction: Una función que estima el likelihood de tener diabetes dado el historial familiar
*   Age: Edad (años)
*   Outcome: Variable 0 o 1 (0 no posee diabtes, 1 posee diabetes)

cPara el análisis se realiza primero un Análisis exploratorio de datos (EDA) completo del dataset, incluyendo: cantidad de valores nulos de las variables, número de personas para cada clase, análisis de distribuciones de las variables, etc.

A su vez se realiza una limpieza donde se eliminan los valores nulos y se eliminan las filas que no poseen datos.

El detector se realiza considerando las variables que son de interés para el correcto funcionamiento de la red neuronal. Para esto se prueba teniendo en cuenta diferentes variables de interes, como la edad, la presión sanguinea, la glucosa, la insulina, etc. de tal modo de maximizar la métrica de la red neuronal, que en este caso es el area bajo la curva ROC (AUC).

Se pueden ver en la presente carpeta 2 archivos además de este readme.

- Diabetes.csv: Dataset original

- main.ipynb: Es la Jupyter Notebook correspondiente al proyecto, donde se detallan todos los pasos seguidos para llegar al resultado esperado.

Una vez implementado el clasificador, se utiliza con el set de testeo para verificar el funcionamiento. Un análisis comparativo de las posibles combinaciones de parámetros de entrada a la red puede ser encontrado en la notebook main.ipynb pero en resumen se decide reemplazar los valores nulos por la mediana de la columna correspondiente y eliminar las columnas de BloodPressure y SkinThickness ya que con esa combinación de parámetros se logra maximizar la métrica en validación.

Finalmente, se obtuvo una métrica en Test de 0.693. Si se compara esto con lo resultante de Train y Validation para el modelo elegido (0.73 y 0.736 respectivamente) se aprecia que su valor no se redujo significativamente. De esta manera se considera que el modelo funciona correctamente y no hay evidencia de Overfitting.

