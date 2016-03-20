### Finding thrid party container
1.  ```docker search redis``` search the images against the public index
2.  ```docker pull redis``` pulling the docker image from docker hub
3.  Run the images ``` docker run --name done-redis -d redis```
4.  verify your images status ``` docker log done-redis```
5.  ```docker run --rm -i -t --entrypoint="bash" --link don-redis:redis redis -C `redis-cli -h $REDIS_PORT_6379_TCP_ADDR```

