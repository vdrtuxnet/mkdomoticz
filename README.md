# mkdomoticz
Make a persistent domoticz container PDQ

### Requirements

docker

## Contributing

Feel free to make an issue or pull request [here](https://github.com/joshuacox/mkdomoticz)

### Usage

`make run`

should ask you any pertinent questions and bring up a container running domoticz

### DockerHub Usage

```
docker pull joshuacox/mkdomoticz
````

```
 @docker run --name=domoticz \
        --privileged \
        --cidfile="cid" \
        -d \
        -p 8080:8080 \
        -v $(DATADIR)/config:/config \
        -t joshuacox/mkdomoticz
```

### Persistence

First run an instance like above and `grab` it's data dirctory:

```
        mkdir -p datadir/domoticz
        docker cp `cat cid`:/config  - |sudo tar -C datadir/ -pxf -
```

```
 @docker run --name=domoticz \
        --privileged \
        -d \
        -p 8080:8080 \
        -v `pwd`/datadir/config:/config \
        -t joshuacox/mkdomoticz
```

### Branches

there are branches for raspberryPi as well, checkout the `arm` branch to pull my image from docker hub, or use the `local-stretch` to build 
locally though it should be noted you'lll need a locally built stretch image named `local-stretch`, I have another [Makefile 
=======
locally though it should be noted you'll need a locally built stretch image named `local-stretch`, I have another [Makefile 
>>>>>>> master
repo](https://github.com/joshuacox/local-debian) for that as  well.  Merely `make stretch` and a local stretch image can be built using 
debootstrap (which is available in most distribution [even ones not based on debian])
