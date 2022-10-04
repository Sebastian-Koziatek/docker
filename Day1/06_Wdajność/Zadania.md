
>W tym momencie wyczyść sobie dockera, skasuj wszystkie obrazy i kontenery które posiadasz. (możesz zostawić obraz my-nginx, zaraz będziemy go używać)
```sh
docker ps -a
docker stop <container_id>
docker rm <container_id>
docker image ls
docker image rm <image_id>
```

1. Jeżeli nie masz to stwórz ponownie obraz nginx, jeżeli masz to uruchom
```
docker image build -t my-nginx . 
docker run -d my-nginx
```

2. Sprawdzmy teraz kontener od momentu stworzenia jakie pliki zostały zmienione, usunięte lub dodane. Mamy do tego poleceine:
```sh
docker container diff <id>
```

3. Sprawdźmy jakie porty nasz nginx ma zadeklarowane
```
docker container port <id>
```
>jak widzimy brak tutaj żadnych portów, ponieważ żadnych nie zadeklarowaliśmy, zróbmy to.

```
docker stop <id>
docker rm <id>
```
```
docker container run --name my-nginx -p 8080:80 -d my-nginx
curl localhost:8080
```
> I ponownie sprawdźmy porty na kontenerze:</i>
```
docker container port <id>
```
4. Sprawdźmy teraz zużycie zasobów bezpośrednio z kontenera

```
docker stats <id>
```

5. Na koniec jeszcze `top`
```
docker container top <id>
```
___



