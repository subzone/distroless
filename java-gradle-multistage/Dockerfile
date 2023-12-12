# Stage 1: Build the application
FROM openjdk:11-jdk-slim-bullseye AS build-env

# Copy your application files to /app
COPY . /app

# Build the application
WORKDIR /app
RUN gradle build

# Stage 2: Create the final image
FROM gcr.io/distroless/java11-debian11

# Copy the application JAR and any other required files
COPY --from=build-env /app/build/libs/*.jar /app.jar

# Set the entrypoint to run the application
ENTRYPOINT ["java", "-jar", "/app.jar"]