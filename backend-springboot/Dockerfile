# ---------- Build Stage ----------
FROM maven:3.9.9-eclipse-temurin-21 AS build

WORKDIR /app

# Copy the entire Spring Boot project
COPY . .

# Build the application
RUN mvn clean package -DskipTests

# ---------- Runtime Stage ----------
FROM eclipse-temurin:21-jre

WORKDIR /app

# Copy the generated JAR
COPY --from=build /app/target/*.jar app.jar

# Render provides the PORT environment variable
EXPOSE 8080

# Start the application
ENTRYPOINT ["java","-jar","app.jar"]