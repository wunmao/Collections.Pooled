``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-009812
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  

```
|                       Method |      N |   Type |           Mean |          Error |         StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|----------------------------- |------- |------- |---------------:|---------------:|---------------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|  **StackICollectionConstructor** |   **1000** |    **Int** |     **1,093.1 us** |     **20.3631 us** |     **19.0476 us** |  **1.00** |    **0.00** |   **1289.0625** |           **-** |           **-** |          **3968.75 KB** |
| PooledICollectionConstructor |   1000 |    Int |       162.8 us |      1.0000 us |      0.9354 us |  0.15 |    0.00 |     12.6953 |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor |   1000 |    Int |     9,811.4 us |    155.9309 us |    145.8579 us |  8.98 |    0.14 |   2687.5000 |           - |           - |          8281.25 KB |
| PooledIEnumerableConstructor |   1000 |    Int |     9,150.9 us |     49.6698 us |     46.4611 us |  8.37 |    0.15 |     15.6250 |           - |           - |            85.94 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|  **StackICollectionConstructor** |   **1000** | **String** |     **2,497.7 us** |     **24.7256 us** |     **23.1283 us** |  **1.00** |    **0.00** |   **2554.6875** |           **-** |           **-** |             **7875 KB** |
| PooledICollectionConstructor |   1000 | String |       678.9 us |      7.8731 us |      7.3645 us |  0.27 |    0.00 |     12.6953 |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor |   1000 | String |    18,223.3 us |    180.7248 us |    169.0501 us |  7.30 |    0.10 |   5281.2500 |           - |           - |         16273.44 KB |
| PooledIEnumerableConstructor |   1000 | String |    14,265.2 us |    228.3455 us |    213.5946 us |  5.71 |    0.11 |     15.6250 |           - |           - |            93.75 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|  **StackICollectionConstructor** |  **10000** |    **Int** |     **9,388.6 us** |     **51.5633 us** |     **48.2324 us** |  **1.00** |    **0.00** |  **12656.2500** |           **-** |           **-** |            **39125 KB** |
| PooledICollectionConstructor |  10000 |    Int |     1,240.7 us |     10.0287 us |      8.8902 us |  0.13 |    0.00 |     11.7188 |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor |  10000 |    Int |   102,440.7 us |  1,419.4169 us |  1,327.7235 us | 10.91 |    0.14 |  41600.0000 |           - |           - |           128375 KB |
| PooledIEnumerableConstructor |  10000 |    Int |    86,231.2 us |  1,200.1207 us |  1,122.5937 us |  9.19 |    0.14 |           - |           - |           - |            85.94 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|  **StackICollectionConstructor** |  **10000** | **String** |    **18,897.1 us** |    **254.4250 us** |    **212.4564 us** |  **1.00** |    **0.00** |  **24968.7500** |           **-** |           **-** |          **78187.5 KB** |
| PooledICollectionConstructor |  10000 | String |     9,187.9 us |    106.0862 us |     94.0426 us |  0.49 |    0.01 |           - |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor |  10000 | String |   264,218.5 us |  2,660.1599 us |  2,488.3152 us | 13.98 |    0.19 |  41500.0000 |  41500.0000 |  41500.0000 |        256367.19 KB |
| PooledIEnumerableConstructor |  10000 | String |   145,923.8 us |  2,901.1558 us |  2,713.7429 us |  7.74 |    0.19 |           - |           - |           - |            93.75 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|  **StackICollectionConstructor** | **100000** |    **Int** |   **192,090.8 us** |  **3,712.2923 us** |  **4,694.8612 us** |  **1.00** |    **0.00** |  **42666.6667** |  **42666.6667** |  **42666.6667** |        **391012.12 KB** |
| PooledICollectionConstructor | 100000 |    Int |    15,581.8 us |     75.1578 us |     70.3027 us |  0.08 |    0.00 |           - |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor | 100000 |    Int | 1,240,413.5 us | 18,248.9746 us | 16,177.2406 us |  6.51 |    0.19 | 222000.0000 | 183000.0000 | 180000.0000 |       1025065.41 KB |
| PooledIEnumerableConstructor | 100000 |    Int |   835,675.3 us |  6,425.9369 us |  6,010.8254 us |  4.38 |    0.13 |           - |           - |           - |            85.94 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|  **StackICollectionConstructor** | **100000** | **String** |   **472,720.7 us** |  **7,518.1358 us** |  **6,664.6315 us** |  **1.00** |    **0.00** |  **26000.0000** |  **26000.0000** |  **26000.0000** |         **781462.8 KB** |
| PooledICollectionConstructor | 100000 | String |    92,418.8 us |  1,018.1937 us |    952.4190 us |  0.20 |    0.00 |           - |           - |           - |            39.06 KB |
|  StackIEnumerableConstructor | 100000 | String | 2,314,294.2 us | 26,771.5566 us | 25,042.1306 us |  4.89 |    0.10 | 374000.0000 | 334000.0000 | 332000.0000 |       2048815.55 KB |
| PooledIEnumerableConstructor | 100000 | String | 1,414,778.7 us | 12,407.2967 us | 11,605.7930 us |  2.99 |    0.05 |           - |           - |           - |            93.75 KB |