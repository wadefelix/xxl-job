FROM maven:3.3-jdk-8 as builder

WORKDIR /usr/src/mymaven
COPY . .
RUN mvn package

FROM openjdk:8-jre-slim
MAINTAINER xuxueli

ENV PARAMS=""

ENV TZ=PRC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY --from=builder /usr/src/mymaven/xxl-job-executor-samples/xxl-job-executor-sample-springboot/target/xxl-job-executor-sample-springboot-2.4.1-SNAPSHOT.jar /app.jar

ENTRYPOINT ["sh","-c","java -jar $JAVA_OPTS /app.jar $PARAMS"]
