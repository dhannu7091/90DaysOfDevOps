# Get the base image
FROM ubuntu

# Create a working directory to store all the files
WORKDIR /work-file

# Install curl
RUN apt-get update && apt-get install -y curl

CMD ["echo", "Hello from my custom image!"]