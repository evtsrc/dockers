FROM gradle:4.7.0-jdk8-alpine AS build
COPY --chown=gradle:gradle . /home/gradle/book-manager
WORKDIR /home/gradle/book-manager
RUN gradle build --no-daemon

FROM java:8
VOLUME /tmp
EXPOSE 8080
COPY --from=build /home/gradle/book-manager/build/libs/book-manager-1.0-SNAPSHOT.jar book-manager-1.0-SNAPSHOT.jar
ENTRYPOINT ["java", "-jar"]
CMD ["book-manager-1.0-SNAPSHOT.jar"]
