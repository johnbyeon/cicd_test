# Build stage
FROM eclipse-temurin:17-jdk-jammy AS build
WORKDIR /home/gradle/src
COPY . .
RUN chmod +x gradlew
RUN ./gradlew build --no-daemon -x test

# Run stage
FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
COPY --from=build /home/gradle/src/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]


