FROM alpine AS build

RUN apk update && apk add openjdk17-jdk maven git

WORKDIR /app

RUN git clone https://github.com/spring-projects/spring-petclinic.git

WORKDIR /app/spring-petclinic

RUN ./mvnw package

#this file doesn't work (why?) maybe alpine doesn't have (*)
#COPY target/*.jar app.jar

FROM openjdk:17-alpine

WORKDIR /app

COPY --from=build /app/spring-petclinic/target/spring-petclinic-3.3.0-SNAPSHOT.jar app.jar

EXPOSE 8080

#CMD ["java","-jar","./target/spring-petclinic-3.3.0-SNAPSHOT.jar"]

CMD ["java","-jar","/app/app.jar"]
