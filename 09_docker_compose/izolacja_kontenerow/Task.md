## Izolacja kontnerów w praktyce

1. Sprawdź czy kontenery są od siebie izolowane. Uruchom dwa terminale i kazżdym z nich uruchom polecenie 

```   
docker run -it busybox sh
```

2. Na pierwszym `terminalu/kontenerze` stwórz plik szkolenie - `touch szkolenie`.
3. Sprawdź na drugim `temrinalu/konterze` czy plik istnieje - `ls`

### Izolacja kontnerów - izlacja sieci w `docker-compose.yml`
