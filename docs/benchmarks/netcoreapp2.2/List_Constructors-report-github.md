``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-010184
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  

```
|                       Method |      N |   Type |           Mean |          Error |         StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|----------------------------- |------- |------- |---------------:|---------------:|---------------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|   **ListICollectionConstructor** |   **1000** |    **Int** |       **250.8 us** |      **4.7275 us** |      **5.4442 us** |  **1.00** |    **0.00** |   **1290.2832** |           **-** |           **-** |          **3968.75 KB** |
| PooledICollectionConstructor |   1000 |    Int |       116.5 us |      0.3191 us |      0.2985 us |  0.47 |    0.01 |     17.7002 |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor |   1000 |    Int |     7,920.3 us |     19.0000 us |     17.7726 us | 31.68 |    0.78 |   2687.5000 |           - |           - |          8273.44 KB |
| PooledIEnumerableConstructor |   1000 |    Int |     7,254.3 us |     19.7193 us |     17.4806 us | 29.07 |    0.70 |     23.4375 |           - |           - |            93.75 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |   **1000** | **String** |       **607.8 us** |      **2.2931 us** |      **2.0328 us** |  **1.00** |    **0.00** |   **2556.6406** |           **-** |           **-** |             **7875 KB** |
| PooledICollectionConstructor |   1000 | String |       573.1 us |      2.1726 us |      2.0323 us |  0.94 |    0.00 |     17.5781 |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor |   1000 | String |    13,530.8 us |     40.7649 us |     36.1370 us | 22.26 |    0.09 |   5281.2500 |           - |           - |         16265.63 KB |
| PooledIEnumerableConstructor |   1000 | String |    13,311.1 us |     71.2922 us |     59.5322 us | 21.91 |    0.12 |     31.2500 |           - |           - |           101.56 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |  **10000** |    **Int** |     **2,635.9 us** |     **22.1088 us** |     **20.6806 us** |  **1.00** |    **0.00** |  **12656.2500** |           **-** |           **-** |            **39125 KB** |
| PooledICollectionConstructor |  10000 |    Int |       956.5 us |      3.6141 us |      3.2038 us |  0.36 |    0.00 |     17.5781 |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor |  10000 |    Int |    75,482.2 us |    490.2844 us |    458.6123 us | 28.64 |    0.32 |  41571.4286 |           - |           - |        128367.19 KB |
| PooledIEnumerableConstructor |  10000 |    Int |    66,454.5 us |    437.3999 us |    409.1441 us | 25.21 |    0.26 |           - |           - |           - |            93.75 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|   **ListICollectionConstructor** |  **10000** | **String** |     **6,248.8 us** |     **14.7185 us** |     **13.0476 us** |  **1.00** |    **0.00** |  **24992.1875** |           **-** |           **-** |          **78187.5 KB** |
| PooledICollectionConstructor |  10000 | String |     8,092.8 us |     21.4115 us |     20.0283 us |  1.29 |    0.00 |     15.6250 |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor |  10000 | String |   185,833.5 us |    686.8662 us |    642.4950 us | 29.72 |    0.11 |  41333.3333 |  41333.3333 |  41333.3333 |        256359.38 KB |
| PooledIEnumerableConstructor |  10000 | String |   126,976.4 us |    577.2476 us |    539.9578 us | 20.32 |    0.11 |           - |           - |           - |           101.56 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|   **ListICollectionConstructor** | **100000** |    **Int** |   **158,043.9 us** |  **2,497.4765 us** |  **2,336.1410 us** |  **1.00** |    **0.00** |  **36500.0000** |  **36500.0000** |  **36500.0000** |        **390935.07 KB** |
| PooledICollectionConstructor | 100000 |    Int |    14,359.9 us |     85.5357 us |     71.4262 us |  0.09 |    0.00 |     15.6250 |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor | 100000 |    Int |   994,071.4 us |  7,073.5134 us |  6,616.5688 us |  6.29 |    0.11 | 216000.0000 | 175000.0000 | 174000.0000 |       1025113.57 KB |
| PooledIEnumerableConstructor | 100000 |    Int |   640,896.5 us |  2,003.5326 us |  1,874.1056 us |  4.06 |    0.06 |           - |           - |           - |            93.75 KB |
|                              |        |        |                |                |                |       |         |             |             |             |                     |
|   **ListICollectionConstructor** | **100000** | **String** |   **363,062.5 us** |  **7,155.5040 us** | **16,151.1650 us** |  **1.00** |    **0.00** |  **14000.0000** |  **14000.0000** |  **14000.0000** |        **781398.77 KB** |
| PooledICollectionConstructor | 100000 | String |    80,789.5 us |    115.4829 us |    102.3725 us |  0.23 |    0.02 |           - |           - |           - |            54.69 KB |
|   ListIEnumerableConstructor | 100000 | String | 1,872,127.1 us | 10,278.5586 us |  8,583.0620 us |  5.31 |    0.39 | 373000.0000 | 333000.0000 | 331000.0000 |       2049111.42 KB |
| PooledIEnumerableConstructor | 100000 | String | 1,332,167.8 us |  3,851.4894 us |  3,602.6855 us |  3.76 |    0.26 |           - |           - |           - |           101.56 KB |