# Budowanie swojego registry


1. Zacznijmy od zbudowania kontenera lokalnego registry z publicznego obrazu `registry:2`
```
   docker run -d -p 27015:5000 --restart=always --name registry registry:2
```
1. Pobierzmy na początek jakiś starszy obraz ubuntu:
```
docker pull ubuntu:16.04
```
2. Stwórz dodatkowy tag dla istniejąćego brazu z uwzględnieniem hosta i portu.

```
docker tag ubuntu:16.04 localhost:27015/my-ubuntu
```
>Ta komenda tworzy dodatkowy tag dla istniejącego obrazu. Gdy pierwszą częścią tagu jest nazwa hosta i port, Docker interpretuje to jako lokalizację rejestru podczas wypychania obrazu do repozytorium.</i><br>

3. Posiadając już odpowiednio otagowany obraz zawierający adres i port wypchnijmy obraz do naszego repozyorium
```
docker push localhost:27015/my-ubuntu
```
4. Skasujmy wszystkie lokalne obrazy (otagowany też, ponnieważ już znajduje się w repozytorium)

```
 docker image remove ubuntu:16.04

 docker image remove localhost:27015/my-ubuntu
 ```
5. Pobierzmy teraz wyslany przez nas obraz `localhost:27015/my-ubuntu` z naszego repozytorium

```
docker pull localhost:27015/my-ubuntu
```

## Zabezpieczenie dostępu z użyciem lets encrypt



## Docker hub
1. Stwórz konto dockera na stronie - https://hub.docker.com/signup
2. Zaloguj się w swojej aplikacji docker hub (docker desktop)
3. Wybierz z listy na stronie opcje `Create a Repository`
4. Nazwij ją ` <your-username>/my-private-repo`
5. Ustaw widoczność repozytorium na prywatne
6. Zbuduj docker image ze swojego dockerfile lokalnie (od razu nadamy mu odpowiedni tag)
```
docker build -t <your_username>/my-private-repo .
```
<i>tak jak w przypadku lokalnego repozytorium które zbudowaliśmy gdy pierwszą częścią tagu jest nazwa hosta i port, Docker interpretuje to jako lokalizację rejestru podczas wypychania obrazu do repozytorium.</i>
2. Przetestuj zbudowany obraz uruchamiając go lokalnie
```
docker run -d <your_username>/my-private-repo
```
3. Wyślij obraz do swojego repo i sprawdź je

```
docker push <your_username>/my-private-repo
``` 
4. Pobierz swój obraz z Docker HUB
```
docker pull sebastiankoziatek/docker-szkolenie
```
___
## Zabawa z obrazami i dockerhub registry

Zabawa i możliwości obrazów na podstawie budowania domowej infrastruktury. Użyj dockerhub do wykonania poniższych zadań.
- Pobierz i uruchom `wordpress` na porcie 8080
- Pobierz i uruchom serwer `plex` na porcie 32400
- Pobierz i uruchom serwer `deluge` na porcie 8112