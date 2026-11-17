# Sesión 1
## 1. Momento 1 - Predecir
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
## 1. Momento 2 — Ejecutar

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

## 1. Momento 3 — Explicar

### La lista de convenciones

| Convención que supuso el emisor | ¿Se puede deducir o hay que adivinarla? | ¿Por qué? |
| :--- | :--- | :--- |
| **Los bits forman un rectángulo** | Se puede deducir | El total de bits (1 679) es el producto de dos números primos ($23 \times 73$), lo que reduce las opciones geométricas a solo dos rectángulos posibles. |
| **Sistema numérico en base 2 (binario)** | Se puede deducir | Al ver una secuencia ordenada de conteo del 1 al 10 al inicio del mensaje, cualquier civilización con matemáticas puede notar el patrón de potencias de 2. |
| **Dirección de lectura (arriba hacia abajo)** | Se puede deducir | Solo leyendo las columnas de arriba hacia abajo la primera sección forma una secuencia lógica del 1 al 10; al revés no tiene sentido. |
| **Bit marcador al final de cada número** | Se puede deducir | Aparece de forma constante como una marca de referencia en la misma fila debajo de cada columna numérica para indicar dónde termina el dato. |
| **Tabla periódica y números atómicos** | Se puede deducir | Los elementos químicos y su número de protones son leyes universales de la física, por lo que otra especie puede asociar los números 1, 6, 7, 8 y 15 a los mismos átomos. |
| **Pictogramas terrestres (ADN, humano, telescopio)** | Hay que adivinarla | Un extraterrestre no conoce nuestra anatomía, cómo luce una antena parabólica ni nuestro sistema solar visto desde afuera; tendría que interpretar los dibujos por contexto. |

### Confrontación

En **P1, P2 y P3** predijimos que había que contar ceros y unos, buscar los divisores de 1 679 para armar una cuadrícula de $23 \times 73$ o $73 \times 23$, y adivinar el orden de lectura del mapa de bits. Al ejecutar el código, confirmamos exactamente las 4 formas posibles del rectángulo y que la disposición real es de 73 filas por 23 columnas. La diferencia estuvo en los detalles internos que no imaginamos antes de ver el dibujo: no sabíamos que los números estaban escritos en vertical ni que incluían un bit marcador en la base para separar el dato del fondo.

### La frase obligatoria

**Representar es** ponernos de acuerdo sobre cómo traducir ideas, números o dibujos de nuestra realidad a una secuencia de ceros y unos, de manera que otra mente pueda reconstruir el mismo significado sin perder la información en el camino.

### 7. La revelación (Comparación con el inventario)

* **Sección 1 (Números del 1 al 10):** Lo leímos **bien con código** usando las funciones columa y leer_numero. No se nos pasó nada importante; identificamos la dirección de lectura y los bits marcadores de posición.
* **Sección 2 (Elementos del ADN):** Lo leímos **bien con código** al extraer los números atómicos 1, 6, 7, 8 y 15. Confirmamos exactamente que representan al hidrógeno, carbono, nitrógeno, oxígeno y fósforo.
* **Sección 3 (Fórmulas de azúcares y bases del ADN):** Lo **adivinamos bien con los ojos** al ver los bloques agrupados debajo de los átomos, aunque se nos pasó traducir con código las cantidades exactas de cada molécula.
* **Sección 4 (Doble hélice del ADN y número de nucleótidos):** Lo **adivinamos bien con los ojos** gracias a la forma de espiral. Se nos pasó calcular el número binario gigante (más de 4 mil millones) que está en el centro vertical de la hélice.
* **Sección 5 (Silueta humana, altura y población):** Adivinamos **bien con los ojos** la figura humana. Se nos pasó descifrar los números laterales que indican la estatura promedio (1,76 m medidos en longitudes de onda) y la población mundial de 1974.
* **Sección 6 (Sistema Solar):** Lo **adivinamos bien con los ojos** al notar el Sol a la izquierda y la Tierra desplazada hacia arriba como el tercer planeta.
* **Sección 7 (Radiotelescopio de Arecibo):** Lo **adivinamos bien con los ojos** por la forma de la antena parabólica abajo. Se nos pasó leer el número binario de la última fila que indica su diámetro físico (305 metros).


# Tarea Puente

>[! question] ¿Por qué comparar dos huellas de 64 caracteres es una manera confiable de saber que dos archivos de 1 679 caracteres son idénticos? ¿Qué tendría que pasar para que dos mensajes distintos tuvieran la misma huella?

