# docker-dynamic-redis
Docker image for the [Dynamic Redis](https://matt.sh/dynamic-redis) server.  Uses a Dockerfile based on the official Redis Docker image.  See the [Redis Docker documentation](https://github.com/docker-library/docs/tree/master/redis) for examples of how to run the Docker image with custom configuration and storage options.  Please file an issue here if you discover incompatibilities.

# Running
## Example: Default Configuration
Uses the default redis configuration that's supplied with the Dynamic Redis project.

```shell
$ sudo docker run dynamic-redis:latest
1:C 23 Apr 04:24:20.564 * Module [<builtin>] loaded 163 commands.
1:C 23 Apr 04:24:20.568 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
                _._
           _.-``__ ''-._
      _.-``    `.  `_.  ''-._           Redis 2.9.999 (e6d3efc8/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._
 (    '      ,       .-`  | `,    )     Running in standalone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 1
  `-._    `-._  `-./  _.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |           http://redis.io
  `-._    `-._`-.__.-'_.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |
  `-._    `-._`-.__.-'_.-'    _.-'
      `-._    `-.__.-'    _.-'
          `-._        _.-'
              `-.__.-'

1:M 23 Apr 04:24:20.578 # Server started, Redis version 2.9.999
1:M 23 Apr 04:24:20.579 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 23 Apr 04:24:20.582 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 23 Apr 04:24:20.584 * The server is now ready to accept connections on port 6379
```

## Example: Custom Configuration
Uses the sample redis configuration that's checked into the ```docker-dynamic-redis``` project repository, which will load the ```geo.so``` module:

```shell
$ sudo docker run -v `pwd`/redis.conf:/usr/local/etc/redis/redis.conf dynamic-redis:latest redis-server /usr/local/etc/redis/redis.conf1:C 23 Apr 04:29:58.980 * Module [<builtin>] loaded 163 commands.
1:C 23 Apr 04:29:58.990 * Loading new [geo.so] module.
1:C 23 Apr 04:29:58.990 * Added command geoadd [geo.so]
1:C 23 Apr 04:29:58.991 * Added command georadius [geo.so]
1:C 23 Apr 04:29:58.992 * Added command georadiusbymember [geo.so]
1:C 23 Apr 04:29:58.993 * Added command geoencode [geo.so]
1:C 23 Apr 04:29:58.994 * Added command geodecode [geo.so]
1:C 23 Apr 04:29:58.994 * Module [geo.so] loaded 5 commands.
1:C 23 Apr 04:29:58.996 * Running load function of module [geo.so].
                _._
           _.-``__ ''-._
      _.-``    `.  `_.  ''-._           Redis 2.9.999 (e6d3efc8/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._
 (    '      ,       .-`  | `,    )     Running in standalone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 1
  `-._    `-._  `-./  _.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |           http://redis.io
  `-._    `-._`-.__.-'_.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |
  `-._    `-._`-.__.-'_.-'    _.-'
      `-._    `-.__.-'    _.-'
          `-._        _.-'
              `-.__.-'

1:M 23 Apr 04:29:59.005 # Server started, Redis version 2.9.999
1:M 23 Apr 04:29:59.006 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 23 Apr 04:29:59.007 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 23 Apr 04:29:59.008 * The server is now ready to accept connections on port 6379
```
