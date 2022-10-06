# TASK1
<h3>Creating ubuntu VM</h3>
-Created an Ubuntu VM and Connected it to Internet.
-Created a vim file.sh inside of Ubuntu Machine And using #!/bin/bash in order to automate all installations that were desired by using sudo command.
-Created a test vim. file.sh by using #!/bin/bash inside of Ubuntu in order to check out the versions of Installations to be make sure that they are installed.

# TASK2

# Launch-Template

# <h3>Creating Launch Template</h3>
- Launch template name: Task2EC2
- Quick start — Ubuntu 20.04
- Instance type — t2.micro
- Key pair name — bastion
- Network settings — subnet-us-east-1a
- Firewall — create a security group --Task2_Sg --> sg-0136cad4c4cf9d3ee
- inbound rules—add rules_
- Type-SSh—— port range-22——source type-anywhere-IPv4_
- Type-Custom TCP——port range-80———source type-Anywhere-IPv4_
- Advanced network configuration — auto-assign public ip (enable)
- Advanced details-user data
    ```
    #!/bin/bash
    apt update -y
    apt install nginx -y
    cd /var/www/html
    git clone https://github.com/zce/html5up.git
    cp -r html5up/arcana/* .
    service nginx start
    ```
# <h3>Auto Scaling Groups</h3>
- Name — Task1AutoScalingGroup
- Launch Template — Task2EC2
- Next
- Vpc — default
- Availability zones and subnets — us-east-1a, us-east-1b
- Load Balancing — Attach to a new load balancer
- Application Load Balancer
- Load balancer name—Task1LoadBalancer
- Load balancer scheme—Internet-facing
- Port-80——>>Default routing(forward to)—create target group—>new target group  name-Task1TargetGroup
- Desired capacity-3—>Minimum capacityi-3——>Maximum capacity-5
- Scaling policies—Target tracking scaling policy—>Target value-30
- _For verify—Load Balancers—click Task1LoadBalancer —->>DNS name copy and paste on chrome_


![proofOfArnaca](https://user-images.githubusercontent.com/64179710/194417217-ebb1d399-4023-4a79-a241-9f2975e3651a.png)


