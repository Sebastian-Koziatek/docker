## EXPOSE

1. W folderze nginx stwórz plik dockerfile w którym zadeklarujesz wystawienie aplikacji na porcie 80 - `EXPOSE 80` 
2. Zbuduj obraz i uruchom kontener
3. Sprwadź czy kontener faktycznie posiada zadeklarowany ustawiony na 80
4. Sprawdź za pomocą polecenia curl (curl.exe) (na hoscie) czy jesteś w stanie się połączyć z tym konterem.
5. Uruchom kontener i zbuduj komuniakcje miedzy kontenerem a hostem.


>Rozwiązanie:
```sh
docker build -t my-nginx .
dd
docker container run --name my-nginx -p 8080:80 -d my-nginx
curl localhost:8080
```
## Workdir

>Parametr WORKDIR deklaruje nam domyślny katalog w którym kontener uruchomi się. W ramach wykonywania poleceń zawrtych w dockerfile jest możliwe kilkukrotne ustawienie WORKDIR np. 

```
FROM ubuntu:16.04
WORKDIR /project
RUN npm install 
WORKDIR ../project2
RUN touch file1.cpp
```

## USER

Instrukcja USER ustawi nasza nazwę użytkownika w kontenerze (lub UID) i opcjonalną grupę użytkowników (lub GID), które mają być używane jak domyślny użytkownik/grupa w danym etapie. Użytkownik używany jest w ramach instrukcji RUN i uruchamia odpowiednie polecenia ENTRYPOINT i CMD w czasie wykonywania

```
FROM ubuntu:latest
RUN groupadd -r grupaszkolenie && szkolenie -r -g grupaszkolenie szkolenie
CMD ["/greetings.sh"]
USER user
```
>Sprawdźmy czy stworzyn nam to grupe `user` i użytkownika `user`.

```
docker build -t uzytkownik .
docker run -it uzytkownik bash 
id
```