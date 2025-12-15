FROM amazoncorretto:25-alpine-full AS build
WORKDIR /app

RUN apk add --no-cache maven

COPY pom.xml .
COPY src ./src

# Build JAR
RUN mvn clean package -DskipTests

FROM amazoncorretto:25-alpine-full
WORKDIR /app

COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar ./app.jar

ENTRYPOINT ["java", "-jar", "./app.jar"]
