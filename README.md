# Jenkins-deploy

This Project deploys a simple hello-world image to EKS cluster.

A jenkins pipeline project is created with this SCM as source for Jenkinsfile.

The jenkins file contains a pipeline with the following steps

1. Clone the git repo
2. Build the simple container image from Dockerfile in the repo
3. Push the Image to ECR repo
4. Deploy to the EKS cluster the image from the ECR repo

The deployment.yml contains the k8s pod deployment configuration

The Jenkins-log file has the pipeline execution log showing successful deployment to EKS.



