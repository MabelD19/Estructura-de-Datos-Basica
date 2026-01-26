# Semana 1
- **Comprende**

`1. Explorador de Complejidades`

Entregable Esperado

· Tabla comparativa de las 6 complejidades con: analogía personal que te haga sentido, patrón de código que la genera, y una situación donde la has visto o podrías verla.

| Complejidad | Analogía Personal | Patrón de código que la genera | Ejemplo |
|---|---|---|---|
| O(1) | Es una acción que no crece con el número de elementos (Tiempo constante). | Acceso directo por índice, asignación simple, hash lookup | Comprobar si una pila está vacía (peek), o acceder a un elemento por índice en un array. |
| O(log n) | Buscar una palabra en un diccionario dividiendo por la mitad, cada paso reduce el problema a la mitad. | Búsqueda binaria, recorrer árboles balanceados | Búsqueda binaria en una lista ordenada. |
| O(n) | Contar cuántas personas hay en una fila. | Un bucle que visita cada elemento una vez | Validación de datos en una colección. |
| O(n log n) | Organizar personas en filas por altura usando pasos de reducción. | Divide-y-vencerás con combinación lineal (merge sort) | Construcción de heaps y operaciones de prioridad. |
| O(n²) | Si cada persona saluda a cada otra persona una vez, el número de saludos crece como pares de personas | Bucles anidados sobre la misma colección | Implementaciones ingenuas de joins en bases de datos (nested loop join). |
| O(2^n) | Todas las combinaciones posibles de encender/apagar, cada interruptor duplica el número de combinaciones disponibles. | Recursión que bifurca en 2 ramas por elemento (generar subconjuntos) | Fuerza bruta en problemas combinatorios; generar todas las subsecuencias, enumerar particiones, solución ingenua del TSP (travelling salesman). |

· Responde: ¿Cuál fue la analogía que más te ayudó a entender y por qué?

La analogía de O(log n) fue la que más me ayudó a entender porque muestra claramente la idea de reducir el problema de forma exponencial en cada paso, es intuitiva, una acción "divide por dos" que baja rápidamente la cantidad restante por revisar.


___________________________________________________________



`2. El Caso de DataStream Inc.`

Entregable Esperado

· Diagnóstico escrito del problema de DataStream (máximo 200 palabras).

El procesamiento ha pasado de “segundos” a 47 minutos al aumentar los datos 50×. Los cálculos indican que el tiempo creció muchísimo más que la entrada: el comportamiento empírico es cercano a cuadrático O(n^2); probablemente porque hay comparaciones pareadas, joins no indexados o algoritmos de fuerza bruta. Además solo el 25% del trabajo es paralelizable (Amdahl), por eso triplicar máquinas da solo +20%. Más RAM sin cambiar algoritmo no reduce la cantidad de operaciones asintóticas ni la sección serial, por eso no resolvería el cuello de botella principal.

· Cálculos que demuestren tu análisis de la complejidad probable.

n0 = 10 000, n1 = 500 000 = 50(n0)

t1 = 47 min = 2820s

· Una recomendación concreta: ¿Qué complejidad deberían buscar y por qué?

Buscar O(n) como objetivo ideal; O(n log n) es aceptable si no se puede evitar ordenar/indexar. O(n) permite multiplicar n con multiplicador lineal (predecible y manejable).

_____________________________________________________


**Checkpoint Metacognitivo - Fase COMPRENDE**

· ¿Puedo explicar con mis propias palabras qué mide Big O sin mencionar "tiempo de ejecución en segundos"?

Big O describe cómo cambia la cantidad de trabajo que hace un algoritmo cuando aumenta el tamaño de la entrada.

· Si alguien me dice "mi algoritmo es O(n²)", ¿qué imagen mental se forma? 

Una cuadrícula "n × n". Cada celda representa una operación

· ¿Puedo predecir su comportamiento?

Tiene un comportamiento predecible si duplicas n, las operaciones crecen por 4; si n aumenta por un factor k, las operaciones aumentan por k².

· ¿Qué preguntas formulé a la IA que no había considerado antes de comenzar?

¿Qué es O(n) y sus demas funciones? ¿Que es la notación Big O? ¿Que son la complejidad temporal y espacial?

· ¿En qué momento sentí que "esto tiene sentido" y qué lo provocó?

Una visualización clara y hacer el conteo manual de operaciones para ejemplos pequeños.
