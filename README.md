## Project: Deploying a Simple Python Web App Using Docker Swarm

### **Step 1: Clone project repo**
```
git clone https://github.com/aashishmalviya/docker_swarm.git
cd docker_swarm
```

### **Step 2: Build the Docker Image**

In a terminal, run:

```bash
docker build -t docker_swarm:latest .
```

### **Step 3: Initialize Docker Swarm**

If your machine isn’t already part of a swarm:

```bash
docker swarm init
```

*Tip*: If working alone, you can use only your local laptop - Swarm still works.

### **Step 4: Deploy the App as a Swarm Service**

Run:

```bash
docker service create --name flask-demo --publish 5000:5000 --replicas 3 docker_swarm:latest
```

- `--name flask-demo`: Name of the service
- `--publish 5000:5000`: Expose port 5000
- `--replicas 3`: Run 3 containers (on single or multiple nodes)

### **Step 5: Access and Test**

- Open your browser and go to `http://localhost:5000`
- Refresh a few times - you’ll likely see the hostname change. This means requests are getting balanced between the replicas.

### **Step 6: Swarm Scaling and Management**

- **Scale up**: `docker service scale flask-demo=5`
- **List services**: `docker service ls`
- **List tasks/containers**: `docker service ps flask-demo`
- **Remove service**: `docker service rm flask-demo`

<br>
<p align="center">
  Liked it? ❤️ <a href="https://linkedin.com/in/aashish-malviya">Let's connect 🤗</a>
</p>