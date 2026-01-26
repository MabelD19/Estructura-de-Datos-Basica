# Semana 1
- **Reflexiona**

`5. Protocolo de Pensamiento en Voz Alta`

Entregable Esperado

· Documento de reflexión con tus respuestas a las 5 preguntas.

1. Lo primero que miré fue el nombre de la función y los nombres de las variables que aparecían al inicio.
Empecé por ahí porque me pareció lo más "familiar": pensé que el nombre me diría qué hace la función y las variables revelarían qué tipo de datos usa (lista, número, etc.).
También miré si había un comentario al principio o la firma de la función (los parámetros) porque eso me da una pista rápida sin tener que entender cada línea.

2. Sentí un poco de certeza cuando vi un bucle for (o while) que recorría toda una lista y luego comparaba o hacía algo con cada elemento. Cuando recorres una lista completa normalmente el tiempo crece con el tamaño de la lista, así que probablemente sea O(n).


3. No verifiqué si la función hacía llamadas a otras funciones cuya complejidad podría ser alta. Básicamente asumí que las líneas dentro del bucle eran operaciones "simples" sin costo extra.


4. Apliqué la regla automática: si hay un solo bucle que recorre n elementos, la complejidad es linear O(n). Ese automatismo viene de explicaciones de mi hermano e investigar en internet.


5. Paso 1: Leer la firma de la función y los nombres de variables para identificar los datos de entrada.

Paso 2: Buscar bucles y llamadas a funciones dentro del código. Contar si los bucles son secuenciales o anidados y anotar si hay llamadas recursivas o llamadas a funciones externas.

Paso 3: Estimar el coste de cada bloque y combinar los costes quedándome con el término dominante y omitiendo constantes.

· Tu "algoritmo personal" de 3-5 pasos para analizar complejidad.

1. Identificar entradas: ¿qué variables representan el tamaño n? (listas, arreglos, matrices, etc.)

2. Localizar estructuras de control: contar bucles, comprobar si están anidados y detectar recursión o llamadas costosas.

3. Calcular coste por bloque: asignar O(1), O(n), O(n^2), etc., a cada parte según lo observado.

4. Combinar y simplificar: sumar costes de secciones secuenciales, multiplicar para anidamientos, y quedarme con el término dominante (y eliminar constantes).

5. Verificar supuestos: revisar llamadas a funciones externas y operaciones dentro de bucles (por ejemplo, si una operación dentro del bucle es otra búsqueda que recorre la lista).

· Una debilidad identificada y un plan concreto para abordarla.

Debilidad:
Tiende a aceptar con rapidez una regla aprendida sin checar el contexto.

Plan para mejorar:
Practicar con ejercicios cortos
Revisar mis respuestas con soluciones
________

`6. Conexión Teoría-Práctica`

Entregable Esperado

· Mapa conceptual conectando: Concepto teórico → Aplicación profesional → Herramientas/Técnicas

**Complejidad temporal (Big-O)**

-- Aplicación: dimensionamiento de endpoints / elegir algoritmo de agregación (stream vs batch)

-- Herramientas: pprof / async-profiler / Datadog APM

**Complejidad espacial (memoria)**

-- Aplicación: decidir caching, compactación de estructuras, elegir Bloom filter vs hash set

-- Herramientas: heap profiler (YourKit, go pprof), metrics (Prometheus)

**Algoritmos O(n^2) vs O(n log n)**

-- Aplicación: elegir solución en code review o diseño (ej. merge intervals)

-- Técnicas: benchmarking (JMH, pytest-benchmark), micro‑profiling

**I/O-bound vs CPU-bound**

-- Aplicación: optimizar consultas DB (eliminar N+1) o mover trabajo a background

-- Herramientas: DB EXPLAIN, slow query logs, APM (New Relic/Datadog)

**Amortized complexity**

-- Aplicación: elegir estructuras concurrentes (ej. hash table rehashing) y dimensionamiento

-- Herramientas: stress tests, benchmarks

· 3 situaciones de tu futura carrera donde aplicarás análisis de complejidad.

1. Code review en un microservicio de alta latencia: detectar y cuantificar loops anidados o N+1 queries; proponer set-based queries o caching.

2. Diseño de un sistema de recommendations en tiempo real: estimar costo por usuario (O(1) amortizado por evento) vs batch recompute (O(n)), y dimensionar infraestructura.

3. Triage de un incidente de producción: usar tracing + flamegraphs para identificar si el hotspot es CPU-bound (algoritmo malo) o I/O-bound (mala estrategia de consultas), y priorizar fixes (cambiar algoritmo vs caching vs DB index).

· Lista de 2-3 herramientas de profiling/benchmarking que investigarás.

1. async-profiler (Java) / perf + FlameGraph (Linux): para CPU flamegraphs y encontrar hotspots reales.

2. go tool pprof / pprof (para binarios Go) o py-spy (Python): ver consumo CPU y stacks sin parar producción.

3. JMH (Java) y pytest-benchmark (Python): para microbenchmarks reproducibles y comparar implementaciones.

_____

**Checkpoint Metacognitivo - Fase REFLEXIONA**

· ¿Qué descubrí sobre mi propio proceso de pensamiento que no sabía antes?

Que aprendes mejor cuando puedes tocar: implementar la solución, perfilarla y ver flamegraphs

· ¿Cómo describiría mi "estilo" de análisis? ¿Soy más visual, más matemático, más intuitivo?

Estilo visual-práctico: con diagramas y ejemplos.

· ¿Qué conexión inesperada hice entre este tema y algo que ya sabía?

Complejidad y Diseño organizacional.

· Si empezara la semana de nuevo, ¿qué haría diferente en mi proceso de aprendizaje?

Investigar mas antes de empezar a hacer los ejercicios, porque avanzo sin saber que estoy viendo o de que estoy hablando.
