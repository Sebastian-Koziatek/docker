W katalogu `my-maven-docker-project` znajduje się gotowa aplikacja w javie wyświetlająca prosty `Hello World`. Zbudujemy w oparciu o nią nasz kontener dockera.

1. W katalogu `my-maven-docker-project` stwórz dockerfile z ustwaieniami:

- Ma zostać zbudowany z obrazu openjdk:8
- Dodaj z folderu `target`  plik `my-maven-docker-project.jar`
- W `ENTRYPOINT` ustaw polecenie `java - jar my-maven-docker-project.jar`
- Wystaw port 8080

2. W repozytorium dockerhub (https://hub.docker.com/) stwórz nowe repozytorium, nazwij je np maven.

3. Zbuduj obraz aplikacji z dockerfile
   
```
docker build -t <nazwa_uzytkownika>/maven .
```

4. Prześlij zbudowany obraz do repozytorium dockerhub

```
docker push <nazwa_uzytkownika>/maven
```

5. Pobierz swój obraz ze swojego repozytorium na dockerhub
6. Uruchom go z użyciem portu 8080

```
docker run -d -p 8080:8080 <nazwa_uzytkownika>/maven
```

> sprawdź czy działa - http://localhost:8080/


https://hub.docker.com/_/maven