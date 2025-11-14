# Step 1: Build Stage
FROM maven:3.9.6-amazoncorretto-17 AS build
WORKDIR /app

# Copy project files
COPY demo/pom.xml .
COPY demo/src ./src

# Build the JAR
RUN mvn clean package -DskipTests

# Step 2: Run Stage
FROM amazoncorretto:17
WORKDIR /app

# Copy the JAR from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