Comparar dos huellas SHA-256 de 64 caracteres es confiable porque esta función criptográfica es determinista y extremadamente sensible: cualquier cambio mínimo en un solo bit de los 1 679 caracteres altera por completo el resultado (efecto avalancha). Además, siempre genera una firma única de longitud fija sin importar el tamaño del archivo original. Para que dos mensajes distintos tuvieran exactamente la misma huella tendría que ocurrir una "colisión criptográfica". Dado que SHA-256 tiene $2^{256}$ combinaciones posibles, la probabilidad de que eso pase por casualidad o de forzarlo es prácticamente cero con la tecnología actual. Por eso, si las dos huellas coinciden, tenemos certeza absoluta de que ambos archivos son idénticos bit por bit.

### Parte B · Tabla de seguimiento y pila de `a_base_rec(1974, 6)`

> [!question] Tabla de seguimiento y pila
> Haz una fila por llamada, con `n`, `n // 6`, `n % 6` y lo que devuelve. Dibuja la pila: ¿qué queda esperando en cada llamada?

| Llamada | `n` | `n // 6` | `n % 6` | Devuelve |
| :---: | :---: | :---: | :---: | :--- |
| **1** | 1974 | 329 | 0 | `a_base_rec(329, 6) + [0]` ➔ **`[1, 3, 0, 5, 0]`** |
| **2** | 329 | 54 | 5 | `a_base_rec(54, 6) + [5]` ➔ **`[1, 3, 0, 5]`** |
| **3** | 54 | 9 | 0 | `a_base_rec(9, 6) + [0]` ➔ **`[1, 3, 0]`** |
| **4** | 9 | 1 | 3 | `a_base_rec(1, 6) + [3]` ➔ **`[1, 3]`** |
| **5** | 1 | — *(caso base: \(1 < 6\))* | — | **`[1]`** |

#### Esquema de la pila de llamadas

```text
  [ Llamada 5 ] n = 1    ──▶ Caso base (1 < 6): devuelve [1] hacia abajo
  ──────────────────────────────────────────────────────────────────────────────
  [ Llamada 4 ] n = 9    ──▶ Espera resultado de (1)   para concatenar: + [3]
  ──────────────────────────────────────────────────────────────────────────────
  [ Llamada 3 ] n = 54   ──▶ Espera resultado de (9)   para concatenar: + [0]
  ──────────────────────────────────────────────────────────────────────────────
  [ Llamada 2 ] n = 329  ──▶ Espera resultado de (54)  para concatenar: + [5]
  ──────────────────────────────────────────────────────────────────────────────
  [ Llamada 1 ] n = 1974 ──▶ Espera resultado de (329) para concatenar: + [0]
```

> **Nota sobre la pila:** Mientras la recursión baja, cada llamada deja pendiente su residuo (`+ [residuo]`) en la memoria esperando a que la llamada superior se resuelva. Al llegar al caso base (`n = 1`), los resultados suben y se van pegando en orden hasta formar `[1, 3, 0, 5, 0]`.

> [!question] ¿Cuál de las dos maneras prefieren y por qué? (Tres líneas)

Preferimos la versión recursiva (`a_base_rec`) por su claridad y elegancia matemática, ya que refleja directamente la definición de descomponer un número mediante divisiones sucesivas y entrega los dígitos en el orden correcto sin tener que invertir la lista al final. Sin embargo, para números extremadamente grandes la versión con ciclo (`a_base_ciclo`) es más segura en la práctica, porque evita agotar la memoria de la pila con demasiadas llamadas en espera.
### Parte C · Nuestra especie (Base 8)

> [!question] Diseño de la especie y sistema numérico
> El monitor lanza un dado y le asigna a cada equipo una base (2, 3, 5, 6, 8 o 12). Todos los números de su mensaje irán en esa base.

* **Nombre de la especie:** Klyntar
* **Base numérica elegida:** **Base 8** (sistema octal).
* **Justificación biológica y cultural:** Los Klyntar son organismos simbiontes amorfos originarios de una colmena cósmica. Al organizar su estructura celular y sus tentáculos de comunicación en grupos de ocho nodos simétricos (dos anillos de cuatro), toda su aritmética, medición del tiempo y transmisión de datos interestelares se fundamentan en el sistema octal (base 8).

#### Diseño del mensaje de los Klyntar (437 bits = 19 columnas × 23 filas)

