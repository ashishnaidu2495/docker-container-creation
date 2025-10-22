# MyToDoApp deployed on the redhat openshift
A simple to-do application deployed on Red Hat OpenShift using a Docker image hosted on Quay.io.

🚀 Overview
This repository contains the source code for mytodoapp and documents the complete process from building a container image to deploying the application on an OpenShift cluster. The deployment leverages an image pulled directly from the Quay.io container registry.

🛠️ Technology Stack
Application: (Specify your application framework/language here, e.g., Node.js/Express, Python/Django, Java/Spring Boot)

Containerization: Docker

Container Registry: Quay.io

Deployment Platform: Red Hat OpenShift

📦 Deployment Process
The application's deployment was achieved through a three-step process: Container Image Creation, Pushing to Quay.io, and Deployment on OpenShift.

1. 🐳 Container Image Creation (Docker)
The application was containerized using Docker. The steps involved:

Writing a Dockerfile: A file was created to define the environment, dependencies, and command to run the application.

Building the Image: The Docker image was built locally using the Dockerfile.

Bash

docker build -t mytodoapp:latest .
Testing the Image (Optional but Recommended): The image was run locally to ensure the application starts correctly.

Bash

docker run -p 8080:8080 mytodoapp:latest
(Adjust the port 8080 to your application's actual listening port.)

2. 🚢 Pushing to Quay.io
Once the image was successfully built, it was tagged and pushed to the Quay.io container registry to make it accessible for the OpenShift deployment.

Tagging the Image: The image was tagged with the full repository path for Quay.io.

Bash

docker tag mytodoapp:latest quay.io/<YOUR_QUAY_USERNAME>/mytodoapp:latest
Logging In: Authentication with Quay.io was performed using the Docker CLI.

Bash

docker login quay.io
Pushing the Image: The tagged image was uploaded to the Quay.io repository.

Bash

docker push quay.io/<YOUR_QUAY_USERNAME>/mytodoapp:latest
3. ☁️ Deployment on Red Hat OpenShift
The final step was deploying the containerized application onto the Red Hat OpenShift cluster.

Accessing the Cluster: Logged into the OpenShift cluster using the oc CLI tool or the web console.

Creating a New Application/Deployment: OpenShift was instructed to pull the image from Quay.io and create a deployment. This typically involves:

Creating a new Project (if necessary).

Creating a Deployment/DeploymentConfig referencing the Quay.io image:

Bash
<img width="1920" height="1080" alt="Screenshot 2025-10-22 174402" src="https://github.com/user-attachments/assets/8a06a2fe-0051-44f0-8710-c5188bf66742" />

oc new-app quay.io/<YOUR_QUAY_USERNAME>/mytodoapp:latest
Exposing the Service (Creating a Route) to make the application accessible externally:

Bash

oc expose service mytodoapp
<img width="1920" height="1080" alt="Screenshot 2025-10-22 174416" src="https://github.com/user-attachments/assets/99b2205c-58f7-4828-ace0-fd2c83bbda48" />

This repository is a sample Node.js application for Docker's documentation.

