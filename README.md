# Fibonacci Web Framework/Platform Shootout

This repository contains web-apps written in different languages and frameworks that get a number as url parameter and calculate the corresponding fibonacci number.

These implementations are used for benchmarking. The original story can be found here:

https://medium.com/@tschundeee/express-vs-flask-vs-go-acc0879c2122

## The Task
I decided to do a little benchmark of some of my favorite web stacks. So I created a web service that calculates the corresponding fibonacci number to a request parameter.

## The Code
A request to for example http://localhost:3000/10 calculates fib(10) and returns the result (55 in this case) as plain text. I think it’s better to have a little computation per each request because it is more realistic than just serving “Hello World”.



Ref:

http://benchmarksgame.alioth.debian.org/
http://benchmarksgame.alioth.debian.org/u32/performance.php?test=nbody#about


-------------

On my macbook air, the testing result:


Ruby

```
Amy@~/lab/test/wrk> ./wrk -c 64 -d 30s http://localhost:4567/10
Running 30s test @ http://localhost:4567/10
  2 threads and 64 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    32.22ms    9.91ms 188.17ms   84.75%
    Req/Sec     1.01k   136.19     1.34k    74.33%
  59975 requests in 30.05s, 12.13MB read
Requests/sec:   1996.06
Transfer/sec:    413.25KB
```

Node.js

```
Amy@~/lab/test/wrk> ./wrk -c 64 -d 30s http://localhost:3000/10
Running 30s test @ http://localhost:3000/10
  2 threads and 64 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    13.23ms    3.94ms  97.67ms   95.25%
    Req/Sec     2.47k   303.08     2.93k    86.67%
  147381 requests in 30.07s, 29.80MB read
Requests/sec:   4901.56
Transfer/sec:      0.99MB
```

Java

```
Amy@~/lab/test/wrk> ./wrk -c 64 -d 30s http://localhost:4567/10
Running 30s test @ http://localhost:4567/10
  2 threads and 64 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     3.64ms    8.05ms 395.45ms   97.34%
    Req/Sec    11.11k     3.15k   17.24k    80.57%
  661928 requests in 30.06s, 96.58MB read
Requests/sec:  22016.85
Transfer/sec:      3.21MB
```

Go

```
Amy@~/lab/test/wrk> ./wrk -c 64 -d 30s http://localhost:4000/10
Running 30s test @ http://localhost:4000/10
  2 threads and 64 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     2.24ms    8.46ms 353.03ms   99.47%
    Req/Sec    16.17k     2.51k   25.80k    71.17%
  968051 requests in 30.08s, 109.86MB read
Requests/sec:  32179.59
Transfer/sec:      3.65MB
```