1. **Contar en Base 8:** Escribimos los números del $1$ al $10$ en sistema octal ($1, 2, 3, 4, 5, 6, 7, 10, 11, 12$). Al llegar al octavo símbolo y ver el salto a $10_8$, el receptor descubre inmediatamente que nuestra base numérica es $8$.
2. **Quiénes somos:** Una ilustración geométrica de un núcleo simbionte central del cual se desprenden **8 nodos o tentáculos simétricos**, reafirmando visualmente nuestra biología y el porqué de nuestra base numérica.
3. **Dónde vivimos:** Un diagrama de una cordillera de tres montañas con el pico central elevado y el número **$2150$** escrito en base 8 ($4146_8$) a su lado, indicando la altitud en metros de nuestra base terrestre.
4. **Qué nos importa:** El pictograma de un grano de café partido por la mitad junto a la fórmula química de la cafeína ($C_8H_{10}N_4O_2$), con los subíndices $8, 10, 4, 2$ escritos en base 8 ($10_8, 12_8, 4_8, 2_8$).

---

> [!question] Contrato de lectura (Predicción para la Sesión 2 — ¡No mostrar a nadie!)

1. **Calcular el tamaño de la cuadrícula:** Contar el total de caracteres ($437$) y factorizarlo en sus dos únicos divisores primos ($19$ y $23$) para probar únicamente los dos rectángulos posibles.
2. **Identificar la orientación correcta:** Probar ambas disposiciones hasta notar que con **19 columnas** aparecen bloques ordenados separados por filas completas de ceros.
3. **Descubrir la dirección de lectura y el marcador:** Observar la primera sección y notar que cada número vertical termina en una fila base con un bit en `1` (marcador de fin de número) y que se leen de **arriba hacia abajo**.
4. **Deducir la Base 8:** Leer la secuencia inicial ($1, 2, 3, 4, 5, 6, 7, 10, 11, 12$) y comprender que, como los dígitos individuales llegan hasta el $7$ antes de pasar al $10$, todo el mensaje está codificado en **base 8**.
5. **Traducir los datos de altitud y química:** Aplicar la conversión de base 8 a decimal en las secciones inferiores para leer el número $4146_8$ ($2150\text{ m}$) junto a las montañas y los subíndices ($10_8, 12_8, 4_8, 2_8$) asociados al grano de café.
6. **Interpretar los pictogramas:** Asociar el dibujo radial de ocho puntas con la anatomía de los **Klyntar**, las montañas con nuestra ubicación geográfica y el grano central con nuestro recurso más preciado.

# Sesión 2
## 2. Momento 1 — Predecir 

> [!question] P4. ¿Qué fracción de su mensaje creen que la otra especie va a entender? Un número entre 0 y 1, y qué sección creen que se va a perder primero.

Creemos que van a entender aproximadamente tres cuartas partes del mensaje. Es muy probable que deduzcan las dimensiones del rectángulo por los números primos, el conteo inicial del $1$ al $8$ y el valor de la altitud. La sección que se va a perder primero es la **sección 4**, ya que el dibujo es un pictograma muy específico de nuestra cultura y, sin contexto previo, puede parecer una simple figura geométrica abstracta.

> [!question] P5. Si el canal daña 1 de cada 100 bits, ¿cuántos bits dañados esperan en su mensaje? ¿Y si lo mandan tres veces?

Como nuestro mensaje de los Klyntar tiene un total de **$437\text{ bits}$**, si el canal daña $1$ de cada $100$, esperamos que se dañen aproximadamente **$4.37\text{ bits}$**. Si lo mandamos tres veces ($437 \times 3 = 1\,311\text{ bits}$ transmitidos), esperamos alrededor de **$13.11\text{ bits}$ dañados** en total a lo largo de las tres copias; sin embargo, al comparar las tres copias entre sí y elegir el bit que se repita por mayoría en cada posición, la tasa de error final tras corregir se reduce casi a **$0\text{ bits}$**.

### 3. Las preguntas incómodas de la representación

> [!question] 1. Ancho fijo (Desbordamiento)
> Si cada número va en un renglón de `COLUMNAS` bits, ¿cuál es el número más grande que cabe en su base? ¿Qué pasa si quieren decir cuántos habitantes tiene Manizales?

