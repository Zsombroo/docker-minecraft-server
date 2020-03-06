FROM ubuntu:bionic

# Install OpenJDK-8
RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean;

# Fix certificate issues
RUN apt-get update && \
    apt-get install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;

# Setup JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
# RUN export JAVA_HOME

# Create server directory
RUN mkdir Minecraft_server

# Change work directory
WORKDIR Minecraft_server

# Copy files from host into it
COPY server.jar .
COPY start.sh .

# Give rights to run start.sh
RUN chmod +x start.sh

# Open minecraft server default port
EXPOSE 25565 25575

# Start minecraft server to generate files
# Gonna fail 'cuz eula is not accepted yet
RUN ./start.sh

# Accept eula
RUN sed -i 's/eula=false/eula=true/g' eula.txt

ENTRYPOINT /Minecraft_server/start.sh
