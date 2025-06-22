# Taller-IV-Colecciones-Concurrentes
Simulación de una tienda en línea con múltiples productores y consumidores simultáneos en C# usando BlockingCollection

En el laboratorio se simulan múltiples hilos productores y consumidores utilizando colecciones concurrentes en C#. El mismo se desarrolla como parte de un taller donde se busca trabajar con programación concurrente. 

Estructura del programa
- Productores o Clientes: Son 2 hilos que crean pedidos y los agregan a una       `BlockingCollection`.
-   Consumidores o operarios: Al igual que los productores se usan 2 hilos que toman pedidos y los procesan.
-   Pedido: Para los pedidos se define una clase simple con `Id` y `Cliente`.

Justificación técnica
- Se usa `BlockingCollection` para evitar condiciones de carrera sin necesidad de usar `lock`.
- El método `GetConsumingEnumerable()` permite que los consumidores esperen automáticamente por nuevos elementos.
- `Interlocked.Increment` asegura que el contador de pedidos procesados sea seguro en entornos multihilo.

Problemas evitados por el uso de sincronización implícita.
Condiciones de carrera:
Al usar BlockingCollection, que gestiona internamente el acceso concurrente a la cola de pedidos. No es necesario utilizar lock para sincronizar hilos.

Lecturas/escrituras inconsistentes:
Gracias a Interlocked.Increment, permite garantizar que el contador de pedidos procesados sea incrementado de forma atómica, evitando así resultados incorrectos si dos hilos acceden al contador al mismo tiempo.


Deadlocks o bloqueos mutuos:
Como no se usa la sincronización manual (como múltiples lock anidados), se reduce de gran manera el riesgo de interbloqueos entre hilos.

.
     

     

