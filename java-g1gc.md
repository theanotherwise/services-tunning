# GC Type vs Spaces vs Threads
| GC Type                       | Eden | Survivor | Old     | ParallelGCThreads | ConcGCThreads |
|-------------------------------|------|----------|---------|-------------------|---------------|
| **Young GC**                  |  +   |    +     |         |         +         |               |
| **Mixed GC**                  |  +   |    +     | partial |         +         |        +      |
| **Full GC**                   |  +   |    +     |    +    |         +         |               |
| **Concurrent Mark / Cleanup** |      |          |    +    |                   |        +      |

# Parameterse

| JVM Option                     | Meaning                          | Note                                     |
|-------------------------------|----------------------------------|------------------------------------------|
| MaxTenuringThreshold           | lower → faster to old (tenured) | `E→S→S→...` → promoted if age ≥ threshold |
| G1MixedGCCountTarget           | higher → softer cleanup         | number of Mixed GCs after Concurrent Mark |
| InitiatingHeapOccupancyPercent | lower → earlier CM trigger      | % of heap usage to start CM               |
| G1ReservePercent               | higher → larger safety buffer   | % of heap reserved to avoid Full GC       |
