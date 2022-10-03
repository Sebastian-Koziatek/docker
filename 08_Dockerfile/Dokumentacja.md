1. Co robi plik `Dockerfile?`

Pliki Docker to zestawy instrukcji używanych do tworzenia obrazu Docker. Format Dockerfile jest sformalizowany przez Docker i oparty na zestawie słów kluczowych, które pozwalają manipulować systemem plików kontenera.

Każde słowo kluczowe jest pisane wielką literą i następuje po nim określone argumenty:

```
FROM ubuntu:latest
COPY /source /destination
RUN touch /example-demo
```

Użyte są tutaj trzy instrukcje: 
<br> `FROM` - który definiuje obraz bazowy, z którego dziedziczy twój;
<br> `COPY`- która pozwala dodawać pliki z hosta do ścieżek wewnątrz kontenera; i <br>
`RUN` s- który jest tranzytem do wykonywania poleceń w systemie plików kontenera.

## Najlepsze praktyki dotyczące pisania pliku Docker 

1. Skanuj w poszukiwaniu luk w zabezpieczeniach
2. Usuń niepotrzebne zależności
3. Bezpieczne wstrzyknięte poświadczenia
4. Uruchom jako użytkownik inny niż root
5. Śledź wersje Dockerfile
6. Twórz bezstanowe, odtwarzalne kontenery
7. Obsługa argumentów wielowierszowych
8. Poznaj różnicę między CMD a ENTRYPOINT
9. Użyj KOPIUJ zamiast DODAJ