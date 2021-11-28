## Clasificador de Noticias

En el presente trabajo se muestra  un clasificador de noticias utilizando el conjunto de datos "fetch_20newsgroups" de la librería Sklearn.

La idea es clasificar las noticias en 20 grupos en base al texto de la noticia. Los grupos se conforman en base al material de la noticia, algunos ejemplos de grupos son: religion, autos, política en general, componentes de pc, etc.

Para esto se separa el set de datos en un set de train (entrenamiento) y un set de test (testeo) y se hace uso de un Clasificador Naive Bayes con Smoothing Laplaciano para la clasificación.

Previo a la clasificación a su vez se realiza un preprocesamiento de los textos para de esta manera mejorar el rendimiento de la red. De esta manera a los textos se les realizan los siguientes métodos:

- Una tokenización para separar el texto en tokens, que serán utilizados para posteriormente procesar individualmente cada palabra del texto.
- También se le aplica a los textos una lematización, la cual tiene en cuenta el análisis morfológico de las palabras para llevar palabras similares a su forma en común, por ejemplo los verbos se llevan a infinitivo y los plurales a singulares. 
- A su vez se eliminan las Stopwords, que son las palabras más comunes en un idioma, por lo que tenerlas en cuenta para el modelo que se desea implementar no aporta información relevante en cuanto a la categorización de los textos e implica mayor tiempo de procesamiento. Como ejemplo las palabras "a", "de", "y" etc. que son consideradas stopwords en el idioma español. 
- Luego de eliminar las Stopwords se realiza un Estemizado, el cual reduce las palabras a su raíz y es utilizado en el preprocesamiento del texto con el objetivo de unificar términos cuyos sufijos varían pero pertenecen a las mismas clases. Por ejemplo, las palabras "niños" y "niñez" que son reducidas mediante esta técnica a la raíz "niñ".

Una vez aplicadas las técnicas mencionadas anteriormente, es probable que el vocabulario siga contando con tokens que no sean palabras. Estos tokens, como signos de puntuación o números, no aportan información útil al procesamiento por lo tanto se eliminan posteriormente para mejorar el rendimiento del modelo.

Para contabilizar el número de ocurrencias de las palabras, se utilizan 2 métodos diferentes, Count Vectorizer y TFIDF. La diferencia entre ambos es que TFIDF contempla la diferencia que implica, en cuanto a la información que aporta, una palabra que aparece muchas veces o pocas. De esta manera, pondera negativamente las palabras que aparecen muchas veces, ya que no brindan información sobre la clasificación en cuestión.

Con todo lo comentado se pueden ver en la presente carpeta 4 archivos además de este readme.

- art_filt.pkl: Dentro de este archivo se encuentra el resultado del preprocesamiento de las palabras en el set de train, se realiza esto para realizar este procedimiento (preprocesar el texto) sólo una vez ya que conlleva tiempo.

- art_filt_test.pkl: Este archivo es similar al anterior sólo que realiza el preprocesamiento en el set de testeo.

- word_list.txt: es un archivo que lista las palabras que se tienen en cuenta para la clasificación de los textos, es simplemente para corroborar que el preprocesamiento funcione debidamente.

- main_ej1.ipynb: Es la Jupyter Notebook correspondiente al proyecto, donde se detallan todos los pasos seguidos para llegar al resultado esperado.

Una vez implementado el clasificador, se utiliza con el set de testeo para verificar el funcionamiento y el accurassy resultante para este dataset, con la finalidad de obtener una métrica (el accuracy), que indique qué tan bien funciona el modelo. 

Los accuracy obtenidos implementando el sistema con CountVectorizer y con TFIDF se pueden ver en la siguiente tabla:

<center>

|   Vectorizador  | Accuracy |
|:---------------:|:--------:|
| CountVectorizer |   0.73   |
| TfidfVectorizer |   0.76   |
 