En nuestro mensaje de **19 columnas** en **base 8** (`ANCHO = 3` bits por dígito), caben como máximo **$6\text{ dígitos octales}$** completos por renglón ($19 // 3 = 6$, sobrando $1\text{ bit}$). El número más grande que podemos escribir en un solo renglón es $777777_8$, que equivale a **$262\,143$** en decimal ($8^6 - 1$). Si intentamos escribir los habitantes de Manizales (aproximadamente **$458\,000$** personas, que en base 8 requiere 7 dígitos: $1576360_8$), ocurre un **desbordamiento**: el número no cabe en una sola línea. Para resolverlo, tendríamos que dividir el número en dos renglones seguidos (como hizo Arecibo con el 8, el 9 y el 10 usando dos columnas) o expresar la cifra en miles de habitantes ($458_{10} = 712_8$, que sí cabe perfecto en 3 dígitos).

> [!question] 2. Decimales y unidades de medida
> ¿Cómo dicen la altura de Manizales en metros si el otro no sabe qué es un metro, ni dónde va la coma?

No podemos usar metros ni comas decimales porque el metro es una medida arbitraria inventada en la Tierra. Para resolverlo, usamos una regla física universal inspirada en las sondas *Pioneer* y en Arecibo: **la longitud de onda de transición hiperfina del átomo de hidrógeno neutro**, que mide exactamente **$21.1\text{ cm}$** ($0.211\text{ m}$) en cualquier rincón del universo. En lugar de mandar "$2\,150\text{ m}$", dividimos esa altura entre la regla del hidrógeno ($2150 / 0.211 \approx 10\,190$) y enviamos el número entero **$10\,190$** (que en base 8 es **$23716_8$**, ocupando 5 dígitos). De ese modo evitamos los decimales y usamos una unidad comprensible para cualquier civilización con radiotelescopios.

> [!question] 3. Texto (ASCII / Unicode)
> ¿Por qué no pueden mandar la palabra "Manizales" en ASCII o en Unicode? ¿Qué sí pueden mandar?

No podemos mandar "Manizales" en ASCII ni en Unicode porque son **tablas de codificación convencionales humanas**: un extraterrestre que reciba el código binario `01001101` (`77`) solo verá un número entero, nunca sabrá que en nuestra cultura ese número representa la letra "M" ni mucho menos cómo suena o qué significa el español. En su lugar, sí podemos mandar **matemáticas puras, constantes físicas, estructuras químicas y pictogramas visuales**.

> [!question] 4. Forma (Dimensiones de la cuadrícula)
> ¿Cómo va a saber la otra especie cuántas columnas tiene su mensaje?

Lo resolvimos asegurando que la longitud total del mensaje sea un **número semiprimo** (el producto exacto de dos números primos: $19 \times 23 = 437\text{ bits}$). Al factorizar $437$, el receptor descarta las tiras unidimensionales de $1 \times 437$ y se queda únicamente con dos opciones rectangulares: $19 \times 23$ o $23 \times 19$. Al probar ambas, notará de inmediato que solo con **19 columnas** aparecen filas vacías de ceros que separan las secciones y un conteo ordenado del $1$ al $10_8$ al inicio.

> [!question] ¿Cuál de las dos protecciones elegirían para un mensaje que tarda 25 000 años en llegar, y por qué? Con sus números. Piensen en la diferencia entre detectar un error y corregirlo.

Para un mensaje interestelar que tarda **25 000 años** en llegar (como hacia el cúmulo M13), elegiríamos sin dudar la **repetición triple (`repetir3` + `votar`)**, aunque cueste **1 311 bits** frente a los **460 bits** de la paridad (el triple del tamaño original de **437 bits**).
* La paridad solo añade 23 bits, pero **únicamente detecta** qué renglón llegó dañado; no sabe qué columna exacta se alteró ni puede arreglar el bit. En un viaje de 25 000 años, el receptor no puede mandarnos un aviso pidiendo *"por favor reenvíen el renglón 4, que llegó corrupto"*, porque esperar una respuesta y retransmitir tomaría **50 000 años** adicionales. 
* Aunque la repetición exige gastar más energía y tiempo de antena para enviar **1 311 bits**, le entrega al receptor la capacidad de **corregir el daño por sí mismo** en destino mediante votación mayoritaria (`votar`). Como comprobamos en los 1 000 experimentos con ruido del 1 %, este método permite reconstruir el mensaje **100 % exacto** en casi **9 de cada 10 envíos** (~880 de 1 000) sin necesidad de pedir retransmisiones.

