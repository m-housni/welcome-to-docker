Here’s a detailed breakdown of the commands provided:

---

### **Introductory Section**
- The text welcomes users to Docker and provides a way to get started with Docker by running a pre-built container using the `docker/welcome-to-docker` image.

---

### **Command 1**
#### **`docker run -d -p 8088:80 --name welcome-to-docker docker/welcome-to-docker`**
- **Purpose**: Runs a pre-built Docker container from the `docker/welcome-to-docker` image.
- **What happens**:
  1. **Detached mode** (`-d`): Runs the container in the background.
  2. **Port mapping** (`-p 8088:80`): Maps **port 8088** on the host machine to **port 80** in the container.
  3. **Naming** (`--name welcome-to-docker`): Names the container `welcome-to-docker`.
  4. **Image**: Pulls the `docker/welcome-to-docker` image if it isn’t available locally and runs it.
- **Result**: A running Docker container accessible at `http://localhost:8088`.

---

### **Building Section**
- This section is aimed at maintainers who want to **build the Docker image** locally rather than using the pre-built one.

---

### **Command 2**
#### **`docker build -t welcome-to-docker .`**
- **Purpose**: Builds a new Docker image from the local repository.
- **What happens**:
  1. **`docker build`**: Creates a Docker image based on the instructions in the `Dockerfile` located in the current directory (`.`).
  2. **Tagging** (`-t welcome-to-docker`): Names (tags) the resulting image as `welcome-to-docker`.

---

### **Command 3**
#### **`docker run -d -p 8088:3000 --name welcome-to-docker welcome-to-docker`**
- **Purpose**: Runs the locally built `welcome-to-docker` image.
- **What happens**:
  1. **Detached mode** (`-d`): Runs the container in the background.
  2. **Port mapping** (`-p 8088:3000`): Maps **port 8088** on the host machine to **port 3000** in the container.
  3. **Naming** (`--name welcome-to-docker`): Names the container `welcome-to-docker`.
  4. **Image**: Runs the locally built `welcome-to-docker` image.
- **Result**: A running Docker container accessible at `http://localhost:8088`.

---

### **Key Points:**
1. **For users**:
   - Use the pre-built `docker/welcome-to-docker` image.
   - Run the first `docker run` command and access the containerized app.

2. **For maintainers**:
   - Build the image locally with `docker build`.
   - Run the app with the second `docker run` command (port 3000 inside the container).

### **Why Two Port Configurations?**
- The pre-built image maps port 80 in the container to port 8088 on the host.
- The locally built image maps port 3000 in the container to port 8088 on the host. This indicates the app in the local image might be configured to serve on port 3000 instead of port 80.