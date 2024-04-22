FROM openjdk:11-jre-slim

WORKDIR /app

COPY target/my-springboot-app.jar /app/app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]

