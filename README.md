# Coworking Analytics Application

This project deploys a Python-based analytics service that generates usage reports from a PostgreSQL database. The application is designed using a containerized microservices architecture and deployed using AWS and Kubernetes.

The analytics service is packaged into a Docker image using a lightweight Python base image to ensure consistent behavior across development and deployment environments. Docker enables the application to be built, tested, and deployed in a repeatable and portable manner.

AWS CodeBuild is used to implement a continuous integration pipeline. When changes are pushed to the source repository, CodeBuild pulls the code, builds the Docker image using the provided Dockerfile, and pushes the image to Amazon Elastic Container Registry (ECR).

Amazon ECR acts as the container registry for storing versioned Docker images of the analytics application. These images are later referenced by Kubernetes during deployment.

Kubernetes is used to deploy and manage the analytics application. The deployment configuration defines the container image, exposed ports, and runtime configuration. A Kubernetes Service of type LoadBalancer is used to expose the application.

Application configuration values such as database host, username, database name, and port are stored in a Kubernetes ConfigMap. Sensitive information, such as the database password, is stored securely in a Kubernetes Secret and injected into the application at runtime.

To release a new version of the application, a developer pushes code changes to the repository. This triggers the CI pipeline to build a new Docker image and push it to ECR, after which the Kubernetes deployment can be updated to use the new image.

Due to AWS Udacity sandbox limitations, some build or runtime steps may be automatically stopped. However, the CI/CD configuration, Docker setup, and Kubernetes manifests are implemented according to best practices and meet the project requirements.

Webhook trigger test after disabling CloudWatch logs