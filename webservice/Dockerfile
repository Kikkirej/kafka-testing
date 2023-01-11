
FROM gradle:7.6-jdk17 as build

COPY build.gradle .
COPY src src

RUN gradle build

FROM openjdk:17
VOLUME /tmp
#https://stackoverflow.com/questions/73516116/got-error-xargs-is-not-available-when-trying-to-run-a-docker-image
RUN microdnf install findutils

COPY --from=build /build/libs/webservice*.jar /app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
