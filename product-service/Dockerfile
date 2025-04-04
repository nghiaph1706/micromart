FROM openjdk:11-jdk-slim

WORKDIR /app
COPY target/product-service.jar /app/product-service.jar

EXPOSE 8080
CMD ["java", "-jar", "product-service.jar"]