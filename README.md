# AWS three-tier-architecture-diagram

![alt_text](https://github.com/Ricardo-Suarez-Chacon/three-tier-architecture-diagram/blob/main/AWS%20three-tier%20architecture.png "image_tooltip")

**_Three-tier architecture diagram, is the final assignment of the AWS Cloud Technical Essentials course taught by Amazon Web Services at www.coursera.org._**

This three-tier architecture diagram is hosted in one region, with two availability zones each, and as the name suggests, three tiers, each with its own security group, load balancer and auto-scaling.

The region hosts the solution, and has defined permissions, security groups, defined through the IAM service. There are three security groups defined to cover the three levels that make up the solution.



* Web Services
* Application Services
* Database Services

The S3 service hosts the media files generated and consumed by the users and CloudWatch is in charge of managing the alarms and triggers needed to dynamically scale the site as needed according to the number of converged users and/or computational load required by the solution.

The backbone of the automatic scaling process lies in the web and application layers in the EBL (Elastic Load Balancing) and EC2 Auto Scaling services, which manage the infrastructure resources needed for these two layers, in the database layer this task is managed by the Amazon RDS (Amazon Relational Database Service), which is responsible for keeping the databases synchronized in each availability zone. 

The communication to the Internet is through the gateway and there the information flow from and to the user is routed through the first layer which is public. This web application layer serves the user interface through a web interface, which it receives and delivers to the end user.

The application layer is hosted in another group of EC2 instances, the requests made in the web layer are resolved at this level, which has private sub-networks for each group of instances per availability zone. This layer communicates with the web layer and the database layer to fulfill its objective of supporting the application's own logic and processes.

The database layer has its own scaling and synchronization service through RDS and only maintains communication with the application layer. It has its own subnets in each zone and as mentioned before its own security group. 

This architecture allows an adequate balance between service availability, security, and price due to keeping the infrastructure hosted in one region and two availability zones. 
