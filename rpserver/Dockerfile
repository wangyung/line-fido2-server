FROM eclipse-temurin:21-jdk-jammy AS builder
ENV OPEN_SOURCE_BUILD=true

USER root
WORKDIR /workspace/app
COPY . .
RUN ./gradlew --no-daemon :rpserver:dockerBuild

FROM eclipse-temurin:21-jdk-jammy
EXPOSE 8080
COPY --from=builder /workspace/app/rpserver/build/libs/rpserver*.jar rpserver.jar
ENTRYPOINT ["java","-Dspring.profiles.active=docker","-jar","/rpserver.jar"]
