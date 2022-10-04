## Izolacja kontnerów w praktyce

1. Sprawdź czy kontenery są od siebie izolowane. Uruchom dwa terminale i kazżdym z nich uruchom polecenie 

```   
docker run -it busybox sh
```

2. Na pierwszym `terminalu/kontenerze` stwórz plik szkolenie - `touch szkolenie`.
3. Sprawdź na drugim `temrinalu/konterze` czy plik istnieje - `ls`

### Izolacja kontnerów - izlacja sieci w `docker-compose.yml`


```yml
version: "3"
services:
  ubuntu:
    build:
      dockerfile: dockerfile
    container_name: ubuntunet1
    image: ubuntu
    restart: on-failure
    command: ["sleep","infinity"]
    networks:
      - net1
  ubuntu2:
    build:
      dockerfile: dockerfile
    container_name: ubuntunet2
    image: ubuntu
    restart: on-failure
    command: ["sleep","infinity"]
    networks:
      - net2

networks:
    net1:
      driver: bridge
    net2:
      driver: bridge
```
