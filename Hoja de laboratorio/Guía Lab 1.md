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
# 1. Momento 2 — Ejecutar

#### 1. Traer y conocer el dato
* **Total de caracteres:** 1 679
* **Caracteres distintos:** 0 y 1
* **Cantidad de unos :** 397
* **Cantidad de ceros:** 1 282

#### 2. La llave: es_primo(n)
* **Resultado para 1 679:** Al ejecutar la función basada en el PSeInt de la clase 5, confirmamos que devuelve `False`. El número 1 679 no es primo.

#### 3. Las formas posibles: rectangulos(n)
* **Parejas encontradas:** Como 1 679 es el producto de dos números primos ($23 \times 73$), solo existen 4 formas de acomodarlo: (1, 1679), (1679, 1), (23, 73) y (73, 23).
* **Pregunta de fondo:** Quien diseñó el mensaje eligió un número semiprimo a propósito para que el receptor solo tuviera dos opciones reales para intentar armar el dibujo ($23 \times 73$ o $73 \times 23$) y no se perdiera entre las 40 combinaciones que habrían resultado con un número como 1 680.
* **Optimización:** Al limitar la búsqueda hasta la raíz cuadrada ($\sqrt{n}$), redujimos el costo computacional para el número 1 000 000 de 1 000 000 de vueltas a solo 1 000 vueltas (un ahorro del 99.90%).

#### 4. Ver: filas_de y dibujar
* **Análisis del dibujo:** Al probar con 73 columnas el resultado es puro ruido visual. Al probar con **23 columnas**, se revela una imagen vertical clarísima. La disposición real del mensaje es de 73 filas por 23 columnas.

#### 5. Leer: leer_numero y columna
* **Dirección de lectura:** Los bits se deben leer **de arriba hacia abajo** en las columnas verticales para que la traducción tenga sentido.
* **Marcas de número:** Sí, la última fila actúa como un marcador de posición (un bit en 1) que avisa dónde termina el número binario.
* **Análisis de la Sección 2 (Elementos Químicos):** Usando el código del monitor, aislamos de las filas 5 a 10 los números atómicos: `[1, 6, 7, 8, 15]`. Al buscarlos en la tabla periódica, corresponden a **Hidrógeno (1), Carbono (6), Nitrógeno (7), Oxígeno (8) y Fósforo (15)**, los componentes esenciales del ADN humano.

#### 6. Inventario del Mensaje de Arecibo

| Filas | Qué creemos que dice | ¿Lo leímos con código o lo adivinamos? | ¿Cómo lo comprobaríamos? |
| :--- | :--- | :--- | :--- |
| **0 – 4** | Los números del 1 al 10 en sistema binario. | **Leído con código** | Corriendo las funciones `columna` y `leer_numero` en el bloque superior de la cuadrícula. |
| **5 – 10** | Los números atómicos de los elementos del ADN (H, C, N, O, P). | **Leído con código** | Con el script automático del monitor que detectó la Sección 2 y arrojó la lista `[1, 6, 7, 8, 15]`. |
| **11 – 29** | Las fórmulas químicas de las bases nitrogenadas y azúcares del ADN. | **Adivinado con los ojos** | Extrayendo secuencialmente los bloques binarios verticales y validando si corresponden a las proporciones moleculares. |
| **30 – 49** | La representación gráfica de la doble hélice del ADN junto a la cantidad de nucleótidos. | **Adivinado con los ojos** | Usando `leer_numero` en el eje central vertical para descifrar la cifra estimada del genoma humano. |
| **50 – 59** | La silueta física de un ser humano, el tamaño promedio de la población y el censo de la Tierra en 1974. | **Adivinado con los ojos** | Decodificando los bloques numéricos laterales para verificar la altura en longitudes de onda y la cantidad en miles de millones. |
| **60 – 65** | La posición relativa de la Tierra como tercer planeta en nuestro Sistema Solar. | **Adivinado con los ojos** | Analizando el desplazamiento de altura del tercer bloque en la fila de planetas respecto al Sol. |
| **66 – 72** | El dibujo del radiotelescopio de Arecibo que envió el mensaje y el diámetro de la antena. | **Adivinado con los ojos** | Midiendo las líneas binarias inferiores en la última sección para extraer la dimensión física del telescopio en base 2. |


---

# 2. Momento 3 — Explicar

Para descifrar este mensaje, el emisor asumió que el receptor conocería convenciones fundamentales como la organización de datos en un plano bidimensional, un orden específico de lectura, el sistema binario y la existencia de una tabla periódica universal. Aunque un extraterrestre podría deducir la geometría del rectángulo gracias a la lógica de los números primos, las convenciones biológicas y químicas terrestres las tendría que adivinar, ya que dependen de nuestra experiencia en la Tierra. A partir de esto, concluyo que representar es llegar a un acuerdo mutuo sobre cómo transformar ideas, formas o conceptos de la realidad en un código de ceros y unos para que otra mente pueda reconstruirlos exactamente igual.



