# Sparta App Auto Scaling Setup

To complete this task for the Sparta app, you will need the same instance used previously for the Sparta application, or you can create a new instance and run the Sparta app script. The instructions for the script are included in another file.

## The Overview

We need to create an AMI of the app. Once we have the AMI, we will create a launch template and test the launch template. This will allow AWS to automatically create an Auto Scaling Group.

We also need to create a policy so that when CPU usage reaches 50%, scaling will occur.  
The policy settings are:

- Minimum instances: 2  
- Maximum instances: 3  
- Desired instances: 2  

This means there will always be at least 2 instances running, with the ability to scale up to 3 instances when needed. The desired value is the recommended number of instances to run normally.

All instances will be created in the Ireland region, which has been used for previous instances.

## Scaling

1. There are two types of scaling: horizontal scaling (in and out) and vertical scaling (up and down). We will use horizontal scaling because we will have multiple instances. When more power is needed, AWS will create more instances, and when demand decreases, AWS will scale back in.

2. Vertical scaling is used when there is only one instance. The instance becomes larger or smaller depending on demand.

3. Return to AWS to continue the setup.

## Creating a Launch Template

1. Go to Launch Templates in EC2.

2. Click the orange "Create launch template" button.

3. Enter a launch template name, for example: `jonathan-launch-template`.

4. Add a short description explaining that it is a launch template.

5. Choose the AMI you want to include in the launch template.

6. Search for your launch image under Amazon Machine Images.

7. Select the instance type you want to use.

8. Choose your key pair.

9. You do not need to change the network settings, but you must select your security group.

10. Scroll down to Advanced Details and go to the bottom to find "User data".  
Create a script and paste the following into the user data box:


````
#! bin/bash
sleep 10
cd /home/ubuntu
cd se-sparta-test-app
cd app
sudo npm install
pm2 start app.js
````



11. Click Create.

12. Go to Actions.

13. Check that all details are correct, including your instance type, security group, and key pair. Then click Launch instance.

14. Go to the Instance Summary page and copy the public IP address.  
It may take some time to load. You might see a bad gateway message at first, so refresh the page a few times.

If everything works correctly, the Sparta app should appear.

(This completes the first set of steps.)

## Auto Scaling

Stay in EC2.

1. Go to Auto Scaling Groups.

2. Click the orange "Create Auto Scaling group" button.

3. Enter a name for your Auto Scaling group, for example:  
"se-jonathan-sparta-app-asg"

4. Specify the launch template you created earlier.

5. Click Next.

6. When you reach Instance Launch Options, check that the settings look correct.

7. Under Availability Zones and subnets, select:
   - eu-west-1a  
   - eu-west-1b  
   - eu-west-1c

8. For Availability Zone distribution, choose Balanced best effort.

9. Under Load Balancing, select Attach to a new load balancer.

10. Choose Application Load Balancer from the two available types.

11. For the load balancer name, attach 1b to the end so it matches your Auto Scaling group name.

12. For the scheme, select Internet-facing.

13. For Listener and routing, choose Default routing and create one if it is not already created. Add "tg" at the end of the name.

14. For VPC Lattice options, select No VPC and use the default settings.

15. Turn on health checks.

16. Keep the health check grace period at 300 seconds.

## Configure Group Size and Scaling

1. Set the group size:
   - Desired capacity: 2  
   - Minimum capacity: 2  
   - Maximum capacity: 3  

2. Under Automatic Scaling, choose Target Tracking.

3. Name the scaling policy something like `cpu-usage-scaling-policy`.

4. For Instance Maintenance Policy, select No policy.

5. Leave the remaining settings as default and click Next.

## Tags

1. Under Tags, enter:
   - Key: Name  
   - Value: se-jonathan-asg-instance  

2. Click Add tag.

3. Click Review.

4. If everything looks correct, click Create Auto Scaling group.

## Testing the Setup

1. Since the minimum number of instances is set to 2, AWS should create two instances.

2. Copy the public IP address of each instance and open them in a web browser. The Sparta app should appear.

3. However, the correct way to access the app is through the load balancer.

4. Go to Load Balancers, select your load balancer, and copy the DNS name.

5. Paste the DNS name into your browser's address bar.

## Final Test

1. Go to Instance Manager.

2. Terminate one instance.

3. The Auto Scaling Group will detect that the number of instances has dropped below the minimum of 2.

4. AWS will automatically create a new instance to replace the terminated one.

5. The terminated instance will show as unhealthy while the new one is being created.
