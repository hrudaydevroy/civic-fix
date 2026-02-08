FROM eclipse-temurin:21-jdk

WORKDIR /app

COPY mvnw mvnw
COPY mvnw.cmd mvnw.cmd
COPY .mvn .mvn
COPY pom.xml pom.xml

RUN ./mvnw -B dependency:go-offline

COPY src src

RUN ./mvnw -B clean package

EXPOSE 10000

CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]
