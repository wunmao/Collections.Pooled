``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.292 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
  [Host] : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0
  Clr    : .NET Framework 4.7.2 (CLR 4.0.30319.42000), 64bit RyuJIT-v4.7.3324.0

Job=Clr  Runtime=Clr  

```
|     Method |      N |   Type |         Mean |      Error |    StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|----------- |------- |------- |-------------:|-----------:|----------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|  **StackPush** |   **1000** |    **Int** |     **3.586 us** |  **0.0313 us** | **0.0292 us** |  **1.00** |    **0.00** |      **2.6779** |           **-** |           **-** |              **8433 B** |
| PooledPush |   1000 |    Int |     4.535 us |  0.0454 us | 0.0424 us |  1.26 |    0.01 |      0.0153 |           - |           - |                56 B |
|            |        |        |              |            |           |       |         |             |             |             |                     |
|  **StackPush** |   **1000** | **String** |     **5.593 us** |  **0.0794 us** | **0.0742 us** |  **1.00** |    **0.00** |      **5.2643** |           **-** |           **-** |             **16616 B** |
| PooledPush |   1000 | String |     9.503 us |  0.0868 us | 0.0812 us |  1.70 |    0.03 |      0.0153 |           - |           - |                56 B |
|            |        |        |              |            |           |       |         |             |             |             |                     |
|  **StackPush** |  **10000** |    **Int** |    **36.079 us** |  **0.3773 us** | **0.3344 us** |  **1.00** |    **0.00** |     **41.6260** |           **-** |           **-** |            **131435 B** |
| PooledPush |  10000 |    Int |    48.433 us |  0.4080 us | 0.3816 us |  1.34 |    0.02 |           - |           - |           - |                56 B |
|            |        |        |              |            |           |       |         |             |             |             |                     |
|  **StackPush** |  **10000** | **String** |   **115.250 us** |  **0.9894 us** | **0.9255 us** |  **1.00** |    **0.00** |     **41.6260** |     **41.6260** |     **41.6260** |            **262531 B** |
| PooledPush |  10000 | String |   113.740 us |  0.8283 us | 0.7748 us |  0.99 |    0.01 |           - |           - |           - |                57 B |
|            |        |        |              |            |           |       |         |             |             |             |                     |
|  **StackPush** | **100000** |    **Int** |   **476.122 us** |  **8.0293 us** | **7.1178 us** |  **1.00** |    **0.00** |    **168.9453** |    **126.9531** |    **126.4648** |           **1051659 B** |
| PooledPush | 100000 |    Int |   419.259 us |  3.2172 us | 3.0094 us |  0.88 |    0.01 |           - |           - |           - |                60 B |
|            |        |        |              |            |           |       |         |             |             |             |                     |
|  **StackPush** | **100000** | **String** |   **944.247 us** |  **5.9197 us** | **5.5373 us** |  **1.00** |    **0.00** |    **196.2891** |    **158.2031** |    **152.3438** |           **2101128 B** |
| PooledPush | 100000 | String | 1,035.169 us | 10.4311 us | 9.2469 us |  1.10 |    0.01 |           - |           - |           - |                64 B |