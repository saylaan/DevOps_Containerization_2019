FROM maven:3.5-jdk-8-alpine AS builder

WORKDIR /usr/src/app

COPY . .

RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:8-jre-alpine

COPY --from=builder /usr/src/app/target/worker-jar-with-dependencies.jar .

ENTRYPOINT ["java","-jar","/usr/src/app/worker-jar-with-dependencies.jar"]  