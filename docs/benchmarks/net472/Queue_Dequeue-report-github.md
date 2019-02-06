``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
  [Host] : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0

Job=Clr  Runtime=Clr  InvocationCount=1  
UnrollFactor=1  

```
|        Method |       N |   Type |        Mean |       Error |      StdDev |      Median | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|-------------- |-------- |------- |------------:|------------:|------------:|------------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|  **QueueDequeue** |   **10000** |    **Int** |   **123.46 us** |   **8.7670 us** |  **25.5738 us** |   **114.98 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue |   10000 |    Int |    41.10 us |   5.1230 us |  14.7811 us |    30.37 us |  0.34 |    0.12 |           - |           - |           - |                   - |
|               |         |        |             |             |             |             |       |         |             |             |             |                     |
|  **QueueDequeue** |   **10000** | **String** |   **100.29 us** |   **6.1716 us** |   **5.4710 us** |    **98.17 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue |   10000 | String |    28.64 us |   0.5563 us |   0.6183 us |    28.61 us |  0.29 |    0.02 |           - |           - |           - |                   - |
|               |         |        |             |             |             |             |       |         |             |             |             |                     |
|  **QueueDequeue** |  **100000** |    **Int** | **1,026.72 us** |  **22.7491 us** |  **64.5355 us** | **1,003.30 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue |  100000 |    Int |   279.48 us |   5.2750 us |   4.6761 us |   276.83 us |  0.27 |    0.02 |           - |           - |           - |                   - |
|               |         |        |             |             |             |             |       |         |             |             |             |                     |
|  **QueueDequeue** |  **100000** | **String** | **1,016.48 us** |  **34.0050 us** |  **97.5666 us** |   **981.06 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue |  100000 | String |   281.53 us |   5.5777 us |  13.4708 us |   279.23 us |  0.28 |    0.03 |           - |           - |           - |                   - |
|               |         |        |             |             |             |             |       |         |             |             |             |                     |
|  **QueueDequeue** | **1000000** |    **Int** | **9,659.55 us** | **185.5203 us** | **227.8355 us** | **9,686.60 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue | 1000000 |    Int | 2,797.89 us |  63.2015 us | 181.3370 us | 2,761.03 us |  0.29 |    0.02 |           - |           - |           - |                   - |
|               |         |        |             |             |             |             |       |         |             |             |             |                     |
|  **QueueDequeue** | **1000000** | **String** | **9,528.09 us** | **196.3455 us** | **183.6617 us** | **9,496.87 us** |  **1.00** |    **0.00** |           **-** |           **-** |           **-** |                   **-** |
| PooledDequeue | 1000000 | String | 2,663.91 us |  51.6985 us |  69.0160 us | 2,621.27 us |  0.28 |    0.01 |           - |           - |           - |                   - |