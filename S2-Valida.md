# Valida

- **Actividad 7**

Para cada implementación: bug identificado, línea específica, corrección propuesta

Caso de prueba mínimo que revelaría cada bug

1.-

    función agregar(valor):
       si tamaño >= capacidad:     // Bug: debería ser ==
           redimensionar()
       datos[tamaño] = valor
       tamaño = tamaño + 1

Bug: La condición tamaño >= capacidad es demasiado permisiva. Si tamaño > capacidad (nunca debería pasar), ya hay un desbordamiento.

Corrección: if tamaño == capacidad

Caso de prueba que lo revela: Llamar a agregar() cuando tamaño = 5, capacidad = 5 debería redimensionar; con >= no lo hace.

Síntoma: Acceso fuera de límites al intentar escribir en datos[5].

Dificultad en producción: Media. El crash sería inmediato, pero en sistemas con manejo de memoria diferente podría corromper datos adyacentes.

2.-

    función insertar(índice, valor):
       // ... validaciones
       // Mover elementos (de izquierda a derecha)
       para i desde índice hasta tamaño-1:   // Bug: debería    ser desde tamaño-1 hasta índice
           datos[i+1] = datos[i]
       datos[índice] = valor
       tamaño++

Bug: El desplazamiento sobrescribe elementos porque va de izquierda a derecha. Si arr = [10,20,30] e inserto en índice 1, termina con [10,20,20].

Corrección: for i from tamaño-1 down to índice

Caso de prueba: Insertar en posición 1 de [1,2,3].

Síntoma: Pérdida de datos, duplicación de valores.

Dificultad: Alta, porque no causa crash pero corrompe datos silenciosamente.

3.-

    función eliminar(índice):
        valor = datos[índice]
        para i desde índice+1 hasta tamaño-1:  // Bug: falta cerrar el hueco completamente
            datos[i-1] = datos[i]
        tamaño--
        retornar valor

Bug: El último elemento no se elimina correctamente; queda duplicado en la penúltima posición.

Corrección: for i from índice to tamaño-2

Caso de prueba: Eliminar posición 0 de [1,2,3].

Síntoma: El arreglo queda con valores duplicados al final.

Dificultad: Media-alta, depende de si se verifica el contenido.

4.- 

    constructor(capacidadInicial):
        capacidad = capacidadInicial
        datos = nuevo arreglo[capacidad  // Bug: si capacidadInicial = 0
        tamaño = 0

Bug: Si capacidadInicial = 0, new array[0] puede causar problemas en algunos lenguajes o al intentar redimensionar.

Corrección: if capacidadInicial <= 0: capacidad = 1

Caso de prueba: Crear ArregloDinámico(0) y luego agregar un elemento.

Síntoma: Comportamiento indefinido, posible crash.

Dificultad: Baja-media, aparece temprano en desarrollo.

Ranking de los bugs de más fácil a más difícil de detectar, con justificación

Constructor con capacidad 0 → Crash temprano, fácil de depurar.

agregar() con condición >= → Crash en primera inserción cuando se llena.

eliminar() con hueco no cerrado → Requiere verificación de contenido.

insertar() con desplazamiento incorrecto → Corrupción silenciosa, difícil de rastrear.

---

- **Actividad 8**

Tablas de datos de los 3 experimentos con tus interpretaciones

1.-
|n|	+1|	+10	|+100|	1.5x|	2x|
|---|---|---|---|---|---|
|1000	|499,500	|49,950	|4,950	|~2,000	|~2,000
|10000	|49,995,000	|4,999,500	|499,500	|~20,000|~20,000|
|100000	|4,999,950,000	|499,995,000	|49,995,000	|~200,000	|~200,000|

El incremento +1 es catastrófico (O(n²)). Los factores exponenciales (1.5x, 2x) son dramáticamente mejores (O(n) amortizado).

2.-

|Posición	|Tiempo relativo (operaciones de desplazamiento)|
|---|---|
|0 (inicio)	|10,000|
|2500	|7,500|
|5000	|5,000|
|7500	|2,500|
|9999 (final)	|0 (si hay capacidad)|

Patrón: El costo es linealmente proporcional a la cantidad de elementos a desplazar: n - posición.


3.-
|n	|Capacidad	|% Desperdicio|
|---|---|---|
|1	|1	|0%|
|2|	2|	0%|
|3	|4	|25%|
|5|	8	|37.5%|
|9	|16|	43.75%|
|17|	32|	46.875%|

Máximo desperdicio: Justo antes de redimensionar, casi 50% (cuando tamaño = capacidad-1).
Mínimo desperdicio: Justo después de redimensionar, 0% (cuando tamaño = capacidad/2 + 1).

Gráfica (ASCII o descripción) del Experimento 1 mostrando las diferentes curvas

El incremento +1 es catastrófico (O(n²)). Los factores exponenciales (1.5x, 2x) son dramáticamente mejores (O(n) amortizado).

Conclusiones: 

¿Los datos empíricos confirman la teoría?

El crecimiento exponencial es órdenes de magnitud mejor que el incremental.

¿Hubo sorpresas?

El desperdicio de memoria con factor 2x puede llegar casi al 50%, lo cual es significativo en sistemas con memoria limitada.



---

- **Checkpoint Metacognitivo - Fase VALIDA**

¿Cuál de los 4 bugs me costó más encontrar?
El de insertar() con desplazamiento incorrecto, porque visualmente el código parece funcionar (no hay índices fuera de rango), pero corrompe datos.

¿Los datos empíricos me sorprendieron en algo?
Sí, la magnitud de la diferencia entre +1 y 2x: para 100,000 elementos, +1 requiere ~5 mil millones de operaciones vs ~200,000 con 2x.

Si tuviera que diseñar pruebas para el código de otro compañero, ¿qué probaría primero?
Los casos borde: arreglo vacío, un solo elemento, llenar hasta capacidad exacta, insertar/eliminar en extremos, y redimensionamiento múltiple.

¿Cómo ha cambiado mi confianza en mi propia implementación después de esta fase?
Aumentó significativamente al ver que puedo identificar bugs sutiles en código ajeno, pero también me hizo más consciente de mis posibles errores, por lo que ahora escribo casos de prueba sistemáticamente.
