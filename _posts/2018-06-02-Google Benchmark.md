# Google Benchmark

### Basic Steps
1. 
```c++
#include <benchmark/benchmark.h>
static void BM_uint2str(benchmark::State& state) {
    unsigned int num = 1234;
    while (state.KeepRunning())
        (void) uint2str(num);
}
// Register the function as a benchmark
BENCHMARK(BM_uint2str);

BENCHMARK_MAIN();
```
2. 
```c++
static void BM_vuint2vstr(benchmark::State& state) {
    vector<unsigned int> vuint;
    for (std::size_t i = 0; i < state.range_x(); ++i) {
        vuint.push_back(i);
    }
    
    vector<string> vstr;
    while (state.KeepRunning())
        vuint2vstr(vuint, vstr);
}
// Register the function as a benchmark
BENCHMARK(BM_vuint2vstr)->Range(8, 8 << 10);

BENCHMARK_MAIN();
```


```
Refs:
http://airekans.github.io/cpp/2015/04/18/google-benchmark
```
