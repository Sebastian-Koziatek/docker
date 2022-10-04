## Zmienne w plikach konfiguracyjnych

Spring w swoich plikach konfiguracyjnych potrafi dostać się do zmiennych środowiskowych. Dzięki temu możemy ich użyć w dowolnym miejscu naszej konfiguracji. Oczywiście, najlepszym miejscem wykorzystania zmiennych będą adresy usług, baz danych i wszystko to co się różni pomiędzy środowiskami.

Dla przykładu, poniżej plik konfiguracyjny zawierający zmienną SPRING_MONGO_HOST jako adres bazy danych MongoDB:

```
spring:
  data:
    mongodb:
      uri: mongodb://${SPRING_MONGO_HOST:localhost}/effent
```

> Zmienne w dockerfile

```
FROM openjdk:11

COPY target/app.jar /app/app.jar
COPY ./application.yml /app/config/application.yml

ENV SPRING_MONGO_HOST=somehost

WORKDIR /app

EXPOSE 8080
ENTRYPOINT java -jar app.jar
```

> zmienne w docker-compose

```yml
version: "3"
services:
  app:
    build: .
    links:
      - mongodb
    depends_on:
      - mongodb
    environment:
      - SPRING_MONGO_HOST=mongodb
    ports:
      - "8080:8080"
  mongodb:
    image: mongo
    hostname: mongodb
```

docker run --env `SPRING_MONGO_HOST=mongodb` image-name

## Hasła i loginy w docker-compose w ramach zmiennych środowiskowych

```yml
version: '3.1'

services:
  db:
    container_name: Mongo-db
    image: mongo:latest
    restart: always
    volumes:
      - ./myData:/data/db
    environment:
      - MONGO_INITDB_DATABASE=${DATABASE}
      - MONGODB_USER=${USERNAME}
      - MONGODB_PASS=${PASS}
    ports:
      - 27020:27017
```