# Uruchom swój pierwszy kontener!

### Podstawowe polecenia, wykonaj je zastanawiając się co one robią i znacza. 

1. Zacznij od ściągnięcia przykładowego `obrazu`:

```sh
docker image pull hello-world
```

2. Sprwadź czy `obraz` znajduje się w twoich zasobach, wylistujemy posiadane obrazy:

```
docker image ls
```

3. A teraz uruchom `konterner` z pobranego `obraz`

```sh
docker container run hello-world
```


4. Sprawdź czy ten `kontener` jest aktualnie uruchomiony?

```sh
docker container list
```
5. Skoro go nie ma to moze sprawdzimy czy jest wyłączony?

```sh
docker container list -a
```

6. Teraz trochę namieszamy, uruchom `kontener` z poniszymi parametrami:
```sh
docker container run --name <myname> --label=type=szkolenie hello-world
```
>Zastanów się jakie `parametry` dla `kontenera` zostały tutaj ustawione?

7. Listowanie `kontenerów`

```sh
docker container ls
docker container ls -a
docker container ls -a -f status=exited
docker container ls -a -f label=type=szkolenie
```

8. Zobacz logi `kontenera`

```sh
docker container logs <myname|id>
``` 

9. Skasuj `kontener`

```sh
docker container rm <myname>
```