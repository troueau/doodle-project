FROM alpine:latest as build
LABEL stage=build

# Install raquired packages
RUN apk add --update --no-cache git bash openjdk11
# Clone repo from remote
RUN git clone https://github.com/barais/doodlestudent.git /app --depth=1
# Copy local repo
WORKDIR /app/api
# Build the project
RUN ./mvnw clean package -Dquarkus.package.type=uber-jar


FROM alpine:latest

RUN apk add openjdk11-jre

WORKDIR /app
# Copy the jar file from the build stage
COPY --from=build /app/api/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar ./application.jar
# Expose the port
EXPOSE 8080

CMD ["java", "-jar", "/app/application.jar"]