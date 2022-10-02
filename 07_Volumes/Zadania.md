## Volume

1. Mapujemy folder w którym jesteśmy do kontenera z dockerem. Używamy do tego zmiennej `-v` (jak volume).
```
docker run -it -v ${PWD}:/szkolenie alpine
```
2. W katalogu widzimy że znajduje się folder szkolenie który zmapowaliśmy z tym folderem w którym jesteśmy.

3. Volumeny to osobne byty. Można je traktowac podobnie do virutalnych dysków twardych przy wirtualizacji. 
```
docker run -it -v dane:/szkolenie alpine
```
4. Spradź zawrtośc stworzonego wolumeny w kontenerze
```
ls 
cd szkolenie
ls
```
5. Stwórz w volumenie `dane` zamontowanym w kontenerze jako `szkolenie` dowolny plik:

```
echo . > plik
```
6. Sprawdz czy plik znajduje się w katalogu. Jeżeli tak to wyjdz z kontenera.
7. Uruchom drugi kontener w którym `volume dane` rownież podmontujesz.
```
docker run -it -v dane:/szkolenie alpine
```
8. Plik jak widac się znaduje w kontenerze. Spradźmy teraz utworzone przez nas volumeny
```
docker volume ls
```
>Jezeli volumen zostanie podmontowany podczas startowania kontnera do katalogu który już istnieje a tworzony volumen nie istnieje to wszystkie dane które beda znajdowały się w katalogu do którego montujemy volumen zostaną automatycznie skopiowane do utworzonego volumenu. Weźmy na przykład folder /etc z obrazu Linux alpine
```
docker run -it -v dane2:/etc alpine
```
> Jak widzisz cała zawartośc katalogu /etc została przekopiowana, sprawdźmy to w innym kontenerze.
9. Zamontuj volumen `dane` do katalogu `szkolenie` w kontenerze
``` 
docker run -it -v dane2:/szkolenie alpine   
```
___
## Volume w dockerfile

Jak widzicie w pliku dockerfile mozemy zdefnikować tworzenie volumenu 

```
FROM alpine 
VOLUME /data
ENTRYPOINT ["/bin/ls"]
CMD ["/"]
```
1. Zbuduj obraz z tego `dockerfile ` w katalogu `Volume_ls`

```
docker build -t volume ./Volume_ls/
```
3. Uruchom kontener ze zbudowanego obrazu
```
docker run volume
```
4. Zobacz że obraz który zbudowaliśmy utworzył nowy volume
```
docker volume ls
```
> Za każdym razem gdy uruchomimy tak zbudowany obraz zostanie nowo utworzony volumen
> 
5. Stwórz plik w dowolnym łatwo dostepnym miejscu np `c:\szkolenie\plik`
>touch /tmp/plik 
6. Uruchom kontener z flaga -v i z konfiuracja /data

```
docker run -v /tmp:/data volume /data
docker run -v c:\szkolenie\plik volume /data
```
> co się stanie przy wyknaniu takiej komendy? 
> <br>Zgodnie z plikiem docker file w CMD i ENTRYPOINT zefiniowaliśmy wkonwanie polecenia `ls` na folderze `/` ale w tym kontenerze napisujemy katalog `/` na katalog `/data`. Co się znajduje data w tym kontenerze przy takim ustawieniu? Wszystko co podalismy z parametrem -v czyli odpowiedniu `/tmp/` oraz `c:\szkolenie\`
___
## Manualne tworzenie volumenów

1. Stwórz swój volumen
```
docker volume create my-volume
```
2. Wylistuj nowe volumeny
```
docker volume ls
```
3. Uruchom dwa kontenery z obrazu my-nginx z ustawieniami:<br>
    a.  Uruchamiamy je w tle<br>
    b. Jeden kontener uruchom z ustawieniami `-v my-volume:/data:ro`<br>
    >opcja :ro oznacza `read only` czyli tylko do odczytu, wiec wszystkie plik w volumenie `my-volume` będą miały status tylko do odczytu w ramach tego kontenera
    c. Druki kontener uruchom bez flagi :ro
4. W drugim kontenerze stwórz nowy plik w katalogu /data
5. sprzwdź czy pierwszy kontener widzi stworzony plik
6. Zweryfikuj czy kontener nie moze zapisywac plikow do katalogu /data

```
docker run -d -v my-volume:/data:ro my-nginx
docker run -d -v my-volume:/data my-nginx
```
> wchodzimy do drugiego kontenera
```
docker ps
docker exec -it <nazwa_kontenera>
touch /data/testowy_plik
```
>wchodzimy do pierwszego kontenera
```
docker ps
docker exec -it <nazwa_kontenera> sh
cd /data
touch nowy_plik
```
>otrzymalismy blad  `touch: nowy_plik: Read-only file system` katalog /data posiada restrykcje zapisu i działa w trybi read only

Sprawdźmy lokalizacje volumenów
```
docker volume inspect <id>
```
> `"Mountpoint": "/var/lib/docker/volumes/35dd5513a053758712ad38d8a53e601032037770c33b1219d5364f0f90072b0c/_data",`

niestety dostęp jest możliwy tylko z linuksa, ani windows ani macos nie mają możliwości wyświetlania tego