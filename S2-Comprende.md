# Comprende

- **Actividad 1**

Diagrama propio que muestre la fórmula de acceso aplicada a un ejemplo diferente

Ejemplo: arreglo de caracteres (1 byte cada uno): ['A', 'B', 'C', 'D', 'E']
Dirección base: 3000

MEMORIA:

| 'A' | 'B' | 'C' | 'D' | 'E' |
|---|---|---|---|---|
| 3000 | 3001 | 3002 | 3003 | 3004 |

Fórmula: dirección(arr[i]) = 3000 + i × 1

Ejemplos:

-- arr[0] = 3000 + 0 × 1 = 3000 → 'A'

-- arr[3] = 3000 + 3 × 1 = 3003 → 'D'

-- arr[4] = 3000 + 4 × 1 = 3004 → 'E'

Tabla comparativa: operación vs. número de movimientos necesarios para un arreglo de n=10

|Operación|Posición|Movimientos requeridos|
|---|---|---|
|Insertar|Inicio|10
|Insertar|Medio (posición 5)|5
|Insertar|Final (sin redimensión)|0
|Eliminar|Inicio|9|
|Eliminar|Medio (posición 5)|4|
|Eliminar|Final|0|

Responde: ¿Por qué insertar al inicio es más costoso que insertar al final?

Porque al insertar al inicio, todos los elementos existentes deben desplazarse una posición a la derecha para hacer espacio. En un arreglo de n elementos, esto requiere n movimientos 'O(n)'. La contigüidad en memoria obliga a mantener el orden secuencial, por lo que cualquier inserción que no sea al final desplaza elementos.

---

- **Actividad 2**

Fórmula matemática del costo de n inserciones con incremento de +1

Costo total de copias para n inserciones = 1 + 2 + 3 + ... + (n-1) = n(n-1)/2
→ O(n²)

Fórmula del costo con duplicación de capacidad

Costo total ≈ 2n (en el peor caso)
Costo amortizado por inserción ≈ 2 → O(1) amortizado

Informe breve (150 palabras) explicando a un gerente no técnico por qué el sistema era lento

El sistema se vuelve lento porque cada vez que se agrega un producto nuevo, el programa está copiando toda la lista de productos existente a una nueva lista ligeramente más grande. Con 500,000 productos, agregar el producto 500,001 requiere copiar medio millón de registros. Esto ocurre con cada producto nuevo, haciendo que el tiempo de inserción crezca cuadráticamente. La solución es cambiar a un sistema que duplique el espacio cuando sea necesario, reduciendo drásticamente las copias y manteniendo el sistema rápido incluso con millones de productos.

---

- **Checkpoint Metacognitivo - Fase COMPRENDE**

¿Puedo explicar con mis propias palabras por qué arr[i] es O(1) usando la fórmula de dirección?
Sí, porque la memoria es contigua y la dirección se calcula con una fórmula matemática simple: dirección_base + (índice × tamaño_elemento). No importa si es el primer o el último elemento, el cálculo es directo y no depende del tamaño del arreglo.

¿Qué imagen mental tengo ahora de un arreglo en memoria?
Lo visualizo como una fila de cajas numeradas consecutivas, donde cada caja tiene una dirección predecible. Antes lo veía como una "lista" abstracta; ahora veo direcciones de memoria y saltos fijos entre elementos.

Si me preguntaran "¿por qué insertar al inicio es O(n)?", ¿podría dibujarlo paso a paso?
Sí: dibujaría un arreglo con elementos, mostraría que para insertar al inicio debo mover cada elemento una casilla a la derecha, uno por uno, antes de colocar el nuevo valor en la primera posición.

¿Qué conexión veo entre el análisis de complejidad de la Semana 1 y las operaciones de arreglos?
La Semana 1 me enseñó a clasificar algoritmos como O(1), O(n), O(n²). Ahora veo que cada operación de arreglos tiene una complejidad específica y predecible según su posición, y puedo justificarla con el modelo de memoria y desplazamientos.
