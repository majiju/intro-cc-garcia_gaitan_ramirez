# 1. Momento 1 - Predecir
>[! question] Pregunta 1
>Les llega una cadena de 1679 ceros y unos, sin nada más. ¿Qué es lo primero que intentarían para encontrarse sentido? Escriban tres ideas, en orden

>1. Contar cuántos 0 u cuántos 1 hay en total para ver si hay un balance o si predomina alguno
>2. Mirar si el número total de bits se puede dividir exactamente en grupos iguales para intentar acomodarlos en forma de matriz
>3. Revisar si existen bloques de bits que se repitan periódicamente  

>[! question] Pregunta 2
>Si alguien quisiera mandar un dibujo con bits, ¿cómo lo haría? ¿Qué tendría que adivinar quien lo recibe?

>1. Lo haría mapeando el dibujo en una cuadrícula, donde cada 1 represente un bloque pintado y cada 0 represente un espacio en blanco.
>2. Tendría que adivinar cuántas filas y cuántas columnas tiene la cuadrícula. Si se equivoca por una sola columna, el dibujo se romperá por completo y se verá como ruido visual. También tendría que deducir el orden de lectura (si se lee de izquierda a derecha, de arriba a abajo, en vertical, etc).

>[! question] Pregunta 3
>¿De cuántas maneras se pueden acomodar 1679 cuadritos en un rectángulo completo, sin que sobre ni falte ninguno? Respondan sin computador, con lo que saben de divisores.

>1. Para saber cuántas formas hay de acomodar los 1 679 cuadritos, necesitamos encontrar los divisores exactos de este número. Como nos explicaron en clase, el diseño del mensaje de Arecibo utiliza una propiedad matemática clave: **1 679 es el producto de exactamente dos números primos**. Haciendo el desglose aritmético, encontramos que: $$1 679 = 23 \times 73$$ Al ser 23 y 73 números primos absolutos, los únicos divisores que existen para 1 679 son: $1, 23, 73 \text{ y } 1 679$. Por lo tanto, solo existen **4 maneras posibles** de organizar los cuadritos en un rectángulo completo: 1. **1 fila** $\times$ **1 679 columnas** (una sola línea horizontal). 2. **1 679 filas** $\times$ **1 columna** (una sola tira vertical). 3. **23 filas** $\times$ **73 columnas** (un rectángulo de disposición horizontal). 4. **73 filas** $\times$ **23 columnas** (un rectángulo de disposición vertical). > **Nota de análisis:** El emisor del mensaje eligió a propósito un número semiprimo (producto de dos primos). De esta forma, cualquier civilización inteligente que reciba el mensaje e intente buscar dimensiones lógicas para reconstruir la imagen, se dará cuenta de que solo tiene dos opciones reales para probar en su cuadrícula ($23 \times 73$ o $73 \times 23$), descartando el ruido visual de inmediato. Si se hubiera usado un número como 1 680, habrían existido 40 combinaciones diferentes, haciendo el descifrado mucho más difícil.