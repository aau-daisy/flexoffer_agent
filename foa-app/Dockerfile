# Use the Oracal Java 8 as parent image
FROM java:8
MAINTAINER "muhaftab@cs.aau.dk"
LABEL vendor="GOFLEX"

# Set the working directory to /app
WORKDIR /app

# Copy the required files into the container at /app
ADD target/foa-app.jar /app/foa-app.jar
ADD ca-cert.jks /app/ca-cert.jks

# Create a mount point on the native host.
VOLUME /tmp

# Port available to the world outside this container
EXPOSE 8081

# Start the application when the container launches
ENTRYPOINT ["java", "-Duser.timezone=CET", "-Dspring.profiles.active=container", "-jar", "foa-app.jar"]
