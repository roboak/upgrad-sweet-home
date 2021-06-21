FROM maven:3.8.1-jdk-11 AS build
WORKDIR /usr/src/app  
COPY src ./src  
COPY pom.xml .  
RUN mvn clean install

FROM gcr.io/distroless/java
WORKDIR /usr/src/app  
COPY --from=build /usr/src/app/target/eurekaServer.jar eurekaServer.jar  
EXPOSE 8080  
ENTRYPOINT ["java","-jar","eurekaServer.jar"]  
