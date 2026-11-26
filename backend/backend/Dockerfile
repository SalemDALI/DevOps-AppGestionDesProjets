
# Java 21 runtime image
FROM eclipse-temurin:21-jre

# Working directory
WORKDIR /app

# Copy Spring Boot application
COPY target/backend-1.0.0.jar app.jar

# Application port
EXPOSE 8080

# Start Spring Boot
ENTRYPOINT ["java", "-jar", "app.jar"]

