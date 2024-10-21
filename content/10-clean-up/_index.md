+++
title = "Clean Up Resources"
date = 2024
weight = 10
chapter = false
pre = "<b>10. </b>"
+++

### Delete Elastic Container Service

- Search for and select **Elastic Container Service**.

![10.1](/images/10-clean-up/10.1.png)

- Choose **FCJ-Lab-cluster**.

![10.2](/images/10-clean-up/10.2.png)

In the **Services** section:

- Select the two running services.
- Click **Delete service**.

![10.3](/images/10-clean-up/10.3.png)

- Enter `delete`.
- Click **Delete**.

![10.4](/images/10-clean-up/10.4.png)

After cleaning up the running services, we will proceed to delete the Cluster:

- Click **Delete cluster**.

![10.5](/images/10-clean-up/10.5.png)

- Enter `delete FCJ-Lab-cluster`.
- Click **Delete**.

![10.6](/images/10-clean-up/10.6.png)

Next, we will clean up the task definitions:

- Select **Task definitions**.
- Choose the task you want to delete.

![10.7](/images/10-clean-up/10.7.png)

- Continue following the instructions:
  - Select the task definition.
  - Click **Action**.
  - Choose **Deregister**.

![10.8](/images/10-clean-up/10.8.png)

Repeat the process to delete the remaining task.

![10.9](/images/10-clean-up/10.9.png)

- Follow the instructions.

![10.10](/images/10-clean-up/10.10.png)

You have successfully deleted the ECS and its services.

### Clean Up Elastic Container Registry

On the AWS Console interface:

- Search for and select **Elastic Container Registry**.

![10.11](/images/10-clean-up/10.11.png)

You will see the two repositories we created earlier:

- Select **fcjresbar-be**.
- Click **Delete**.

![10.12](/images/10-clean-up/10.12.png)

- Confirm the **Delete** action.

![10.13](/images/10-clean-up/10.13.png)

Similarly, perform the same for the other repository:

- Select **fcjresbar-fe**.
- Click **Delete**.

![10.14](/images/10-clean-up/10.14.png)

- Confirm the **Delete** action.

![10.15](/images/10-clean-up/10.15.png)

### Delete Load Balancer

- Search for and select **Load Balancer**.

![10.16](/images/10-clean-up/10.16.png)

- Choose the Load Balancer you created.
- Click **Action**.
- Select **Delete load balancer**.

![10.17](/images/10-clean-up/10.17.png)

- Enter **confirm**.
- Click **Delete**.

![10.18](/images/10-clean-up/10.18.png)

### Clean Up Target Groups

In the left panel:

- Select **Target Groups**.
- Choose the target group you created.
- Click **Action**.
- Select **Delete**.

![10.19](/images/10-clean-up/10.19.png)

### Clean Up RDS

On the AWS Console interface:

- Search for and select **RDS**.

![10.20](/images/10-clean-up/10.20.png)

- Select **Databases**.
- Choose the RDS instance you created.
- Click **Action**.
- Select **Delete**.

![10.21](/images/10-clean-up/10.21.png)

- Check **I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.**
- Enter `delete me`.
- Click **Delete**.

![10.22](/images/10-clean-up/10.22.png)

#### NAT Gateway

- Search for and select `NAT gateway`

![10.23](/images/10-clean-up/10.23.png)

- Select the NAT Gateway you created
- Click on **Action**
- Choose **Delete NAT gateway**

![10.24](/images/10-clean-up/10.24.png)
