FROM openjdk:8 AS BUILD_IMAGE
WORKDIR /usr/src/app/
RUN apt update -y && apt install maven -y
COPY ./ /usr/src/app/
RUN mvn install -DskipTests


FROM openjdk:8 
WORKDIR /usr/src/app/
COPY --from=BUILD_IMAGE /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1-SNAPSHOT.jar

EXPOSE 9000
ENTRYPOINT ["java","-jar", "book-work-0.0.1.jar"]

#-jar -> A flag for the Java command that tells it to execute a JAR (Java Archive) file to host the API Gateway.
