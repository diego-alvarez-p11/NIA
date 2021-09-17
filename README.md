# Sistema de reconocimiento de dígitos: Lector de NIA

Diseño e implementación de un sistema de reconocimiento de números basado en la utilización del algoritmo de aprendizaje supervisado SVC para el reconocimiento de números en la lectura de los NIAs.


En primer lugar, para el entrenamiento de la máquina, hemos cargado un set de datos disponible en los datasets de sklearn. Esta base de datos está compuesta por una gran cantidad de imágenes de números escritos a mano. Cada una de ellas tiene un tamaño de 8x8 píxeles. Además, vienen acompañadas por su correspondiente target, necesario a la hora de relacionar la imagen con el dato correcto. En la Figura 5 se muestran algunos ejemplos de datos 
cargados acompañados en la esquina inferior izquierda por su valor correspondiente. 

Para comprobar la tasa de acierto que tiene nuestra máquina, hemos separado el conjunto en datos de entrenamiento y datos de test. El primer grupo será mayor que el segundo para que pueda aprender la mayor cantidad de ejemplos posibles, dedicando por ello, el 80% al entrenamiento y el 20% restante a las pruebas, como se adjunta a continuación. Adicionalmente, calcularemos la matriz de confusión.

<img src="https://user-images.githubusercontent.com/54302649/133783185-105b224d-23b4-4c64-b66b-ecd3c3ce8e13.PNG" width="350" height="350"> <img src="https://user-images.githubusercontent.com/54302649/133783528-fe433582-5e06-4d2f-8354-d79d467cac84.png" width="400" height="350">



