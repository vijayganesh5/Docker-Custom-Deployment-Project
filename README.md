# 🐳 Custom Nginx Docker Image Deployment

### **Task Description**

Create a **custom Nginx Docker image** and deploy it using **Docker Compose**, where the **volume bind mount** is located at `/var/opt/nginx`.
Finally, push the custom image to **Docker Hub**.

---

## 🚀 Tech Stack

* **AWS EC2 (Ubuntu)** — Cloud instance to run everything
* **Docker** — To build and run containers
* **Docker Compose** — To simplify container deployment
* **Nginx** — Web server to serve your HTML page

---

## 🧩 Project Structure

```
custom-nginx/
│
├── Dockerfile
├── docker-compose.yml
├── index.html
└── data/
```

---

## 📜 Files Explanation

### **index.html**

Simple web page content.

```html
<h1>Welcome from Vijay Ganesh's Custom Nginx!</h1>
```

---

### **Dockerfile**

Defines your custom Nginx image.

```dockerfile
# Use official Nginx base image
FROM nginx:alpine

# Copy webpage into container
COPY index.html /usr/share/nginx/html/index.html

# Add maintainer info
LABEL maintainer="vijayganesh5"
```

---

### **docker-compose.yml**

Defines how to run the Nginx container with a volume bind mount.

```yaml
version: '3'
services:
  nginx:
    image: vijayganesh5/custom-nginx
    ports:
      - "80:80"
    volumes:
      - ./data:/var/opt/nginx
```

---

## 🛠️ Setup & Execution Steps

### **1️⃣ Connect to EC2**

```bash
ssh -i your-key.pem ubuntu@<your-ec2-public-ip>
```

---

### **2️⃣ Install Docker and Docker Compose**

```bash
sudo apt update
sudo apt install -y docker.io docker-compose
sudo systemctl enable docker
sudo systemctl start docker
```

---

### **3️⃣ Create Project Folder**

```bash
mkdir custom-nginx && cd custom-nginx
```

---

### **4️⃣ Create the Files**

```bash
echo "<h1>Welcome from Vijay Ganesh's Custom Nginx!</h1>" > index.html
```

Create the `Dockerfile` and `docker-compose.yml` as shown above.

---

### **5️⃣ Build the Custom Docker Image**

```bash
sudo docker build -t vijayganesh5/custom-nginx .
```

---

### **6️⃣ Run Using Docker Compose**

```bash
mkdir data
sudo docker-compose up -d
```

---

### **7️⃣ Access Your Website**

Open your browser and visit:

```
http://<your-ec2-public-ip>
```

You’ll see your custom HTML page being served by your custom Nginx container.

---

### **8️⃣ Push to Docker Hub**

Login and push the image:

```bash
sudo docker login
sudo docker push vijayganesh5/custom-nginx
```

---

### **9️⃣ Stop and Clean Up**

```bash
sudo docker-compose down
```

---

## 📦 Output Example

Once deployed, you should see this in your browser:

```
Welcome from Vijay Ganesh's Custom Nginx!
```

---

## 🧠 Key Concepts Learned

* Building a **custom Docker image**
* Using **Docker Compose** for deployment
* Implementing **volume bind mounts**
* Pushing Docker images to **Docker Hub**
* Hosting and accessing your app on **AWS EC2**

---

## ⚙️ Troubleshooting

| Issue                           | Fix                                                                    |
| ------------------------------- | ---------------------------------------------------------------------- |
| **Port 80 not accessible**      | Check EC2 security group → Inbound rules → Add rule for port 80 (HTTP) |
| **Permission denied on volume** | Use `sudo` when running docker-compose                                 |
| **Image not found**             | Ensure you build the image before running compose                      |
| **Push denied**                 | Make sure Docker Hub username in image name matches your account       |

---

## 🏁 Summary

This project helps you understand the full workflow:

* Creating a **custom image**
* Deploying via **Docker Compose**
* Managing **volumes and mounts**
* **Publishing** your work to Docker Hub

---

## 🎉 Output Link with Screenshots:
- https://docs.google.com/document/d/1vBC9YA1AdYFEIPhpsqvbw3ZEU60em977pZJ4RkC2AUE/edit?usp=sharing

---
