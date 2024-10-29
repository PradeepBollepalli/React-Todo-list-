# React Todo List Project Documentation

## Table of Contents

1. [Project Overview](#project-overview)
2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Clone the Repository](#clone-the-repository)
 3. [Building and Deploying the Application](#building-and-deploying-the-application)
   - [Building the Docker Image](#building-the-docker-image)
     - [Creating the Dockerfile](#creating-the-dockerfile)
     - [Building the Image](#building-the-image)
     - [Running the Docker Image Locally](#running-the-docker-image-locally)
 4. [Deploying to Kubernetes](#deploying-to-kubernetes)
   - [Creating the Deployment YAML File](#creating-the-deployment-yaml-file)
   - [Deploying the Application](#deploying-the-application)
   - [Accessing the Application](#accessing-the-application)
 5. [Viewing the Kubernetes Dashboard](#viewing-the-kubernetes-dashboard)
   - [Accessing the Dashboard](#accessing-the-dashboard)
 6. [Cleanup](#cleanup)
 7. [Conclusion](#conclusion)

## Project Overview

The React Todo List application is designed to provide a practical tool for managing daily tasks, allowing users to add, complete, and delete tasks seamlessly. Built using React for the frontend and Node.js for backend operations, the application utilizes Docker for containerization and Kubernetes (via MicroK8s) for deployment, ensuring consistent and scalable environments. The component-driven architecture enables modularity, while effective state management ensures that the user interface dynamically reflects the current state of tasks. Future enhancements could include user authentication, persistent storage for task management, search and filter functionalities, and deployment on cloud platforms, making it a robust project for developing modern web development skills.

## Getting Started
To get started with this project, follow the steps below.

### Prerequisites
Ensure you have the following software installed on your machine:
- **Node.js**: [Download Node.js](https://nodejs.org/)
- **npm**: Comes with Node.js installation
- **Docker**: [Download Docker](https://www.docker.com/get-started)
- **MicroK8s**: [Install MicroK8s](https://microk8s.io/docs/)

### Clone the Repository

Begin by cloning the repository to your local machine:
```
git clone https://github.com/MaheshRautrao/React-Todo-list.git
cd React-Todo-list
```
   ![image](https://github.com/user-attachments/assets/cecc63f8-9b44-4d4d-8937-49ae722e37e9)
   

#Building the Docker Image

To deploy the application using Docker, you need to build a Docker image.

Creating the Dockerfile

Create a Dockerfile in the root directory of your project with the following content:

dockerfile
```
# Use Node.js as the base image
FROM node:14

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the application port
EXPOSE 80

# Command to run the application
CMD ["npm", "start"]
```

# Run the following command to build the Docker image:

```
docker build -t pradeep051/react-todo-app:latest .
```
 ![image](https://github.com/user-attachments/assets/c0d519e8-f72a-4bbb-9080-05a108651434)

Running the Docker Image Locally

To test the image locally, you can run the following command:
```
docker run -p 80:80 pradeep051/react-todo-app:latest
```

# Deploying to Kubernetes

  Once the Docker image is built, you can deploy it using MicroK8s.

  Create a deployment.yaml file in the root directory with the following content:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: react-todo-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: react-todo-app
  template:
    metadata:
      labels:
        app: react-todo-app
    spec:
      containers:
      - name: react-todo-container
        image: pradeep051/react-todo-app:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: react-todo-service
spec:
  selector:
    app: react-todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP

```

# Deploying the Application

 Apply the deployment configuration using the following command:
```
microk8s kubectl apply -f deployment.yaml
```
 Accessing the Application

 To access the application, set up port-forwarding with the following command:
```
microk8s kubectl port-forward service/react-todo-service 8080:80
```
 # Now open your web browser and navigate to http://localhost:8080 to view the application.

 ![image](https://github.com/user-attachments/assets/e2907541-bd5e-44d3-97d7-8c7a2670cc68)


Viewing the Kubernetes Dashboard

To monitor your Kubernetes cluster and deployed applications, you can access the Kubernetes dashboard.

If you haven't enabled the Kubernetes dashboard yet, you can do so by running:
```
microk8s enable dashboard
```
Once the dashboard is enabled, you can access it by running:

```
microk8s dashboard-proxy
```
This command will provide you with a URL, typically something like http://127.0.0.1:10443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/. Open this URL in your web browser to view the dashboard.

# Cleanup

To remove the deployed application, run:
```
microk8s kubectl delete -f deployment.yaml
```
If you need to stop MicroK8s, execute:
```
microk8s stop
```

#Conclusion

You have successfully built a Docker image for a React application and deployed it on MicroK8s. If you have any questions or need further assistance, feel free to reach out or create an issue in this repository












   

