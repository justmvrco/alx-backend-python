# 0x02. Python - Async Comprehension

## Resources
Read or watch:

* [PEP 530 – Asynchronous Comprehensions](https://www.python.org/dev/peps/pep-0530/)
* [What’s New in Python: Asynchronous Comprehensions / Generators](https://www.blog.pythonlibrary.org/2017/02/14/whats-new-in-python-asynchronous-comprehensions-generators/)
* [Type-hints for generators](https://stackoverflow.com/questions/42531143/type-hinting-generator-in-python-3-6)
* [Parallel asynchronous IO in Python's coroutines](https://stackoverflow.com/questions/47169474/parallel-asynchronous-io-in-pythons-coroutines)
* [Coroutines and Tasks](https://docs.python.org/3/library/asyncio-task.html)
* [Running coroutines in Python with Asyncio](https://medium.com/cassandra-cryptoassets/running-coroutines-in-python-with-asyncio-ca8e141137e2)
* [Parallel execution of asyncio functions](https://hinty.io/ivictbor/parallel-execution-of-asyncio-functions/)

## General
* All your functions and coroutines must be `type-annotated`.
* All your modules and function should have a `documentation`
* Your code should use the `pycodestyle` style

## Tasks

## [0. Async Generator](./0-async_generator.py)
Write a coroutine called `async_generator` that takes no arguments.

The coroutine will loop 10 times, each time asynchronously wait 1 second, then yield a random number between 0 and 10. Use the `random` module.
```
$ ./0-main.py
[4.403136952967102, 6.9092712604587465, 6.293445466782645, 4.549663490048418, 4.1326571686139015, 9.99058525304903, 6.726734105473811, 9.84331704602206, 1.0067279479988345, 1.3783306401737838]
```

## [1. Async Comprehensions](./1-async_comprehension.py)
Import `async_generator` from the previous task and then write a coroutine called `async_comprehension` that takes no arguments.

The coroutine will collect 10 random numbers using an async comprehensing over `async_generator`, then return the 10 random numbers.
```
$ ./1-main.py
[9.861842105071727, 8.572355293354995, 1.7467182056248265, 4.0724372912858575, 0.5524750922145316, 8.084266576021555, 8.387128918690468, 1.5486451376520916, 7.713335177885325, 7.673533267041574]
```

## [2. Run time for four parallel comprehensions](./2-measure_runtime.py)
Import `async_comprehension` from the previous file and write a `measure_runtime` coroutine that will execute `async_comprehension` four times in parallel using `asyncio.gather`.

`measure_runtime` should measure the total runtime and return it.

Notice that the total runtime is roughly 10 seconds, explain it to yourself.
```
$ ./2-main.py
10.021936893463135
```
