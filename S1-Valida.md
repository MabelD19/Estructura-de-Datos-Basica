# Semana 1
- **Valida**

`7. El Auditor Implacable`

Entregable Esperado

· Registro de los 4 casos con: tu identificación de errores, la corrección que propondrías, y verificación de si encontraste todos.

1. 

    for i = 1 to n:
    j = n
    while j > 0:
        O(1)  // operación constante
        j = j / 2  // división entera, reduce j a la mitad


Error identificado: El análisis afirma que el bucle interno es "constante" y por tanto descarta su contribución logarítmica.

Corrección propuesta: O(n log n) tiempo, O(1) espacio.

Verificación: He encontrado el error intencional. No parece haber más errores en el análisis intencional.

2.  

     for i = 1 to n:
    for j = 1 to i:
        O(1)  // operación constante


Error identificado: Se ha calculado mal la suma de 1+2+...+n. 

Corrección propuesta: O(n^2) tiempo, O(1) espacio.

Verificación: He encontrado el error intencional. No parece haber más errores en el análisis intencional.

3. 

    function mergesort(A):
    if length(A) <= 1: return A
    mid = length(A) / 2
    left = mergesort(A[0:mid])
    right = mergesort(A[mid:])
    return merge(left, right)  // merge toma tiempo lineal en el tamaño de A


Error identificado: El análisis aplica incorrectamente un factor log extra a partir de la recurrencia.

Corrección propuesta: T(n) = Θ(n log n) tiempo, O(n) espacio adicional en la versión que usa buffers de merge.

Verificación: He encontrado el error intencional. No parece haber más errores en el análisis intencional.

4. 

    for i = 1 to n:
    found = false
    for j = 1 to n:
        if A[j] == target:
            found = true
            break
    if not found:
        O(1)


Error identificado: Se confunden claramente los casos. Aunque el caso medio pudiera ser O(n) total si target suele estar cerca del inicio.

Corrección propuesta: Mejor caso O(n), caso promedio depende de la distribución pero puede ser Θ(n^2) si la búsqueda en A es lineal por cada i.

Verificación: He encontrado el error intencional. No parece haber más errores en el análisis intencional.

· Porcentaje de errores detectados (meta: >75%).

Porcentaje = 4 / 4 = 100% (supera la meta >75%).

· Categorización: ¿Qué tipo de errores fueron más difíciles de detectar?

Errores en resolución de recurrencias: suelen ser sutiles porque involucran teoremas y es fácil introducir o quitar factores log por error.

________

`8. Simulación Empírica`

Entregable Esperado

· Tabla de datos con tus cálculos de razones entre tiempos consecutivos.

| n | A (s) | B (s) | C (s) |
| --- | --- | --- | --- |
| 100 | 0.00742 | 0.00088 | 0.00610 |
| 500 | 0.03325 | 0.01860 | 0.03874 |
| 1000 | 0.07210 | 0.08320 | 0.09417 |
| 2000 | 0.12880 | 0.31040 | 0.19541 |
| 5000 | 0.37450 | 2.16000 | 0.56954 |
| 10000 | 0.68600 | 7.68000 | 1.13610 |

· Conclusión para cada algoritmo: ¿Los datos empíricos confirman la predicción teórica?

1. Las razones medidas están cerca del orden de magnitud esperado y siguen la variación que induce el cambio en n.


2. Las medidas están a la escala esperada para cuadrático: la razón grande en 100→500 está a la misma orden y las otras razones están cercanas.


3. Las razones medidas siguen muy bien las razones esperadas para n log n.

· Explicación del patrón esperado: "Si un algoritmo es O(n²), al duplicar n, el tiempo debería multiplicarse por ___".

1. O(n): al duplicar n, el tiempo debería multiplicarse por ≈ 2 (en general: por n2/n1).


2. O(n^2): al duplicar n, el tiempo debería multiplicarse por ≈ 4 (en general: por (n2/n1)^2).


3. O(n log n): al duplicar n, el tiempo debería multiplicarse por ≈ 2 * (log(2n)/log n). Para grandes n en base 2 esto es ≈ 2*(1 + 1/log2 n) — ligeramente mayor que 2 y converge a 2 cuando n crece muchísimo.
