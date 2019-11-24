FROM oracle/graalvm-ce:19.3.0-java11 as graalvm
COPY . /home/app/micronaut-graal-app
WORKDIR /home/app/micronaut-graal-app
RUN gu install native-image
RUN native-image --no-server -cp build/libs/complete-*-all.jar

FROM debian:9
EXPOSE 8080
COPY --from=graalvm /home/app/micronaut-graal-app/micronaut-graal-app .
ENTRYPOINT ["./micronaut-graal-app"]