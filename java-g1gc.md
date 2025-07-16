# GC Type vs Spaces vs Threads
| GC Type                  | Eden | Survivor | Old     | ParallelGCThreads | ConcGCThreads |
|--------------------------|------|----------|---------|-------------------|----------------|
| **Young GC**             |  +   |    +     |         |         +         |               |
| **Mixed GC**             |  +   |    +     | partial |         +         |        +       |
| **Full GC**              |  +   |    +     |    +    |         +         |        -       |
| **Concurrent Mark / Cleanup** |      |          |    +    |                  |        +       |

# Parameterse

| JVM Option                     | Opis                                                                 |
|-------------------------------|----------------------------------------------------------------------|
| MaxTenuringThreshold          | lower → fast to old (tenured) `E→S→S→...` age ≥ threshold            |
| G1MixedGCCountTarget          | higher → soft cleanup — GCs to clean old after CM                   |
| InitiatingHeapOccupancyPercent| lower → CM starts earlier                                           |
| G1ReservePercent              | higher → more safety buffer — % of heap reserved to avoid Full GC   |
