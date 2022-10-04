# Nauczymy się budować obrazy! 

>### Zacznij od zapoznania się z plikiem `Dockerfile`, zwróć uwage jakie parametry są tam zdeklarowane.
<br>
1. W folderze znajduje się przygotowany plik Dockerfile. Stwórz teraz obraz z tego pliku o nazwie "my-hello-world". </br>
   
>Pamiętaj o wskazaniu lokalizacji z której zbudujesz obraz, w tym przypadku to folder w którym jesteś.</i>
<br></i> 
```sh
docker image build -t my-hello-world .
```
</br>

### 2. Sprawdź czy twój obraz jest dostępny w zasobach dockera

```sh
docker image ls 
```
<br>

### 3. Odszukaj swój obraz przy użyciu labela zadeklarowanego w pliku Dockerfile

```sh
docker image ls -f label=imagetype=szkolenie
```
</br>

____

## Część II
1. Skasuj istniejący obraz z tagiem `my-hello-world`
```
docker image ls
docker image rm my-hello-world
```
2. Z obrazu `Dockerfile2` zbuduj ponownie obraz z tagiem `my-hello-world`. Aby wskazać plik `Dockerfile2` należy podac flagę -f oraz nazwzę pliku.
```
docker image build -t my-hello-world -f Dockerfile2 .
```
3. Uruchom kontener i ustaw swoje imie jako argument
```
docker run my-hello-world Jan
```
4. Przejrzyj logi kontenera przy użyciu jego ID.
```  
docker container logs <id>
```` 
5. Skaskuj stworzone kontenery. 
```
docker ps -a
docker rm <id>
```