### Urchamianie aplikacji javy w kontenerze na przykładzie springboot

1. Zajrzyj na strone springboota. Pozwala on przyśpieszyc i ułątwić budowanie alikacji webowych i mikroserwisów we frameworku spring.   

`https://spring.io/guides/gs/spring-boot-docker/`

Na podstawie dokumetacji ze strony Spring boot przygotowałem na dzisiaj prostą aplikację webową (w katalogu z lekcją). Przekompilujemy ją, uruchomimy i skonteneryzujemy. 

1. Za pomocą mavena zbudujemy teraz ten projekt. W katalogu z aplikacja uruchom polecenie
```
mvn clean install
```
2. Utworzył nam sie folder `target` który zawiera naszą aplikację Javy - `spring-boot-docker-0.0.1-SNAPSHOT.jar`
3. Skoro mamy zbudowaną już aplikację to stwórzmy sobie dockerfile aby stworzyc dla niej kontener. <br>
Stwórz docker file który: </br>
- Zbuduje kontener z obrazu `FROM openjdk:19`
- Stworzy zmienną środowiskową `ARG` o wartości `JAR_FILE=target/*.jar`
- skopiuje naszą zbudowną aplikację `${JAR_FILE}` do kontenera i nazwie ją `app.jar`
- W entrypoint spwooduje jej uruchomienie `java -jar ./app.jar`


Nasz dockerfile powinien wyglądac tak:

```
FROM openjdk:19
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
5. Zbudujmy obraz z dockerfile

```   
docker build -t springboot .
```

6. Sprawdźmy czy aplikacja urochomi. Uruchom kontener z obrazu w tle i na porcie 8080

```
docker run -p 8080:8080 springboot
```