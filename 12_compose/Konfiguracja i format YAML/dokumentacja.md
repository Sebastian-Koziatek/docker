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