# Sistema de reconocimiento de dígitos: Lector de NIA

Diseño e implementación de un sistema de reconocimiento de números basado en la utilización del algoritmo de aprendizaje supervisado SVC para el reconocimiento de números en la lectura de los NIAs.


En primer lugar, para el entrenamiento de la máquina, hemos cargado un set de datos disponible en los datasets de sklearn. Esta base de datos está compuesta por una gran cantidad de imágenes de números escritos a mano. Cada una de ellas tiene un tamaño de 8x8 píxeles. Además, vienen acompañadas por su correspondiente target, necesario a la hora de relacionar la imagen con el dato correcto. En la Figura 5 se muestran algunos ejemplos de datos 
cargados acompañados en la esquina inferior izquierda por su valor correspondiente. 

Para comprobar la tasa de acierto que tiene nuestra máquina, hemos separado el conjunto en datos de entrenamiento y datos de test. El primer grupo será mayor que el segundo para que pueda aprender la mayor cantidad de ejemplos posibles, dedicando por ello, el 80% al entrenamiento y el 20% restante a las pruebas, como se adjunta a continuación.

Como se puede comprobar en los dígitos mostrados, no se ha cometido ningún error a la hora de predecir los valores. No obstante, calcularemos la matriz de confusión.

