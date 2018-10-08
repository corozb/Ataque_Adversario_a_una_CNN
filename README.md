# Ataque a una Convolutional Neuronal Network (CNN)

Una Convolutional Neuronal Network (CNN) se usa para el procesamiento de imágenes ya sean fotografías o videos (Aunque también puede ser usado para procesar texto) y los clasifica de acuerdo a un entrenamiento previo.

Un Ataque Adversario es una técnica que usa para engañar **(hackear)** una red neuronal y da un resultado completamente diferente al que se visualiza en la imágen. Por ejemplo, le presentamos una imagen de un edificio y nos dirá que es un perro. En algunos casos podrá reemplazar la indentidad de una persona o para los coches de conducción autónoma podrá confundir señales de tránsito. Ésto se explica a que el output de una red neuronal se expresa como una propobabilidad y la imagen modificada ofrece una certeza de resultado mucho mayor que las otras imágenes por lo que la red optar por la más alta. 

Vamos a trucar entonces el sistema de la Red Neuronal **Inception_V3**, el cual es una dataset de imagenes entrenado sobreque el dataset **ImageNet**. Este dataset es diseñado por Google y puede clasificar imagenes en 1000 categorías diferentes, lo cual es un buen rendimiento. 

La técnica para trucar ésta red es similar a la técnica que se usa para entrenarla. Cuando se trabaja con una red neuronal la forma de entrenarla es a través de la modificación de sus parámetros:
- Tenemos unos datos de entrada y unos de salida en los cuales queremos que se encuentren una relación, esa relación viene definida en cómo están ajustados los parámetros.
- Para ajustar éstos parámetros se usan dos técnicas: **Backpropagation** y **Gradient Descend** 
- Estas dos técnicas lo que hace es pedirle a la red neuronal que, teniendo los datos de entrada y salida, responda a ¿Cuáles son los valores internos de nuestros parámetros para que el **error** en que se incurre al predecir un resultado sea el **mínimo**?
- Igualmente con éstas técnicas de optimización podremos realizar el **Ataque Adversario** simplemente cambiando la pregunta en un modelo pre-entrenado: ¿Cuál es el **máximo error** que podemos obtener al manipular los pixeles de la imágen?
En este caso contamos con un modelo cuyos parámetros ya están ajustados para que funcionen bien;  por ejemplo, clasificador de imágenes. Lo que buscamos no es reajustar los parámetros de entrada (podríamos dañarlo) sino modificar los píxeles de la imagen de entrada que serán nuestros parámetros de optimización. Esto es lo que se conoce como Ataques Adversarios.
- Con el fin de que la imagen no sea facilmente detectada por un humano adicionamos otra pregunta y es: ¿Cuál es el máximo error que podremos obtener modificando los pixeles de una imagen de entrada pero que la diferencia entre la imagen original y la perturbada sea mínima?

                'REAJUSTAR INPUT ---> MAXIMIMAR ERROR + MINIMIZAR PERTURBACIÓN'
                

Es de resaltar que para poder engañar nuestro modelo, no es necesario tener acceso a su funcionamiento interno. Simplemente con el hecho de tener un clasificador de imágenes, perturbar una imagen e ir testeando lo prodremos hacer. Lo más impresionante aún es que éstos ataques pueden ser transferidos entre modelos. Por lo que puedo entrenar en cualquier modelo y luego probarlo en otro y hackearlo.

