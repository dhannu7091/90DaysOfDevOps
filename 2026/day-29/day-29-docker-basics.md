# Day 29 Assignment – Introduction to Docker
## Task 1: What is Docker?
Research and write short notes on:

**1. What is a container and why do we need them?**
- A container is a lightweight, isolated environment that packages application code, runtime, libraries, and dependencies. It runs as a process on the host OS, sharing the same kernel. They are used for portability, faster deployment, and efficient resource utilization.

**2. Containers vs Virtual Machines — what's the real difference?**
- VMs virtualize the hardware, including a full operating system (OS), while containers virtualize the OS kernel and share it. Containers are lightweight, portable, and start instantly, making them ideal for microservices. VMs offer stronger security and isolation but are larger, slower, and resource-heavy.

**3. What is the Docker architecture? (daemon, client, images, containers, registry)**
- Docker uses a client-server architecture where the client communicates with the daemon, which in turn manages images and containers, often pulling or pushing images from a registry.
  - **Docker Client:** This is the primary interface users interact with, typically via a command-line interface (CLI). When you run a command like docker run or docker build, the client translates it into a REST API request and sends it to the Docker daemon.
  - **Docker Daemon (dockerd):** This is the persistent background process running on the host machine (the Docker Host). It is the "brain" of the Docker installation, responsible for performing all the heavy lifting: building images, running and managing containers, and managing Docker objects like networks and storage volumes.
  - **Docker Images:** An image is a read-only template with instructions for creating a Docker container. It contains the application code, runtime, libraries, and dependencies required to run the application consistently across different environments. Images are built from a Dockerfile and are composed of layers, which makes them lightweight and efficient to store and transfer.
  - **Docker Containers:** A container is a runnable, isolated instance of an image. It is a lightweight environment that packages an application and its dependencies, sharing the host OS kernel but isolated from other containers and the host system. You can create, start, stop, or delete containers using the Docker API or CLI.
  - **Docker Registry:** A registry is a centralized, stateless storage and distribution system for Docker images. The most well-known public registry is Docker Hub, which is the default location Docker looks for images. When you use docker pull or docker run commands, the daemon pulls the required image from the registry; when you use docker push, the daemon uploads your image to the registry.
 
## Task 2: Install Docker
- Completed ✅
## Task 3: Run Real Containers
- Completed ✅
## Task 4: Explore
- Completed ✅

## Terminal Output
📄 [View Full Terminal Output (PDF)](terminal_output/output.pdf)

