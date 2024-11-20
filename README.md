 # EX 4 SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
 ```
Reg no: 212223220032
Name: HARSETHA J
```
  ## AIM
       To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT
This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.

## ALGORITHM
#### Step 1: Launch Two EC2 Instances in Different Availability Zones
Go to the EC2 service in the AWS Management Console.</BR>
Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.</BR>
Assign each instance a security group that allows NFS access on port 2049.</BR>

### Step 2: Set Up Security Group for EFS
Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.</BR>
Attach this security group to the EFS file system to permit access from both instances.</BR>

#### Step 3: Create an EFS File System
In the AWS Console, navigate to the EFS service and select Create file system.</BR>
Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.</BR>
Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).</BR>

#### Step 4: Configure EC2 Instances to Access EFS
## COMMANDS
### EC2 Instance 1
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```

### EC2 Instance 2
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  # Verify shared access by reading content created in Instance 1
```
## OUTPUT

### Both EC2 instances showing EFS mounting. 

![386965681-c509af1a-92eb-45bc-bb31-9e0dc7174233](https://github.com/user-attachments/assets/6b12be94-affb-4af0-b3c1-be792204c1bb)

![386867742-b9f9af9d-9d66-46fd-9c0c-2344c807e401](https://github.com/user-attachments/assets/8e9f81a1-2de5-44eb-92c5-bc34a900dc05)

### The creation of a file on Instance 1.

![388009581-a833ce93-974a-49cf-8fdd-948941477eb6](https://github.com/user-attachments/assets/9639a26d-d394-40e3-b18b-23a5a93b88a8)

### The display of that file’s contents on Instance 2 to verify shared access

![388009634-c31e323d-2485-4781-a744-9bfff9c80e9f](https://github.com/user-attachments/assets/e98d14b5-2290-467d-b120-6eaede6898a6)

## RESULT
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing. 

  


