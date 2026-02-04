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
