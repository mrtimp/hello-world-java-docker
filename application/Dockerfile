FROM maven:3.8-openjdk-18-slim AS build

RUN apt update && \
    apt install \
      --no-install-recommends \
      --no-install-suggests \
      tzdata && \
    apt clean

COPY pom.xml pom.xml
COPY src src

RUN mvn clean package

FROM redhat/ubi9-minimal:9.5

ENV TV=Pacific/Auckland

RUN microdnf install \
      -y \
      --nodocs \
      java-11-openjdk-headless && \
    microdnf clean all

WORKDIR /work/

COPY --from=build /target/*.jar application.jar

EXPOSE 8080
CMD ["java", "-jar", "application.jar"]