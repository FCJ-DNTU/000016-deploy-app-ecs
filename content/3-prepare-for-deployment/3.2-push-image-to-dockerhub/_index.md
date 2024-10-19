+++
title = "Push image to Dockerhub"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Push the Image to Dockerhub

In the previous step, we successfully pushed the image to ECR, and in this step, we will push the image to Dockerhub.

- Log out (remove ECR credentials) from Docker using `docker logout`.
- Then log in with `docker login -u "your-docker-username"`.

![3.2.1](/images/3-prepare-for-deployment/3.2.1.png)

List the existing images, and now we won’t rebuild the image but just add another tag for Dockerhub. After tagging, list the images again, and you will see the new tag has been added.

![3.2.2](/images/3-prepare-for-deployment/3.2.2.png)

Now, proceed to push this image to Dockerhub.

![3.2.3](/images/3-prepare-for-deployment/3.2.3.png)

And check the result.

![3.2.4](/images/3-prepare-for-deployment/3.2.4.png)

So, we have successfully pushed the image to both ECR and Dockerhub. Now you can use the image from any registry to deploy the Frontend Service.






