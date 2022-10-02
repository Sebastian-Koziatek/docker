## Najważniejsze narzędzia diagnostyczne kontenerów

1. Wiele programów loguje rzeczy do `stdout`. Wszystko co daje sie zapisać do procesu `stouta` ma wartość `PID 1` w konterze i zostaje przechwycone do lpliku historii na hoscie, gdzie mozną ja wyświetlić za pomocą polecenia logs.
> Żeby dobrze to zobrazować sciągnij sobie obraz jenkinsa i go wystartujemy.

```
docker run -d --name jenkins jenkins/jenkins:lts
```
Teraz mamy dostep do logów kontenera jenkins
```
docker logs jenkins
```
2. Docker stats omawiany był już przy przeglądaniu wydajności kontnera. Jedną z rzeczy do weryfikacji poprawnego dzialania kontenera jest jego zaopatrznie w zasoby. 
```
docker stats <container_id>
```

3. `docker cp` to polecenie które pozwoli kopowiać wybrane pliki lub foldery z kontenera do naszej lokalnej ścieżki. Możemy dzięki temu np pobrać logi albo sprawdzić jakiś folder przy użyciu narzędzie których nie mamy na kontenerze.
   
```
docker cp <container_id>:/path/to/useful/file /local-path
```
skopiujmy z naszego obrazu my-nginix katalog /tmp w ktorym jest nginix
```
docker cp <container_id>:/tmp /tmp/data
```

4. To polecenie już znamy, pozwala nam na zalogowanie się do powloki działającego kontenera. Dzieki temu można przeprowadzić pełną diagnostykę. 
```
docker exec -it <container_id> /bin/bash
```
   
5. Nie możesz w ogóle uruchomić kontenera? eśli masz początkowe polecenie lub punkt wejścia, który natychmiast się zawiesza, Docker natychmiast go wyłączy. Może to uniemożliwić uruchomienie kontenera, więc nie będziesz mógł już więcej sprawdzić co się dzieję. Na szczęście istnieje obejście: zapisz bieżący stan zamykanego kontenera jako nowy obraz i uruchom go innym poleceniem, aby uniknąć istniejących awarii.

```
docker commit <container_id> moj-uszkodzony-kontener && docker run -it moj-uszkodzony-kontener /bin/bash
```

> To polecenie zapisze stan zmaykanego kontenera jao nowy obraz, uruchomi go oraz da nam możliwość wejścia do powłoki w celu diagnostyki.