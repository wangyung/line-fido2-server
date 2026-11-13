FROM eclipse-temurin:21-jdk-jammy AS builder
ENV OPEN_SOURCE_BUILD=true

USER root
WORKDIR /workspace/app
COPY . .
RUN ./gradlew --no-daemon :demo:dockerBuild

FROM eclipse-temurin:21-jdk-jammy
EXPOSE 8081
COPY --from=builder /workspace/app/fido2-demo/demo/build/libs/demo*.jar demo.jar
ENTRYPOINT ["java","-jar","/demo.jar"]
