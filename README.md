# Thread Pool

**A simple thread pool implementation, based on c++20**.

## How to use

Just `#include "ThreadPool.hpp"`.

```cpp
auto main() -> int {
  auto pool = karus::ThreadPool(1);

  for (int i = 0; i < 5; i++) {
    pool.AddTask([i] {
      std::osyncstream(std::cout)
          << "Task: " << i << " Thread id: " << std::this_thread::get_id()
          << std::endl;
      using namespace std::chrono_literals;
      std::this_thread::sleep_for(200ms);
    });
  }

  using namespace std::chrono_literals;
  std::this_thread::sleep_for(2000ms);
  std::osyncstream(std::cout)
      << "====================================================" << std::endl;

  pool.Stop(true);
}
```
