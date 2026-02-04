# Aplica

- **Actividad 3**

Código completo del TAD ArregloDinámico (pseudocódigo o lenguaje real)

clase ArregloDinámico:
    datos: arreglo de enteros
    tamaño: entero
    capacidad: entero
    
    constructor(capacidadInicial):
        capacidad = capacidadInicial
        tamaño = 0
        datos = nuevo arreglo[capacidad]
    
    función obtener(índice):
        si índice < 0 o índice >= tamaño:
            lanzar error "Índice fuera de rango"
        retornar datos[índice]
    
    función establecer(índice, valor):
        si índice < 0 o índice >= tamaño:
            lanzar error "Índice fuera de rango"
        datos[índice] = valor
    
    función redimensionar():
        nuevaCapacidad = capacidad * 2
        nuevoArreglo = nuevo arreglo[nuevaCapacidad]
        para i desde 0 hasta tamaño-1:
            nuevoArreglo[i] = datos[i]
        datos = nuevoArreglo
        capacidad = nuevaCapacidad
    
    función agregar(valor):
        si tamaño == capacidad:
            redimensionar()
        datos[tamaño] = valor
        tamaño = tamaño + 1
    
    función insertar(índice, valor):
        si índice < 0 o índice > tamaño:
            lanzar error "Índice fuera de rango"
        si tamaño == capacidad:
            redimensionar()
        // Mover elementos a la derecha
        para i desde tamaño-1 hasta índice paso -1:
            datos[i+1] = datos[i]
        datos[índice] = valor
        tamaño = tamaño + 1
    
    función eliminar(índice):
        si índice < 0 o índice >= tamaño:
            lanzar error "Índice fuera de rango"
        valorEliminado = datos[índice]
        // Mover elementos a la izquierda
        para i desde índice hasta tamaño-2:
            datos[i] = datos[i+1]
        tamaño = tamaño - 1
        retornar valorEliminado
    
    función buscar(valor):
        para i desde 0 hasta tamaño-1:
            si datos[i] == valor:
                retornar i
        retornar -1

Tabla de complejidades: cada método con su O() temporal y espacial

|Método	|Complejidad Temporal	|Complejidad Espacial
|---|---|---|
|obtener	|O(1)	|O(1)|
|establecer	|O(1)	|O(1)|
|agregar (sin redimensión)|	O(1)|	O(1)|
|agregar (con redimensión)|	O(n)|	O(n)|
|agregar (amortizado)|	O(1)|	O(1)|
|insertar|	O(n)|	O(1)|
|eliminar|	O(n)	|O(1)|
|buscar|	O(n)|	O(1)|
|redimensionar|	O(n)|	O(n)|


Lista de al menos 3 casos borde que tu implementación maneja

1.- Índice negativo → lanza error.

2.- Índice mayor o igual a tamaño → lanza error (excepto en insertar, que permite índice = tamaño para agregar al final).

3.- Redimensionar cuando capacidad = 0 → se evita iniciando con capacidad mínima de 1.


---

- **Actividad 4**

Pseudocódigo de tu solución para cada problema

1.-

    función rotar(arr, k):
    n = longitud(arr)
    k = k mod n  // para k > n
    si k == 0: retornar arr
    
    // 1. Invertir todo el arreglo
    invertir(arr, 0, n-1)
    // 2. Invertir primera parte (0 a k-1)
    invertir(arr, 0, k-1)
    // 3. Invertir segunda parte (k a n-1)
    invertir(arr, k, n-1)
    
    función invertir(arr, inicio, fin):
    mientras inicio < fin:
        intercambiar(arr[inicio], arr[fin])
        inicio++, fin--


2.-

    función eliminarDuplicados(arr):
    si longitud(arr) == 0: retornar 0
    
    indiceUnico = 1
    para i desde 1 hasta longitud(arr)-1:
        si arr[i] != arr[i-1]:
            arr[indiceUnico] = arr[i]
            indiceUnico++
    retornar indiceUnico


3.-
    
    función moverCeros(arr):
    indiceNoCero = 0
    
    // Primero: mover todos los no-ceros al inicio
    para i desde 0 hasta longitud(arr)-1:
        si arr[i] != 0:
            arr[indiceNoCero] = arr[i]
            indiceNoCero++
    
    // Segundo: llenar el resto con ceros
    para i desde indiceNoCero hasta longitud(arr)-1:
        arr[i] = 0




Análisis de complejidad temporal y espacial de cada solución

    función elementoMayoritario(arr):
    candidato = null
    contador = 0
    
    // Primera pasada: encontrar candidato
    para cada num en arr:
        si contador == 0:
            candidato = num
        contador += (num == candidato) ? 1 : -1
    
    // Segunda pasada: verificar que realmente es mayoritario
    // (en este problema se garantiza que existe, pero es buena práctica)
    contador = 0
    para cada num en arr:
        si num == candidato:
            contador++
    
    si contador > longitud(arr)/2:
        retornar candidato
    sino:
        retornar -1  // no debería ocurrir según enunciado

Para al menos un problema, muestra la evolución de tu solución si la mejoraste

Usar un arreglo auxiliar para copiar no-ceros y luego ceros → O(n) tiempo, O(n) espacio.

---

- **Checkpoint Metacognitivo - Fase APLICA**

¿Puedo implementar agregar() sin mirar mis notas?
Sí, la lógica es: verificar si hay capacidad, si no, redimensionar (duplicar), luego colocar el valor en datos[tamaño] e incrementar tamaño.

Cuando la IA me hizo preguntas socráticas, ¿en qué momento me di cuenta de algo que no había considerado?
En el redimensionamiento: no había considerado qué pasa si capacidad = 0. También en insertar(): el orden del desplazamiento (de derecha a izquierda) es crucial.

De los 4 problemas, ¿cuál me costó más trabajo?
El de "elemento mayoritario" con O(1) espacio, porque el algoritmo de Boyer-Moore no es intuitivo a primera vista.

¿Cómo cambió mi aproximación a los problemas entre el primero y el último?
Al principio intentaba soluciones con arreglos auxiliares.
