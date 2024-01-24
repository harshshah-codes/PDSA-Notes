# Timing our code

Sometimes, we need to know how much time does our code takes to execute.

We can do that so in many ways, one of them being to use the `perf_counter()` function.

The `perf_counter()` function gives us the current timestamp. It alone is not as useful but if we call the function at the start and the end of program and subtract both the timestamps we get the execution time of the code. 

### Using `perf_counter()`

We will create a class `Timer` to use this `perf_counter()` as this will help us to use this more and more.

```py linenums="1" title="Timer.py"
import time
class Timer:
    def __init__(self):
        self._start_time = None
        self._elapsed_time = None

    def start(self):
        if self._start_time is not None:
            raise Exception("Timer is already running")
        self._start_time = time.perf_counter()

    def stop(self):
        if self._start_time is None:
            raise Exception("Timer is not running")
        end_time = time.perf_counter()
        self._elapsed_time = end_time - self._start_time()
        self._start_time = None

    def __str__(self):
        print(str(self._elapsed_time))
```

