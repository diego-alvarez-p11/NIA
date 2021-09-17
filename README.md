# Sistema de reconocimiento de dígitos: Lector de NIA

Diseño e implementación de un sistema de reconocimiento de números basado en la utilización del algoritmo de aprendizaje supervisado SVC para el reconocimiento de números en la lectura de los NIAs.


En primer lugar, para el entrenamiento de la máquina, hemos cargado un set de datos disponible en los datasets de sklearn. Esta base de datos está compuesta por una gran cantidad de imágenes de números escritos a mano. Cada una de ellas tiene un tamaño de 8x8 píxeles. Además, vienen acompañadas por su correspondiente target, necesario a la hora de relacionar la imagen con el dato correcto. En la Figura 5 se muestran algunos ejemplos de datos 
cargados acompañados en la esquina inferior izquierda por su valor correspondiente. 

Para comprobar la tasa de acierto que tiene nuestra máquina, hemos separado el conjunto en datos de entrenamiento y datos de test. El primer grupo será mayor que el segundo para que pueda aprender la mayor cantidad de ejemplos posibles, dedicando por ello, el 80% al entrenamiento y el 20% restante a las pruebas, como se adjunta a continuación. Adicionalmente, calcularemos la matriz de confusión.

<img src="https://user-images.githubusercontent.com/54302649/133783185-105b224d-23b4-4c64-b66b-ecd3c3ce8e13.PNG" width="350" height="350"> <img src="https://user-images.githubusercontent.com/54302649/133783528-fe433582-5e06-4d2f-8354-d79d467cac84.png" width="400" height="350">


Inicialmente, para reducir el número de errores que obtendríamos al cargar dígitos escritos a mano, utilizaremos números a ordenador. De esta forma, nos aseguramos de que el fondo es completamente blanco y que las cifras pueden observarse con mayor claridad. En la Figura 10 se presenta el NIA introducido. 

<img src="https://user-images.githubusercontent.com/54302649/133806627-50d6a1fe-a413-4bf2-b8fe-3ee0a4b1abb7.png" width="600" height="120">

Para efectuar la segmentación de la imagen 
en los distintos dígitos, vamos a sumar los valores de las columnas. Se sabe que los colores más claros tendrán en sus componentes RGB valores más próximos a 255, mientras que los más oscuros estarán próximos al cero. Los puntos comprendidos en la franja verde de la Figura 11, situada al 90% del valor máximo, serán considerados como 1 y el resto serán 0. A continuación, representamos la gráfica con los valores de las columnas sumados, donde los picos más altos corresponderán a los espacios entre dígitos.

<img src="https://user-images.githubusercontent.com/54302649/133806670-94ca92ed-2c4f-4e3d-b3c4-29ce8a45a6b4.png" width="600" height="300">

Como se comentó anteriormente, el color verde hace referencia a los valores a partir de los cuales calcularemos los puntos donde recortaremos la imagen. Estos puntos (separadores) serán la distancia media entre los dos extremos de cada pico, para dejar a ambos lados la misma distancia en blanco, quedando centrado el número en cada imagen. Una vez obtenidos los separadores, cogeremos los píxeles comprendidos entre dos separadores contiguos, obteniendo como resultado los distintos dígitos representados individualmente. La imagen que quedaría tras la segmentación sería la siguiente

<img src="https://user-images.githubusercontent.com/54302649/133806710-0f200ad8-d12c-4134-9719-2d2113a824b9.png" width="600" height="120">

Originalmente, la máquina fue entrenada con imágenes de 8x8 píxeles en escala de grises. Para realizar la validación de los NIAs, debemos transformar a grises las imágenes recortadas y así obtener la misma estructura. También se cambiarán los valores de los píxeles, comprendidos hasta ahora entre 0 y 1, por valores entre 0 y 16 como en la base de datos de entrenamiento. Acto seguido, debemos invertir los valores, pasando a tener el color blanco en el valor cero y el negro en el valor dieciséis.
Finalmente, eliminaremos los más bajos que obtengamos, pasando a valer cero. De esta forma, dejaremos solo el número y el resto de la imagen en blanco. Todos estos pasos se han realizado mediante un único bucle que se detalla en la Figura 14. El limitador marca a partir de qué valor, todos los números que hay por debajo de él se convierten en cero. Si bajamos el limitador, aparecen más grises alrededor del número y pueden darse predicciones erróneas. En contraposición, si subimos este valor, comenzarán a recortarse los grises, pudiendo perderse información del dígito. Cada imagen transformada, se guarda en un vector que utilizaremos como datos de prueba para predecir sus valores.

Los números estimados por el sistema reconocen a la perfección los números introducidos:

![image](https://user-images.githubusercontent.com/54302649/133808622-fea4c509-0598-4e0a-9a16-993919bf8974.png)








