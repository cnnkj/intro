# Docker Compose Configuration Guide

This document explains the structure and usage of the `docker-compose.yml` file for managing multiple containers efficiently.

## **File Structure**

```yaml
version: '3.8'  # Specifies the Compose file version

services:  # Defines the containers to run
  web:  # Service name (customizable)
    image: nginx:latest  # Uses the Nginx latest image
    ports:
      - "8080:80"  # Maps host port 8080 to container port 80
    volumes:
      - ./html:/usr/share/nginx/html  # Mounts local HTML files to the container
    depends_on:
      - db  # Ensures 'db' service starts before 'web'

  db:
    image: postgres:latest  # Uses PostgreSQL latest image
    restart: always  # Restarts container on failure
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    volumes:
      - db_data:/var/lib/postgresql/data  # Persistent storage for database

volumes:
  db_data:  # Named volume for persistent database storage
```

## **Explanation of Structure**

| **Key**        | **Description** |
|---------------|--------------|
| `version`     | Defines the Compose file version (e.g., `3.8`). |
| `services`    | Lists the containers to be managed. |
| `image`       | Specifies the container image to be used. |
| `build`       | Used when building an image from a `Dockerfile`. |
| `ports`       | Maps host ports to container ports (`host:container`). |
| `volumes`     | Mounts local files/directories into containers. |
| `environment` | Defines environment variables for the container. |
| `depends_on`  | Ensures that a service starts only after another service is up. |
| `restart`     | Defines restart policy (`always`, `on-failure`, `no`). |
| `volumes:`    | Declares persistent volumes for data storage. |

## **Usage Instructions**

### **1️⃣ Start Containers**
```sh
docker-compose up -d
```
(`-d` runs in detached mode.)

### **2️⃣ Stop Containers**
```sh
docker-compose down
```

### **3️⃣ Check Running Containers**
```sh
docker-compose ps
```

### **4️⃣ Restart a Service**
```sh
docker-compose restart web
```

## **Conclusion**
`docker-compose.yml` simplifies multi-container management, making it easier to deploy web applications with services like **Nginx** and **PostgreSQL**. 🚀

For more details, visit [Docker Compose Documentation](https://docs.docker.com/compose/).

