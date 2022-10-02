
## Instalacja
Docker compose wystarczy pobrać ze strony - https://docs.docker.com/compose/install/ 
W przypadku systemu linux zalecane jest używanie reposytorium do pobrania. Jeżeli jest skonfigurowane repozytorium zgodnie z dokumentacja to wystarczy

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
___
## Wstęp do docker-compose.

1. W zadaniu `04_registry` w "ramach zabawy" pobraliśmy i uruchomiliśmy kilka użytecznych obrazów dockera. Użyliśmy do tego kilku komend. Za pomocą docker compose jesteśmy w stanie zapisać cała konfigurację takiego Multimedialnego środowiska domowego w ramach jednego pliku.
   


Dokumentacja:
- docker compose <a href="https://docs.docker.com/compose/compose-file/compose-file-v2/" title="docker-compose version 2"> Version:2</a></td> i <a href="https://docs.docker.com/compose/compose-file/compose-file-v3/" title="docker-compose version 3">Version:3 </a>
- <a href="https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html"> Yaml </a> na podstawie ansible 
___
## docker-compose

### Najważniejsze komendy:<br>

- `docker-compose build` - wykonuje zbudowanie pliku `docker-compose.yml`.
- `docker-compose images` - listuje wszystkie zbudowane obrazy uzywane przez `docker-compose`.
- `docker-compose stop` - zatrzymuje wskazany kontener.
- `docker-compose run` - komenda podobna do `docker run`, stworzy kontener z obrazu określonego w pliku `docker-compose.yml`.
- `docker-compose up` - to połączenie komend `docker-compose build` i `docker-compose run`. Zbuduje obrazy jeżeli nie są zbudowane i uruchomi kontener. 
- `docker-compose ps` - listuje wszystkie kontenery uruchomione przez `docker-compose`
- `docker-compose down` - komenda podobna do `docker system prune`. Zastopuje serwisy w kontenerze, zamknie kontener, usuniego, usunie konfiguracje sieci oraz obrazy.
___
### Struktura pliku

```services:
  frontend:
    image: my-vue-app
    ...
  backend:
    image: my-springboot-app
    ...
  db:
    image: postgres
    ...
```