# 🐳 Docker Architecture

Docker follows a **client-server architecture** with three main components:

1. **Docker Client**
2. **Docker Daemon (Server)**
3. **Docker Objects (Images, Containers, Volumes, Networks)**

---

## ⚙️ 1. Docker Client (`docker`)
The **Docker Client** is the command-line tool you use to interact with Docker.

**Examples:**
```bash
docker run nginx
docker build -t myapp .
docker ps
```
The client sends these commands to the **Docker Daemon** using **REST APIs**.

---

## 🧠 2. Docker Daemon (`dockerd`)
The **Docker Daemon** is the core engine that performs all Docker tasks.

It:
- Builds and runs containers.
- Manages images, networks, and volumes.
- Listens for API requests from the Docker client.

Communication happens via:
- **UNIX socket** (default in Linux)
- or **TCP socket** (for remote connections).

---

## 📦 3. Docker Objects

### 🖼️ Images
- Read-only templates used to create containers.
- Example: `nginx:latest`, `ubuntu:20.04`
- Built from Dockerfiles.

### 🧩 Containers
- Running instances of images.
- Lightweight and isolated.
- You can start, stop, move, or delete containers anytime.

### 🗄️ Volumes
- Used for **persistent data storage**.
- Keeps data even if the container is deleted.

### 🌐 Networks
- Allow communication between containers or between containers and the host.

---

## ☁️ 4. Docker Registry (e.g., Docker Hub)
A **repository** for storing Docker images.

Example:
```bash
docker pull nginx
```
This pulls the image from Docker Hub (or a private registry).

---

## 🧩 5. How It All Works Together

1. You (client) run:
   ```bash
   docker run nginx
   ```
2. The **client** sends the request to the **daemon**.
3. The **daemon** checks if the `nginx` image is available locally.
   - If not, it **pulls** it from Docker Hub.
4. It **creates** and **runs** a container from that image.
5. You can then interact with it using commands like `docker ps`, `docker exec`, etc.

---

## 🧭 Architecture Diagram (Conceptual)

```
+-----------------------------+
|        Docker Client        |
| (CLI / REST API / GUI)      |
+-------------+---------------+
              |
              | Docker API
              v
+-----------------------------+
|        Docker Daemon        |
|  - Builds images            |
|  - Manages containers       |
|  - Handles networks/volumes |
+-------------+---------------+
              |
              v
+-----------------------------+
|     Docker Objects          |
| (Images, Containers, etc.)  |
+-----------------------------+
              |
              v
+-----------------------------+
|     Docker Registry         |
| (Docker Hub / Private Repo) |
+-----------------------------+
```

---

## 🧠 Optional Components
- **Docker Compose** – Define and run multi-container apps using `docker-compose.yml`.
- **Docker Swarm** – Native container orchestration (alternative to Kubernetes).

---

**✅ Summary:**
Docker = *Client* + *Daemon* + *Objects* + *Registry*
