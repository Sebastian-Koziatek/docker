## EXPOSE

1. W pliku dockerfile zadeklaruj wystawienie aplikacji na porcie 80 - `EXPOSE 80` 
2. Zbuduj obraz i uruchom kontener
3. Sprwadź czy kontener faktycznie posiada zadeklarowany ustawiony na 80
4. Sprawdź za pomocą polecenia curl (curl.exe) czy jesteś w stanie się połączyć.
> Dlaczego nie jesteś? Wspominaliśmy o tym w lekcji na temat izolacji kontenerów. W tej chwili kontener wystawiony jestn a porcie 80 ale nie mamy zbudowanej komunikacji z nim - jest odizolowany. 
5. Uruchom kontener i zbuduj komuniakcje miedzy kontenerem a hostem.


>Rozwiązanie:
```sh
docker build -t my-nginx .
docker run -d my-nginx
docker container run --name my-nginx -p 8080:80 -d my-nginx
curl localhost:8080
```
## ENV

> Environment Variables - zmienne środowiskowe - ENV

1. Stwórzmy sobie w katalogu prosty skrypt bashowy o nazwie greetings.sh
```bash
#!/bin/sh

echo Hello $env_name
```
2. Stwórzmy sobie dockerfile
```
FROM alpine:latest
COPY greetings.sh .
RUN chmod +x /greetings.sh
CMD ["/greetings.sh"]
```
Zbudujmy obraz i uruchommy go
```
docker build -t greetings .
docker run greetings
```
3. Teraz stwórzmy dockerfile2 i przekażmy w nim zmienną środowiskową o wartości `env name Sebastian`
```
FROM alpine:latest
ENV env_name Sebastian
COPY greetings.sh .
RUN chmod +x /greetings.sh
CMD ["/greetings.sh"]
```
```
docker build -t greetings .
docker run greetings:2
```

4. Mozna zmienne średowiskowe przypisać też poprzez parametr ARG w dockerfile a następnie dynamiczniego zmieniać podczas budowy obrazu z pliku przy użyciu flagi `--build-arg`. Zbudujmy nowy plik dockerfile3 
   
```
FROM alpine:latest
#Ustaw domyślna wartośc parametru ARG
ARG WELCOME_USER=Sebastian
RUN echo "Welcome $WELCOME_USER, to Docker World!" > message.txt
CMD cat message.txt
```

```
build -t greetings:3 --build-arg WELCOME_USER=Michal -f dockerfile3 . 
docker run greetings:5
```
> Cokolwiek zostanie zdefiniowane po fladze `--build-arg` zostanie zastąpione zmienną `ARG` zdefiniowaną w dockerfile 


## Workdir

>Parametr WORKDIR deklaruje nam domyślny katalog w których kontener uruchomi się. W ramach wykonywania poleceń zawrtych w dockerfile jest możliwe kilkukrotne ustawienie WORKDIR np. 

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