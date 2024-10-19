+++
title = "Test Result"
date = 2024
weight = 9
chapter = false
pre = "<b>9. </b>"
+++

#### Observation

Before trying out the application, we should take a moment to observe the Services and Load Balancer.

- Select **frontend** service  to access its detail page.
- Select tab **Task**

Here, we can see that one task is running since it is managing one container (which is also running).

![9.1](/images/9-test-result/9.1.png)

Switching to the Logs tab, we can see that this service is generating logs normally.

![9.2](/images/9-test-result/9.2.png)

The backend behaves similarly.

![9.3](/images/9-test-result/9.3.png)

![9.4](/images/9-test-result/9.4.png)

Now, go to the **Load Balancer** interface, select **FCJ-Lab-alb**, and click on the **Resource map** tab.

![9.5](/images/9-test-result/9.5.png)

It can be seen that our system is functioning normally. Remember to copy the DNS of the Load Balancer.

#### Try Out the Application

Paste the Load Balancer's DNS into the search bar, press enter, and we will get the login interface.

![9.6](/images/9-test-result/9.6.png)

After logging in as a user with the User role, we will see the dashboard interface.

![9.7](/images/9-test-result/9.7.png)

Let’s check out some other pages.

![9.8](/images/9-test-result/9.8.png)

![9.9](/images/9-test-result/9.9.png)

Now, let’s try performing a function; here, I will create an order.

![9.10](/images/9-test-result/9.10.png)

After creating an order, we can see the details of that order.

![9.11](/images/9-test-result/9.11.png)

Log out and log in as an Admin user.

![9.12](/images/9-test-result/9.12.png)

Here is the Admin dashboard.

![9.13](/images/9-test-result/9.13.png)

In the orders page, we can see the order that we just created.

![9.14](/images/9-test-result/9.14.png)

Okay, our system is now functioning normally, from the Database Server to the Backend and Frontend.
