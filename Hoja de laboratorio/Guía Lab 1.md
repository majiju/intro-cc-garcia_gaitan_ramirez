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

>Como 1679 es el producto de dos números primos (23 x 73), sus únicos divisores son 1, 23, 73, 1679. Por lo tanto, solo existen 4 maneras posibles de acomodarlos:
>1. 1 fila x 1679 columnas
>2. 1679 filas x 1 columna
>3. 23 filas x 73 columnas
>4. 73 filas x 23 columnas

# 1. Momento 2 - Ejecutar
