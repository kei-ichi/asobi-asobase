# Benchmark Test result

EC2:

[https://calculator.aws/#/estimate?id=8e292c4a3ce2e6609aed0f8e6713ff72c897214a](https://calculator.aws/#/estimate?id=6fd464a9c533b3ab01b0161b9896cd6117b4c5e9)

Fargate:
[https://calculator.aws/#/estimate?id=fa371109221030e27e55ba855b2078f9d13e4e07](https://calculator.aws/#/estimate?id=73f72c503b1acf2f17bca2d1cf687949648e5988)

```sh
ab -n 100 -c 5 -t 300 [Target_URL]
```

## Test 1

EC2:

```
❯ ab -n 100 -c 5 -t 300 http://54.65.47.148/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 54.65.47.148 (be patient)
Completed 5000 requests
Completed 10000 requests
Finished 10515 requests


Server Software:        nginx/1.24.0
Server Hostname:        54.65.47.148
Server Port:            80

Document Path:          /
Document Length:        49888 bytes

Concurrency Level:      5
Time taken for tests:   300.116 seconds
Complete requests:      10515
Failed requests:        0
Total transferred:      526983360 bytes
HTML transferred:       524627104 bytes
Requests per second:    35.04 [#/sec] (mean)
Time per request:       142.708 [ms] (mean)
Time per request:       28.542 [ms] (mean, across all concurrent requests)
Transfer rate:          1714.78 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   23 125.8      7    1012
Processing:    45  119  41.6    126    1174
Waiting:       33  106  41.5    112    1162
Total:         51  142 127.9    133    1199

Percentage of the requests served within a certain time (ms)
  50%    133
  66%    138
  75%    140
  80%    141
  90%    144
  95%    148
  98%    168
  99%   1083
 100%   1199 (longest request)
```

Fargate:

```
❯ ab -n 100 -c 5 -t 300 http://18.183.139.242/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 18.183.139.242 (be patient)
Completed 5000 requests
Finished 7992 requests


Server Software:        Apache/2.4.65
Server Hostname:        18.183.139.242
Server Port:            80

Document Path:          /
Document Length:        49892 bytes

Concurrency Level:      5
Time taken for tests:   300.049 seconds
Complete requests:      7992
Failed requests:        0
Total transferred:      400956596 bytes
HTML transferred:       398750528 bytes
Requests per second:    26.64 [#/sec] (mean)
Time per request:       187.719 [ms] (mean)
Time per request:       37.544 [ms] (mean, across all concurrent requests)
Transfer rate:          1304.98 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   27 138.8      7    1012
Processing:    54  160  61.9    175    1208
Waiting:       42  145  61.9    161    1196
Total:         61  187 142.8    184    1249

Percentage of the requests served within a certain time (ms)
  50%    184
  66%    195
  75%    200
  80%    204
  90%    213
  95%    226
  98%   1063
  99%   1086
 100%   1249 (longest request)
```

```
METRIC                    EC2 c8g.medium    Fargate Task    Performance Gap
Requests/second:          35.04             26.64           -24.0%
Response time (mean):     142.7ms           187.7ms         +31.5% slower
Processing time:          119ms             160ms           +34.5% slower
Total requests (5min):    10,515            7,992           -24.0%
Transfer rate:            1,714 KB/s        1,305 KB/s      -23.9%

```

## Test 2

EC2:

```
❯ ab -n 100 -c 5 -t 300 http://54.65.47.148/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 54.65.47.148 (be patient)
Completed 5000 requests
Completed 10000 requests
Finished 10513 requests


Server Software:        nginx/1.24.0
Server Hostname:        54.65.47.148
Server Port:            80

Document Path:          /
Document Length:        49888 bytes

Concurrency Level:      5
Time taken for tests:   300.006 seconds
Complete requests:      10513
Failed requests:        0
Total transferred:      526827456 bytes
HTML transferred:       524472544 bytes
Requests per second:    35.04 [#/sec] (mean)
Time per request:       142.683 [ms] (mean)
Time per request:       28.537 [ms] (mean, across all concurrent requests)
Transfer rate:          1714.90 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   25 133.6      7    1012
Processing:    45  117  37.0    124    1140
Waiting:       33  104  37.0    110    1126
Total:         51  142 134.1    131    1171

Percentage of the requests served within a certain time (ms)
  50%    131
  66%    136
  75%    139
  80%    140
  90%    144
  95%    147
  98%    173
  99%   1086
 100%   1171 (longest request)
```

Fargate:

```
❯ ab -n 100 -c 5 -t 300 http://18.183.139.242/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 18.183.139.242 (be patient)
Completed 5000 requests
Finished 7986 requests


Server Software:        Apache/2.4.65
Server Hostname:        18.183.139.242
Server Port:            80

Document Path:          /
Document Length:        49892 bytes

Concurrency Level:      5
Time taken for tests:   300.058 seconds
Complete requests:      7986
Failed requests:        0
Total transferred:      400641648 bytes
HTML transferred:       398437512 bytes
Requests per second:    26.61 [#/sec] (mean)
Time per request:       187.865 [ms] (mean)
Time per request:       37.573 [ms] (mean, across all concurrent requests)
Transfer rate:          1303.92 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   28 142.3      7    1013
Processing:    54  159  60.2    176    1206
Waiting:       42  145  60.1    161    1193
Total:         60  187 144.9    184    1268

Percentage of the requests served within a certain time (ms)
  50%    184
  66%    195
  75%    201
  80%    204
  90%    212
  95%    225
  98%   1063
  99%   1087
 100%   1268 (longest request)
```

```
METRIC                    Test 1          Test 2          Variance
EC2 Requests/sec:         35.04           35.04           0.00%
EC2 Response time:        142.7ms         142.7ms         0.00%
EC2 Total requests:       10,515          10,513          -0.02%

Fargate Requests/sec:     26.64           26.61           -0.11%
Fargate Response time:    187.7ms         187.9ms         +0.11%
Fargate Total requests:   7,992           7,986           -0.08%
```

## Test 3

EC2:

```
❯ ab -n 100 -c 5 -t 300 http://54.65.47.148/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 54.65.47.148 (be patient)
Completed 5000 requests
Completed 10000 requests
Finished 10506 requests


Server Software:        nginx/1.24.0
Server Hostname:        54.65.47.148
Server Port:            80

Document Path:          /
Document Length:        49888 bytes

Concurrency Level:      5
Time taken for tests:   300.021 seconds
Complete requests:      10506
Failed requests:        0
Total transferred:      526476672 bytes
HTML transferred:       524123328 bytes
Requests per second:    35.02 [#/sec] (mean)
Time per request:       142.785 [ms] (mean)
Time per request:       28.557 [ms] (mean, across all concurrent requests)
Transfer rate:          1713.67 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   24 127.3      7    1014
Processing:    45  119  38.8    126    1152
Waiting:       33  105  38.7    113    1136
Total:         51  142 127.9    134    1166

Percentage of the requests served within a certain time (ms)
  50%    134
  66%    139
  75%    141
  80%    142
  90%    145
  95%    148
  98%    162
  99%   1075
 100%   1166 (longest request)
```

Fargate:

```
❯ ab -n 100 -c 5 -t 300 http://18.183.139.242/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 18.183.139.242 (be patient)
Completed 5000 requests
Finished 7983 requests


Server Software:        Apache/2.4.65
Server Hostname:        18.183.139.242
Server Port:            80

Document Path:          /
Document Length:        49892 bytes

Concurrency Level:      5
Time taken for tests:   300.003 seconds
Complete requests:      7983
Failed requests:        0
Total transferred:      400491144 bytes
HTML transferred:       398287836 bytes
Requests per second:    26.61 [#/sec] (mean)
Time per request:       187.901 [ms] (mean)
Time per request:       37.580 [ms] (mean, across all concurrent requests)
Transfer rate:          1303.67 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   28 142.3      7    1011
Processing:    54  159  59.8    175    1193
Waiting:       41  144  59.8    160    1181
Total:         60  187 144.3    183    1219

Percentage of the requests served within a certain time (ms)
  50%    183
  66%    195
  75%    200
  80%    204
  90%    213
  95%    226
  98%   1064
  99%   1082
 100%   1219 (longest request)
```

```
METRIC                    Test 1    Test 2    Test 3    Std Dev
EC2 Requests/sec:         35.04     35.04     35.02     0.012
EC2 Response time (ms):   142.7     142.7     142.8     0.058
EC2 Total requests:       10,515    10,513    10,506    4.58

Fargate Requests/sec:     26.64     26.61     26.61     0.017
Fargate Response time:    187.7     187.9     187.9     0.115
Fargate Total requests:   7,992     7,986     7,983     4.51
```

## Test 4

EC2:

```
❯ ab -n 100 -c 5 -t 300 http://54.65.47.148/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 54.65.47.148 (be patient)
Completed 5000 requests
Completed 10000 requests
Finished 10527 requests


Server Software:        nginx/1.24.0
Server Hostname:        54.65.47.148
Server Port:            80

Document Path:          /
Document Length:        49888 bytes

Concurrency Level:      5
Time taken for tests:   300.116 seconds
Complete requests:      10527
Failed requests:        0
Total transferred:      527697344 bytes
HTML transferred:       525338400 bytes
Requests per second:    35.08 [#/sec] (mean)
Time per request:       142.546 [ms] (mean)
Time per request:       28.509 [ms] (mean, across all concurrent requests)
Transfer rate:          1717.10 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   23 126.4      7    1011
Processing:    45  119  40.3    126    1153
Waiting:       33  105  40.2    113    1140
Total:         51  142 128.4    134    2122

Percentage of the requests served within a certain time (ms)
  50%    134
  66%    139
  75%    141
  80%    142
  90%    145
  95%    148
  98%    164
  99%   1078
 100%   2122 (longest request)
```

Fargate:

```
❯ ab -n 100 -c 5 -t 300 http://18.183.139.242/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 18.183.139.242 (be patient)
Completed 5000 requests
Finished 7990 requests


Server Software:        Apache/2.4.65
Server Hostname:        18.183.139.242
Server Port:            80

Document Path:          /
Document Length:        49892 bytes

Concurrency Level:      5
Time taken for tests:   300.036 seconds
Complete requests:      7990
Failed requests:        0
Total transferred:      400842320 bytes
HTML transferred:       398637080 bytes
Requests per second:    26.63 [#/sec] (mean)
Time per request:       187.757 [ms] (mean)
Time per request:       37.551 [ms] (mean, across all concurrent requests)
Transfer rate:          1304.67 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   28 144.4      7    1015
Processing:    54  159  57.9    175    1238
Waiting:       42  144  57.8    161    1198
Total:         60  187 145.4    184    1244

Percentage of the requests served within a certain time (ms)
  50%    184
  66%    195
  75%    200
  80%    203
  90%    212
  95%    223
  98%   1064
  99%   1084
 100%   1244 (longest request)
```

```
METRIC                    Test 1    Test 2    Test 3    Test 4    Mean    Std Dev
EC2 Requests/sec:         35.04     35.04     35.02     35.08     35.05   0.026
EC2 Response time (ms):   142.7     142.7     142.8     142.5     142.7   0.122
EC2 Total requests:       10,515    10,513    10,506    10,527    10,515  8.54

Fargate Requests/sec:     26.64     26.61     26.61     26.63     26.62   0.014
Fargate Response time:    187.7     187.9     187.9     187.8     187.8   0.100
Fargate Total requests:   7,992     7,986     7,983     7,990     7,988   3.92
```

## Test 5

EC2:

```
❯ ab -n 100 -c 5 -t 300 http://54.65.47.148/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 54.65.47.148 (be patient)
Completed 5000 requests
Completed 10000 requests
Finished 10520 requests


Server Software:        nginx/1.24.0
Server Hostname:        54.65.47.148
Server Port:            80

Document Path:          /
Document Length:        49888 bytes

Concurrency Level:      5
Time taken for tests:   300.017 seconds
Complete requests:      10520
Failed requests:        0
Total transferred:      527192160 bytes
HTML transferred:       524835456 bytes
Requests per second:    35.06 [#/sec] (mean)
Time per request:       142.594 [ms] (mean)
Time per request:       28.519 [ms] (mean, across all concurrent requests)
Transfer rate:          1716.02 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   24 130.8      7    1011
Processing:    45  118  39.8    125    1165
Waiting:       33  104  39.8    111    1151
Total:         51  142 131.9    132    1173

Percentage of the requests served within a certain time (ms)
  50%    132
  66%    137
  75%    139
  80%    140
  90%    143
  95%    147
  98%    173
  99%   1082
 100%   1173 (longest request)
```

Fargate:

```
❯ ab -n 100 -c 5 -t 300 http://18.183.139.242/
This is ApacheBench, Version 2.3 <$Revision: 1913912 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 18.183.139.242 (be patient)
Completed 5000 requests
Finished 7957 requests


Server Software:        Apache/2.4.65
Server Hostname:        18.183.139.242
Server Port:            80

Document Path:          /
Document Length:        49892 bytes

Concurrency Level:      5
Time taken for tests:   300.016 seconds
Complete requests:      7957
Failed requests:        0
Total transferred:      399200716 bytes
HTML transferred:       397004308 bytes
Requests per second:    26.52 [#/sec] (mean)
Time per request:       188.523 [ms] (mean)
Time per request:       37.705 [ms] (mean, across all concurrent requests)
Transfer rate:          1299.41 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        6   28 141.7      7    1011
Processing:    54  160  58.6    176    1198
Waiting:       42  146  58.6    162    1186
Total:         60  188 143.3    185    1219

Percentage of the requests served within a certain time (ms)
  50%    185
  66%    195
  75%    201
  80%    204
  90%    213
  95%    224
  98%   1064
  99%   1083
 100%   1219 (longest request)
```

```
METRIC                    Test 1    Test 2    Test 3    Test 4    Test 5    Mean    Std Dev
EC2 Requests/sec:         35.04     35.04     35.02     35.08     35.06     35.05   0.023
EC2 Response time (ms):   142.7     142.7     142.8     142.5     142.6     142.7   0.111
EC2 Total requests:       10,515    10,513    10,506    10,527    10,520    10,516  7.68

Fargate Requests/sec:     26.64     26.61     26.61     26.63     26.52     26.60   0.047
Fargate Response time:    187.7     187.9     187.9     187.8     188.5     188.0   0.334
Fargate Total requests:   7,992     7,986     7,983     7,990     7,957     7,982   14.5
```
