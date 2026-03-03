# Day 30 Assignment – Docker Images & Container Lifecycle

## Task 1: Docker Images
1. Pull the `nginx`, `ubuntu`, and `alpine` images from Docker Hub ✅
2. List all images on your machine — note the sizes

| Images | Size |
| :--- | :---: |
| nginx | 161 MB |
| ubuntu | 78.1 MB |
| alpine | 8.44 MB |

3. Compare `ubuntu` vs `alpine` — why is one much smaller?
- alpine
4. Inspect an image — what information can you see?
- The docker image inspect command provides detailed, low-level information about images. It returns the data in a JSON array format by default, which includes Image ID and Tags, Creation Date and Size, Layers, Base Image, Configuration, Architecture and OS
5. Remove an image you no longer need ✅


---
## Task 2: Image Layers
1. Run `docker image history nginx` — what do you see?
- it shows creation history of image and showing each layer and the command
2. Each line is a layer. Note how some layers show sizes and some show 0B ✅

3. Write in your notes: What are layers and why does Docker use them?
- Docker layers are read-only, immutable filesystem changes (additions, deletions, modifications) created by Dockerfile instructions like RUN``COPY, and ADD. Stacked together using a union filesystem (like OverlayFS), they form a single container image. They enable efficient storage, faster builds via caching, and easy sharing of common base images.
- Why Docker Uses Layers:
  - Reusability & Space Optimization: Since layers are immutable, they can be shared across multiple images. If multiple containers use the same base image (e.g., Ubuntu), they share the same underlying layers, reducing disk space usage.
  - Faster Builds (Caching): Docker caches each layer during the build process. If a Dockerfile instruction hasn't changed, Docker reuses the cached layer, significantly speeding up subsequent builds.
  - Efficiency in Transportation: When pushing or pulling images, Docker only transfers layers that are not already present on the host, saving network bandwidth.
  - Version Control: Layers act as a history of changes to the image.
  - Copy-on-Write (CoW): When a container runs, a thin, writable container layer is added on top of the read-only image layers. Changes made within the container (like writing a file) occur only in this top layer, keeping the base image intact.

---
## Task 3: Container Lifecycle
Practice the full lifecycle on one container:

1. Create a container (without starting it)
- `docker create --name web-server nginx`
2. Start the container
- `docker start web-server`
3. Pause it and check status
- `docker pause web-server`
4. Unpause it
- `docker unpause web-server`
5. Stop it
- `docker stop web-server`
6. Restart it
- `docker restart web-server`
7. Kill it
- `docker kill web-server`
8. Remove it
- `docker rm web-server`

Check docker ps -a after each step — observe the state changes.


---
## Task 4: Working with Running Containers
1. Run an Nginx container in detached mode
- `docker run -d --name web-server -p 80:80 nginx`
2. View its logs
- `docker logs web-server`
3. View real-time logs (follow mode)
- `docker logs -f web-server`
4. Exec into the container and look around the filesystem
- `docker exec -it web-server bash`
5. Run a single command inside the container without entering it
- `docker exec -it web-server bash` -> `ls` `cd /usr/share/nginx`
6. Inspect the container — find its IP address, port mappings, and mounts
- `"IPAddress": "172.17.0.2"`, `"HostPort": "80"`, `"Mounts": []`

---
## Task 5: Cleanup
1. Stop all running containers in one command
- `docker stop $(docker ps -q)`
2. Remove all stopped containers in one command
- `docker container prune`
3. Remove unused images
- `docker image prune -a`
4. Check how much disk space Docker is using
- `docker system df`
