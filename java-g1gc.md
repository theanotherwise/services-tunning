# G1GC

### GC Type vs Spaces vs Threads

| GC Type                       | Eden | Survivor | Old     | ParallelGCThreads | ConcGCThreads |
|-------------------------------|------|----------|---------|-------------------|---------------|
| **Young GC**                  |  +   |    +     |         |         +         |               |
| **Mixed GC**                  |  +   |    +     | partial |         +         |        +      |
| **Full GC**                   |  +   |    +     |    +    |         +         |               |
| **Concurrent Mark / Cleanup** |      |          |    +    |                   |        +      |

### Key JVM Parameters

| JVM Option                     | Meaning                          | Note                                     |
|-------------------------------|----------------------------------|------------------------------------------|
| MaxTenuringThreshold           | lower → faster to old (tenured) | `E→S→S→...` → promoted if age ≥ threshold |
| G1MixedGCCountTarget           | higher → softer cleanup         | number of Mixed GCs after Concurrent Mark |
| InitiatingHeapOccupancyPercent | lower → earlier CM trigger      | % of heap usage to start CM               |
| G1ReservePercent               | higher → larger safety buffer   | % of heap reserved to avoid Full GC       |

### Concepts

| Concept         | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| Object lifecycle| `Eden → Survivor (age++) → Old (if age ≥ threshold)`                        |
| Humongous       | objects ≥ 50% region size go directly to Old, span multiple regions         |
| STW GCs         | Young, Mixed, Full                                                           |
| Concurrent GCs  | Concurrent Mark, Cleanup (run with application)                             |
| G1 goal         | short pause times via incremental cleanup and concurrent marking            |

### Snippet

```bash
-XX:+UseG1GC
-XX:MaxGCPauseMillis=100
-XX:+UseStringDeduplication
-XX:InitiatingHeapOccupancyPercent=25
-XX:G1ReservePercent=25
-XX:MaxTenuringThreshold=8
-XX:G1MixedGCCountTarget=16
-XX:ConcGCThreads=48
-XX:ParallelGCThreads=96
```

# ZGC
