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
### Parte C · Nuestra especie

> [!question] Diseño de la especie y sistema numérico
> El monitor lanza un dado y le asigna a cada equipo una base (2, 3, 5, 6, 8 o 12). Todos los números de su mensaje irán en esa base.

* **Nombre de la especie:** Klyntar
* **Base numérica elegida:** **Base 6** (sistema senario).
* **Justificación biológica y cultural:** Los Klyntar son organismos simbiontes amorfos originarios de una colmena cósmica. Como carecen de un esqueleto rígido con diez dedos como los humanos, organizan su estructura celular y sus tentáculos de comunicación en grupos de seis nodos simétricos. Por esta razón natural, toda su aritmética, medición del tiempo y transmisión de datos interestelares se fundamentan en el sistema senario (base 6).
### Diseño del mensaje de los Klyntar (437 bits = 19 columnas × 23 filas)

Para que la otra especie pueda armar el dibujo sin ambigüedades, diseñamos una cuadrícula semiprima de **19 columnas de ancho por 23 filas de alto**, dividida en cuatro secciones separadas por filas vacías de ceros:

1. **Contar en Base 6 (Obligatoria):** Escribimos los números del $1$ al $8$ en sistema senario (1, 2, 3, 4, 5, 10, 11, 12). Al llegar al sexto símbolo y ver el salto a $10_6$, el receptor descubre inmediatamente que nuestra base numérica es 6.
2. **Quiénes somos (Identidad Klyntar):** Una ilustración geométrica de un núcleo simbionte central del cual se desprenden 6 nodos o tentáculos simétricos, reafirmando visualmente nuestra biología y el porqué de nuestra base numérica.
3. **Dónde vivimos (Colmena en Manizales):** Un diagrama de una cordillera de tres montañas con el pico central elevado y el número 2150 escrito en base 6 ($13542_6$) a su lado, indicando la altitud en metros de nuestra base de operaciones terrestre.
4. **Qué nos importa (El Café):** El pictograma de un grano de café partido por la mitad junto a su fórmula química simplificada de cafeína ($C_8H_{10}N_4O_2$), con los subíndices $8, 10, 4, 2$ escritos en base 6 ($12_6, 14_6, 4_6, 2_6$).

---

> [!question] Contrato de lectura (Predicción para la Sesión 2 — ¡No mostrar a nadie!)

1. **Calcular el tamaño de la cuadrícula:** Contar el total de caracteres ($437$) y factorizarlo en sus dos únicos divisores primos ($19$ y $23$) para descartar las tiras de $1$ fila y probar únicamente los dos rectángulos posibles.
2. **Identificar la orientación correcta:** Probar ambas disposiciones ($23 \times 19$ y $19 \times 23$) hasta notar que con **19 columnas** aparecen bloques ordenados separados por filas completas de ceros.
3. **Descubrir la dirección de lectura y el marcador:** Observar la primera sección y notar que cada número vertical termina en una fila base con un bit en `1` (marcador de fin de número) y que se leen de **arriba hacia abajo**.
4. **Deducir la Base 6:** Leer la secuencia inicial ($1, 2, 3, 4, 5, 10, 11, 12$) y comprender que, como los dígitos individuales llegan hasta el $5$ antes de pasar al $10$, todo el mensaje está codificado en **base 6**.
5. **Traducir los datos de altitud y química:** Aplicar la conversión de base 6 a decimal en las secciones inferiores para leer el número $13542_6$ ($2150\text{ m}$) junto a las montañas y los subíndices ($12_6, 14_6, 4_6, 2_6$) asociados al grano de café.
6. **Interpretar los pictogramas:** Asociar el dibujo radial de seis puntas con la anatomía de los **Klyntar**, las montañas con nuestra ubicación geográfica y el grano central con nuestro recurso más preciado.
