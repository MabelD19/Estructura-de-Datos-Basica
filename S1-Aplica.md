# Semana 1
- **Aplica**

`3. Analizador de Código`

Entregable Esperado

· Captura o registro de tu análisis de los 6 fragmentos con tu razonamiento escrito.

1.- Acceso a A[1], Asignación de y, Suma y return.

2.- El bucle 'for' se repite exactamente n veces, Cada repeticion hace O(1), Total de operaciones Θ(n) (n * O(1)).

3.- Tres bucles anidados, Si consideramos solo dos bucles anidados sería n^2; aquí es n^3 (producto de matrices). Si quisieras exactamente O(n^2) usarías solo dos bucles anidados.

4.- Cada iteración reduce el intervalo (high - low + 1) a la mitad aproximadamente, Cada iteración hace O(1) de trabajo.

5.- A simple vista hay un bucle externo y un bucle interno, parece producto (n * algo). Observa cuántas veces se ejecuta el cuerpo del while en total, contando sobre todos los i: Para un i fijo, el while hace aproximadamente ⌈log2(n / i)⌉ iteraciones.

6.- Combinación de recorrido lineal + recursión tipo merge/quick + coste adicional menor.


· Para cada uno, documenta: tu hipótesis inicial, el razonamiento paso a paso, y la conclusión final.

1.- Hipótesis inicial: O(1).

Razonamiento paso a paso:
La función hace una única operación: acceso a A[0] y retorno. No depende de n (el tamaño del arreglo); siempre hace la misma cantidad constante de trabajo.

Conclusión final: O(1).

2.- Hipótesis inicial: O(n).

Razonamiento paso a paso:
Inicialización de sum es O(1). El bucle 'for' se ejecuta exactamente n veces. Dentro del bucle la operación es una suma y asignación "O(1)" por iteración.

Conclusión final: O(n).

3.- Hipótesis inicial: O(n²).

Razonamiento paso a paso:
Bucle exterior ejecuta n veces. Para cada iteración del exterior, el bucle interior ejecuta n veces. Cada iteración hace trabajo O(1).

Conclusión final: O(n²).

4.- Hipótesis inicial: O(log n).

Razonamiento paso a paso:
Cada iteración del while reduce el intervalo [left, right] aproximadamente a la mitad.

Conclusión final: O(log n).

5.- Hipótesis inicial: Parece O(n^2) porque hay un 'for' y dentro un while.

Razonamiento paso a paso:
Observa que j comienza en n-1 y solamente se decrementa dentro del while; NO se reinicia en cada iteración de i. El bucle interior decrementa j, y cada decremento acerca j a 0.

Conclusión final: La sección mostrada es O(n). Aunque la estructura textual muestra un bucle anidado.

6.- Hipótesis inicial: Creo O(n (log n)^2) o similar.

Razonamiento paso a paso:
Si 'i' es pequeño, el número de iteraciones es aproximadamente log n; si i es grande (cercano a n), el número es pequeño. Dentro de cada iteración del while se ejecuta una binarySearch(A, ...) que cuesta O(log n), y una lookupHash que es O(1).

Conclusión final: O(n log n).

· Identifica cuál te costó más trabajo y por qué.

El caso que me costó más trabajo: el ejemplo 6.

Por qué:
Porque combina varias capas; una ordenación inicial "O(n log n)", un bucle exterior lineal, un bucle interior con crecimiento exponencial y una operación interna de coste logarítmico. Los demás ejemplos son directos: O(1), O(n), O(n^2) y O(log n) son inmediatos; el ejemplo 5 requiere la observación de que la variable del bucle interior no se reinicia, pero es un patrón clásico y relativamente sencillo tras identificar la técnica de dos-punteros.

___________

`4. Generador de Casos Límite`

Entregable Esperado

· Tabla comparativa con los cálculos de operaciones para cada caso.

| Caso | n | p (índice) | buscarLineal (comparaciones arr) | buscarDoble (i==j checks) | buscarDoble (arr checks) | buscarDoble (total primitivo) | Ratio (B_total / A) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| A | 10 | 5 | 6 | 5*10 + 6 = 56 | 6 | 62 | 10.33× |
| B | 100 | 50 | 51 | 5,051 | 5,102 | 5,102 | ≈100× |
| C | 1,000,000 | 999,999 | 1,000,000 | 1,000,000,000,000 | 1,000,000 | 1,000,001,000,000 | 1,000,001× |


· Explicación de 100 palabras sobre por qué códigos "que funcionan igual" pueden tener rendimientos radicalmente diferentes.

Dos implementaciones pueden producir resultados correctos pero tener costos algorítmicos muy distintos porque la estructura de control cambia la cantidad de operaciones según el tamaño de entrada. Un bucle simple realiza O(n) comparaciones; un bucle anidado puede convertir la carga a O(n^2) aun cuando las comprobaciones efectivas parezcan similares. Durante el desarrollo se suelen usar entradas pequeñas donde ambas versiones parecen rápidas, ocultando el comportamiento cuadrático a escala. Además, las optimizaciones del compilador o del intérprete no siempre compensan un crecimiento asintótico peor. Por eso es crucial evaluar la complejidad y medir rendimiento en datos grandes y en producción también.

· Propuesta de cómo detectarías este tipo de problemas en código real.

Revisión de complejidad durante code review: buscar bucles anidados, especialmente con el mismo rango/n y condiciones que no reducen el dominio.

_________

**Checkpoint Metacognitivo - Fase APLICA**

· ¿Qué patrón de código es mi "señal" inmediata de O(n²)?

for i = 0 to n-1: 
    for j = 0 to n-1:

· ¿Y de O(log n)?

while n > 1:

· Cuando la IA corrigió mi análisis, ¿qué paso del razonamiento me había saltado?

No hice un conteo de operaciones primarias por cada par (i,j).

· ¿Puedo ahora analizar código nuevo sin ayuda? Si/no,

No

· ¿qué me falta?

Necesito mas practica y mas ejercicios, y otra form de verlo

· ¿Cómo cambiaron mis preguntas a la IA entre el Reto 3 y el Reto 4?

Buscaba respuestas numéricas, ejemplos concretos y entender el proceso de razonamiento.
