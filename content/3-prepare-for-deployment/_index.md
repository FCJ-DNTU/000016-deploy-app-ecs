+++
title = "Prepare for Deployment"
date = 2024
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

To deploy a Node.js and Nginx with React application, we need to prepare Docker images for both Node.js and Nginx React. The Docker image functions like built and packaged code (in the past, the code would be built and then compressed).

At the end of the previous lesson, we built images for both Node.js and Nginx React, and the Node.js Docker image was able to work properly with ECS Service. However, the Nginx React image needs some adjustments. So in this section, we will rebuild the image for Nginx React.

![applications-architecture](/images/3-prepare-for-deployment/applications-architecture.png)

#### Contents

1. [Push Docker image to ECR](3.1-push-image-to-ecr/)
2. [Push Docker image to Dockerhub](3.2-push-image-to-dockerhub/)
