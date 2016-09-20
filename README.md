#Crossbar

This image creates a crossbar image but does not run any process (no entrypoint)

To use this image, simply create a dockerfile that mounts the configuration and starts the crossbar engine.  For example

```
FROM amalhotra/crossbar
COPY ${CONFIG_DIR}/config.json /root/.crossbar
ENTRYPOINT ["crossbar", "start", "--cbdir=/root/.crossbar", "--logdir=/var/log/crossbar", "--logtofile", "--loglevel=info"]
```

And subsequently, this can be called in a docker-compose file with :
```
crossbar:
    build: ./crossbar/
    container_name: crossbar
    environment:
     - CONFIG_DIR=/root/.crossbar/
    ports:
     - "9999:9999"
```


