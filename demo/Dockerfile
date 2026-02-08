FROM eclipse-temurin:21-jdk

WORKDIR /app

# Copy Maven wrapper and config
COPY mvnw mvnw
COPY mvnw.cmd mvnw.cmd
COPY .mvn .mvn
COPY pom.xml pom.xml

# 🔥 FIX: give execute permission to mvnw
RUN chmod +x mvnw

# Download dependencies
RUN ./mvnw -B dependency:go-offline

# Copy source code
COPY src src

# Build the application
RUN ./mvnw -B clean package

# Expose port (Render uses PORT env)
EXPOSE 10000

# Run Spring Boot
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]
