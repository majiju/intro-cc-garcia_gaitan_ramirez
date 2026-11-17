>[! question] ¿Por qué comparar dos huellas de 64 caracteres es una manera confiable de saber que dos archivos de 1 679 caracteres son idénticos? ¿Qué tendría que pasar para que dos mensajes distintos tuvieran la misma huella?

Comparar dos huellas SHA-256 de 64 caracteres es confiable porque esta función criptográfica es determinista y extremadamente sensible: cualquier cambio mínimo en un solo bit de los 1 679 caracteres altera por completo el resultado (efecto avalancha). Además, siempre genera una firma única de longitud fija sin importar el tamaño del archivo original. Para que dos mensajes distintos tuvieran exactamente la misma huella tendría que ocurrir una "colisión criptográfica". Dado que SHA-256 tiene $2^{256}$ combinaciones posibles, la probabilidad de que eso pase por casualidad o de forzarlo es prácticamente cero con la tecnología actual. Por eso, si las dos huellas coinciden, tenemos certeza absoluta de que ambos archivos son idénticos bit por bit.

### Parte B · Tabla de seguimiento y pila de `a_base_rec(1974, 6)`

#### Tabla de seguimiento

| Llamada | `n` | `n // 6` | `n % 6` | Devuelve |
| :---: | :---: | :---: | :---: | :--- |
| **1** | 1974 | 329 | 0 | `a_base_rec(329, 6) + [0]` ➔ **`[1, 3, 0, 5, 0]`** |
| **2** | 329 | 54 | 5 | `a_base_rec(54, 6) + [5]` ➔ **`[1, 3, 0, 5]`** |
| **3** | 54 | 9 | 0 | `a_base_rec(9, 6) + [0]` ➔ **`[1, 3, 0]`** |
| **4** | 9 | 1 | 3 | `a_base_rec(1, 6) + [3]` ➔ **`[1, 3]`** |
| **5** | 1 | — *(caso base: \(1 < 6\))* | — | **`[1]`** |

#### Esquema de la pila de llamadas (¿Qué queda esperando?)

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

#### [!qesti¿Cuál de las dos maneras prefieren y por qué?

Preferimos la versión recursiva (`a_base_rec`) por su claridad y elegancia matemática, ya que refleja directamente la definición de descomponer un número mediante divisiones sucesivas y entrega los dígitos en el orden correcto sin tener que invertir la lista al final. Sin embargo, para números extremadamente grandes la versión con ciclo (`a_base_ciclo`) es más segura en la práctica, porque evita agotar la memoria de la pila con demasiadas llamadas en espera.
