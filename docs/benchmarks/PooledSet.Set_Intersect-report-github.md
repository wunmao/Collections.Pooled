``` ini

BenchmarkDotNet=v0.11.5, OS=Windows 10.0.18362
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview5-011568
  [Host] : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.8.3801.0
  Core   : .NET Core 3.0.0-preview5-27626-15 (CoreCLR 4.6.27622.75, CoreFX 4.700.19.22408), 64bit RyuJIT

Jit=RyuJit  Platform=X64  InvocationCount=1  
UnrollFactor=1  

```
|              Method |  Job | Runtime | CountToIntersect | InitialSetSize |      Mean |     Error |    StdDev |    Median | Ratio | RatioSD | Gen 0 | Gen 1 | Gen 2 | Allocated |
|-------------------- |----- |-------- |----------------- |--------------- |----------:|----------:|----------:|----------:|------:|--------:|------:|------:|------:|----------:|
|     **HashSet_Hashset** |  **Clr** |     **Clr** |            **32000** |        **8000000** |  **5.552 ms** | **0.1105 ms** | **0.1935 ms** |  **5.500 ms** |  **1.00** |    **0.00** |     **-** |     **-** |     **-** |         **-** |
| PooledSet_PooledSet |  Clr |     Clr |            32000 |        8000000 |  5.270 ms | 0.0998 ms | 0.1025 ms |  5.258 ms |  0.94 |    0.04 |     - |     - |     - |         - |
|        HashSet_Enum |  Clr |     Clr |            32000 |        8000000 |  4.065 ms | 0.0796 ms | 0.1286 ms |  4.035 ms |  0.73 |    0.03 |     - |     - |     - |   20744 B |
|      PooledSet_Enum |  Clr |     Clr |            32000 |        8000000 |  3.406 ms | 0.0675 ms | 0.0777 ms |  3.413 ms |  0.61 |    0.02 |     - |     - |     - |   20744 B |
|       HashSet_Array |  Clr |     Clr |            32000 |        8000000 |  3.997 ms | 0.0785 ms | 0.0964 ms |  3.975 ms |  0.72 |    0.03 |     - |     - |     - |   20744 B |
|     PooledSet_Array |  Clr |     Clr |            32000 |        8000000 |  3.279 ms | 0.0642 ms | 0.0834 ms |  3.279 ms |  0.59 |    0.03 |     - |     - |     - |   12552 B |
|                     |      |         |                  |                |           |           |           |           |       |         |       |       |       |           |
|     HashSet_Hashset | Core |    Core |            32000 |        8000000 |  5.611 ms | 0.1246 ms | 0.2116 ms |  5.617 ms |  1.00 |    0.00 |     - |     - |     - |         - |
| PooledSet_PooledSet | Core |    Core |            32000 |        8000000 |  5.059 ms | 0.0771 ms | 0.0721 ms |  5.064 ms |  0.89 |    0.03 |     - |     - |     - |         - |
|        HashSet_Enum | Core |    Core |            32000 |        8000000 |  3.800 ms | 0.0751 ms | 0.1786 ms |  3.739 ms |  0.69 |    0.04 |     - |     - |     - |   12568 B |
|      PooledSet_Enum | Core |    Core |            32000 |        8000000 |  3.393 ms | 0.0676 ms | 0.1052 ms |  3.382 ms |  0.60 |    0.03 |     - |     - |     - |   12568 B |
|       HashSet_Array | Core |    Core |            32000 |        8000000 |  4.085 ms | 0.0774 ms | 0.0860 ms |  4.078 ms |  0.72 |    0.03 |     - |     - |     - |   12560 B |
|     PooledSet_Array | Core |    Core |            32000 |        8000000 |  3.350 ms | 0.0661 ms | 0.0970 ms |  3.324 ms |  0.60 |    0.03 |     - |     - |     - |   12528 B |
|                     |      |         |                  |                |           |           |           |           |       |         |       |       |       |           |
|     **HashSet_Hashset** |  **Clr** |     **Clr** |           **320000** |        **8000000** |  **2.528 ms** | **0.0505 ms** | **0.1180 ms** |  **2.492 ms** |  **1.00** |    **0.00** |     **-** |     **-** |     **-** |         **-** |
| PooledSet_PooledSet |  Clr |     Clr |           320000 |        8000000 |  2.378 ms | 0.0455 ms | 0.0524 ms |  2.368 ms |  0.93 |    0.06 |     - |     - |     - |         - |
|        HashSet_Enum |  Clr |     Clr |           320000 |        8000000 | 12.552 ms | 0.2496 ms | 0.2670 ms | 12.447 ms |  4.91 |    0.32 |     - |     - |     - |   20744 B |
|      PooledSet_Enum |  Clr |     Clr |           320000 |        8000000 | 12.079 ms | 0.2418 ms | 0.2019 ms | 12.088 ms |  4.82 |    0.24 |     - |     - |     - |   20744 B |
|       HashSet_Array |  Clr |     Clr |           320000 |        8000000 | 12.529 ms | 0.2836 ms | 0.2368 ms | 12.476 ms |  5.00 |    0.23 |     - |     - |     - |   20744 B |
|     PooledSet_Array |  Clr |     Clr |           320000 |        8000000 |  9.973 ms | 0.2593 ms | 0.2298 ms |  9.922 ms |  3.97 |    0.24 |     - |     - |     - |   12552 B |
|                     |      |         |                  |                |           |           |           |           |       |         |       |       |       |           |
|     HashSet_Hashset | Core |    Core |           320000 |        8000000 |  2.746 ms | 0.0543 ms | 0.0937 ms |  2.720 ms |  1.00 |    0.00 |     - |     - |     - |         - |
| PooledSet_PooledSet | Core |    Core |           320000 |        8000000 |  2.396 ms | 0.0471 ms | 0.0579 ms |  2.387 ms |  0.87 |    0.03 |     - |     - |     - |         - |
|        HashSet_Enum | Core |    Core |           320000 |        8000000 | 12.805 ms | 0.2545 ms | 0.5024 ms | 12.701 ms |  4.69 |    0.26 |     - |     - |     - |   12568 B |
|      PooledSet_Enum | Core |    Core |           320000 |        8000000 | 11.693 ms | 0.1679 ms | 0.1488 ms | 11.700 ms |  4.25 |    0.10 |     - |     - |     - |   12568 B |
|       HashSet_Array | Core |    Core |           320000 |        8000000 | 11.679 ms | 0.1787 ms | 0.1395 ms | 11.697 ms |  4.23 |    0.08 |     - |     - |     - |   12560 B |
|     PooledSet_Array | Core |    Core |           320000 |        8000000 |  9.933 ms | 0.1932 ms | 0.1984 ms |  9.853 ms |  3.59 |    0.12 |     - |     - |     - |   12528 B |