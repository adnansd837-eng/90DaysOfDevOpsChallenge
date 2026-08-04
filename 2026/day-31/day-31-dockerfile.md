# Day 31 – Dockerfile: Build Your Own Images

## Objective

Today I learned how to write Dockerfiles and build my own Docker images. Before this, I mostly used existing images from Docker Hub, but now I understand how to create my own images by writing a Dockerfile. I also learned how Docker builds images layer by layer and why writing a good Dockerfile is important.

---

# Task 1 – My First Dockerfile

I created my first Dockerfile using the Ubuntu image as the base image. During the build process, I installed `curl` and set a default command to print a message when the container starts.

### What I Did

* Used `ubuntu` as the base image.
* Installed `curl`.
* Built the image with the tag `my-ubuntu:v1`.
* Ran a container and verified the output.

### Commands Used

```bash
docker build -t my-ubuntu:v1 .

docker run my-ubuntu:v1
```

### What I Learned

Creating a Docker image starts with a Dockerfile. Every instruction in the Dockerfile creates a new image layer.

---

# Task 2 – Dockerfile Instructions

I created another Dockerfile using the most common instructions.

### Instructions I Practiced

* `FROM` – Selects the base image.
* `RUN` – Executes commands during image build.
* `COPY` – Copies files from my local machine into the image.
* `WORKDIR` – Sets the working directory inside the container.
* `EXPOSE` – Documents the application's port.
* `CMD` – Defines the default command when the container starts.

### What I Learned

Each instruction has a specific purpose, and together they create a complete Docker image.

---

# Task 3 – CMD vs ENTRYPOINT

I created two different Docker images to understand the difference.

### CMD

When I ran the container normally, it executed the default command.

When I passed another command while running the container, the default command was replaced.

### ENTRYPOINT

With ENTRYPOINT, Docker always executed the defined command, and any extra values I passed were treated as arguments.

### My Understanding

* I use **CMD** when I want to provide a default command that users can easily replace.
* I use **ENTRYPOINT** when I want the container to always run a specific application.

---

# Task 4 – Build a Simple Website

I created a simple HTML page and used the `nginx:alpine` image to serve it.

### Steps

* Created an `index.html` file.
* Copied it into the Nginx web directory.
* Built the Docker image.
* Ran the container with port mapping.
* Opened the webpage in my browser.

### Commands Used

```bash
docker build -t my-website:v1 .

docker run -d -p 8080:80 my-website:v1
```

### What I Learned

Docker makes it easy to package and deploy a simple web application.

---

# Task 5 – Using .dockerignore

I created a `.dockerignore` file and added:

```text
node_modules
.git
*.md
.env
```

### What I Learned

The `.dockerignore` file prevents unnecessary files from being copied into the image. This keeps the image smaller and speeds up the build process.

---

# Task 6 – Build Optimization

I rebuilt the image after making a small change and noticed Docker reused the cached layers.

Then I changed the order of my Dockerfile and observed how the build cache worked.

### What I Learned

Docker builds images layer by layer. If a layer hasn't changed, Docker reuses it from the cache instead of building it again.

Keeping frequently changing instructions near the bottom of the Dockerfile helps reduce build time.

---

# Commands Used

```bash
docker build -t my-ubuntu:v1 .

docker run my-ubuntu:v1

docker build -t my-website:v1 .

docker run -d -p 8080:80 my-website:v1

docker images

docker ps

docker logs
```

---

# What I Learned

* I learned how to create my own Docker images using a Dockerfile.
* I understood the purpose of common Dockerfile instructions like `FROM`, `RUN`, `COPY`, `WORKDIR`, `EXPOSE`, and `CMD`.
* I learned the difference between `CMD` and `ENTRYPOINT`.
* I created and deployed a simple static website using Nginx.
* I learned why `.dockerignore` is important.
* I understood how Docker cache improves build speed and why Dockerfile layer order matters.

---

