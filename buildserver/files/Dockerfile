FROM ubuntu:18.04 as build
RUN apt-get update \
    && apt-get install -y default-jdk git maven \
    && rm -rf /var/cache/apt
WORKDIR /home
RUN git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello
WORKDIR /home/boxfuse-sample-java-war-hello
RUN mvn package

FROM tomcat:8.0-alpine
COPY --from=build /home/boxfuse-sample-java-war-hello/target/hello-1.0.war /usr/local/tomcat/webapps