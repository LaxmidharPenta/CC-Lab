Experiment 1: How do you launch an EC2 instance using the AWS Free Tier, configure security groups, and connect to it using SSH?

Objective: 
To learn how to launch and configure a virtual server using Amazon EC2, set up security groups, and connect to the instance using SSH.
Outcome:
Students will be able to launch an EC2 instance, configure its security settings, and establish a secure connection to the instance using SSH.
Step-by-Step Procedure:
1.Open a browser and go to https://aws.amazon.com/.
2.Sign in to the AWS Management Console using your Free Tier account.
3.In the search bar, type EC2 and click on EC2 to open the EC2 Dashboard.
4.Click on Launch Instance.
5.Under the “Name and Tags” section, give a name to your instance (e.g., MyEC2Instance).
6.Choose an Amazon Machine Image (AMI): Select Amazon Linux 2 AMI (Free Tier eligible).
7.Choose an instance type: Select t2.micro (Free Tier eligible).
8.Scroll down and under Key pair (login), click Create new key pair.
oEnter a key pair name.
oSelect .pem file format and click Create key pair.
oSave the .pem file securely.
9.In the Network settings, click Edit to modify the security group:
oClick Add rule.
oType: SSH, Protocol: TCP, Port Range: 22, Source: My IP.
10.Click Launch Instance.
11.Go to the Instances page and wait for the instance to reach the running state.
12.Copy the Public IPv4 address of your instance.
13.Open a terminal or command prompt on your computer.
14.Change the permission of the key file:
chmod 400 your-key-name.pem
15.Connect to the instance using SSH:
ssh -i "your-key-name.pem" ec2-user@<your-ec2-public-ip>

Experiment 2: Creating an Amazon SQS Queue and Sending Messages using AWS CLI

Objective:
To understand how to create and manage Simple Queue Service (SQS) queues and send messages using the AWS CLI.
Outcome:
Students will learn to create an SQS queue and use AWS CLI commands to send and manage messages.
Step-by-Step Procedure:
1.Install AWS CLI from https://aws.amazon.com/cli/ if not already installed.
2.Open a terminal or command prompt.
3.Configure AWS CLI with your credentials:
aws configure
Enter Access Key ID
Enter Secret Access Key
Enter AWS Region (e.g., us-east-1)
Enter output format as json
4.Create a new SQS queue:
aws sqs create-queue --queue-name MyQueue
5.List all available queues to verify:
aws sqs list-queues
6.Get the URL of the created queue:
aws sqs get-queue-url --queue-name MyQueue
7.Copy the queue URL from the output.
8.Send a message to the queue:
aws sqs send-message --queue-url <your-queue-url> --message-body "Hello from Cloud Lab"
9.Receive the message from the queue:
aws sqs receive-message --queue-url <your-queue-url>


Experiment 3: Creating an SNS Topic, Subscribing Email, and Publishing a Message
Objective:
To demonstrate how to use Amazon Simple Notification Service (SNS) to create topics, subscribe endpoints, and publish messages.
Outcome:
Students will be able to create an SNS topic, subscribe an email to it, and send notifications using the AWS Management Console or AWS CLI.
Step-by-Step Procedure:
1.Sign in to the AWS Management Console at https://aws.amazon.com/.
2.Search for SNS in the services menu and open Simple Notification Service.
3.Click Topics → Create topic.
4.Select Standard type.
5.Provide a topic name (e.g., MyTopic) and click Create topic.
6.After creation, click on the topic name to open it.
7.Click Create subscription.
8.Set the following:
oProtocol: Email
oEndpoint: Your valid email address
9.Click Create subscription.
10.Check your email inbox and confirm the subscription using the link provided in the AWS email.
11.Go back to the SNS topic and click Publish message.
12.Enter a subject (e.g., "Test Notification").
13.Enter a message body (e.g., "This is a test message from AWS SNS").
14.Click Publish message.
15.Check your email inbox to confirm the receipt of the message.

Experiment 4: Creating an S3 Bucket and Uploading Files 
Objective:
To understand how to create an Amazon S3 bucket and upload files to it using the AWS Management Console.
Outcome:
Students will be able to create and configure an S3 bucket and successfully upload objects such as text, images, or other files to it.
Step-by-Step Procedure:
1.Log in to your AWS Management Console at https://aws.amazon.com/.
2.In the Services menu, search for and open S3.
3.Click on Create bucket.
4.Enter a unique bucket name (e.g., my-cloud-lab-bucket).
5.Choose an AWS Region (e.g., us-east-1).
6.Leave other settings as default and click Create bucket.
7.After the bucket is created, click on the bucket name to open it.
8.Click on the Upload button.
9.Click Add files to select files from your computer (e.g., .txt, .jpg).
10.Click Upload to add the files to the bucket.
11.Once uploaded, click on any file name to view details and access permissions.

Experiment 5: Setting Up a WordPress Website Using Amazon Lightsail Free Tier
Objective:
To learn how to deploy a WordPress website using Amazon Lightsail's Free Tier instance and access it via a browser.
Outcome:
Students will be able to launch a Lightsail instance, install WordPress, and manage a basic web application hosted in the cloud.
Step-by-Step Procedure:
1.Log in to your AWS account at https://aws.amazon.com/.
2.Search for and open Amazon Lightsail from the services menu.
3.Click Create Instance.
4.Under Platform, choose Linux/Unix.
5.Under Blueprint, choose WordPress.
6.Choose the Free Tier eligible instance plan ($3.50 USD/month).
7.Provide a name for your instance (e.g., wordpress-site).
8.Click Create instance.
9.Wait for the status to show Running.
10.Click the instance name to open its dashboard.
11.Under Connect, copy the public IP address of the instance.
12.Open a browser and enter the public IP in the address bar to access the WordPress site.
13.To log in, append /wp-admin to the IP (e.g., http://<public-ip>/wp-admin).
14.Use the default username (usually user) and find the password in the Lightsail dashboard under Connect using SSH (use SSH and run cat bitnami_application_password).
15.After logging in, customize the WordPress site from the admin dashboard.

Experiment 6: Configuring AWS Backup to Automatically Back Up an EC2 Instance and Restore It
Objective:
To configure automatic backups of an EC2 instance using AWS Backup and learn how to restore data when required.
Outcome:
Students will be able to set up backup plans, assign resources (EC2 instances), and perform restoration using AWS Backup.
Step-by-Step Procedure:
1.Log in to the AWS Management Console.
2.Go to AWS Backup from the services menu.
3.Click Create Backup Plan.
4.Choose Build a new plan.
5.Provide a name for your backup plan (e.g., EC2BackupPlan).
6.Under Backup rule name, enter a name (e.g., DailyBackup).
7.Set backup frequency to Daily and retention period (e.g., 7 days).
8.Choose or create a backup vault (e.g., MyBackupVault).
9.Click Create plan.
10.After creating the plan, go to the plan and click Assign resources.
11.Set a resource assignment name (e.g., AssignEC2Instance).
12.Choose the resource type as EC2 and select the instance ID from the list.
13.Click Assign resources.
14.Wait for the backup job to be triggered (manually or automatically based on schedule).
15.To restore:
oGo to Backup vaults > your vault.
oFind the completed backup.
oClick Restore, select restore options, and click Restore backup.
oA new EC2 instance will be created from the backup.

Experiment 7: Launch an RDS Instance, Connect via MySQL Workbench, and Create a Database
Objective:
To learn how to create a managed relational database using Amazon RDS and access it using MySQL Workbench.
Outcome:
Students will be able to launch an RDS MySQL instance, connect to it remotely, and create a custom database.
Step-by-Step Procedure:
1.Log in to the AWS Console and go to Amazon RDS.
2.Click Create database.
3.Choose Standard Create.
4.Engine type: Select MySQL.
5.Use Free Tier template.
6.Set DB instance identifier (e.g., mydbinstance), master username, and password.
7.In Connectivity, ensure “Public access” is enabled.
8.Choose default VPC and create new security group.
9.Click Create database and wait for the status to become Available.
10.Note the endpoint of the RDS instance.
11.Open MySQL Workbench.
12.Create a new connection:
oHostname: RDS endpoint
oPort: 3306
oUsername: Your master username
oPassword: Your master password
13.Click Test Connection and then OK.
14.After connecting, execute:
CREATE DATABASE labdb;


Experiment 8: Create a DynamoDB Table and Perform Insert, Retrieve, and Delete Using AWS CLI
Objective:
To understand how to manage NoSQL data using Amazon DynamoDB and the AWS CLI or SDK.
Outcome:
Students will be able to create tables, insert items, retrieve them, and delete them using command-line tools or scripts.
Step-by-Step Procedure:
1.Open your terminal and configure AWS CLI:
aws configure
2.Create a DynamoDB table:
aws dynamodb create-table \
  --table-name StudentRecords \
  --attribute-definitions AttributeName=StudentID,AttributeType=S \
  --key-schema AttributeName=StudentID,KeyType=HASH \
  --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1
3.Wait for the table to become ACTIVE.
4.Insert an item:
aws dynamodb put-item \
  --table-name StudentRecords \
  --item '{"StudentID": {"S": "101"}, "Name": {"S": "John"}, "Dept": {"S": "CSE"}}'
5.Retrieve the item:
aws dynamodb get-item \
  --table-name StudentRecords \
  --key '{"StudentID": {"S": "101"}}'
6.Delete the item:
aws dynamodb delete-item \
  --table-name StudentRecords \
  --key '{"StudentID": {"S": "101"}}'


Experiment 9: Analyze an Image Using Amazon Rekognition for Object Detection
Objective:
To use Amazon Rekognition to perform object and scene detection on an image using AWS CLI.
Outcome:
Students will be able to analyze visual content in an image using Rekognition and retrieve detected labels with confidence scores.
Step-by-Step Procedure:
1.Upload an image to an S3 bucket.
2.Install and configure AWS CLI:
aws configure
3.Run the following command to detect labels in the image:
aws rekognition detect-labels \
  --image "S3Object={Bucket=my-bucket,Name=my-image.jpg}" \
  --max-labels 10 \
  --min-confidence 70
4.Analyze the JSON output to view the detected objects with confidence scores.

Experiment 10: Create a Jupyter Notebook Instance in SageMaker and Train a Basic ML Model
Objective:
To launch a SageMaker Jupyter notebook instance and execute Python code to train a simple machine learning model.
Outcome:
Students will be able to build and train a basic classifier in a managed notebook environment using AWS SageMaker.
Step-by-Step Procedure:
1.Go to Amazon SageMaker in the AWS Console.
2.Select Notebook instances → Create notebook instance.
3.Enter a name (e.g., ml-notebook).
4.Choose instance type (e.g., ml.t2.medium – Free Tier eligible).
5.Create a new IAM role with AmazonS3FullAccess.
6.Click Create notebook instance.
7.Wait for the instance to become InService.
8.Click Open Jupyter.
9.Create a new notebook using Python 3 (Data Science) kernel.
10.In the notebook, paste the following example code:
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score
data = load_iris()
X_train, X_test, y_train, y_test = train_test_split(data.data, data.target)
model = RandomForestClassifier()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
accuracy = accuracy_score(y_test, predictions)
print(f"Model Accuracy: {accuracy}")
11.Run the code and note the printed model accuracy.
DESCRIPTION
EXP-01
An Amazon EC2 (Elastic Compute Cloud) instance is a virtual server in Amazon’s cloud that 
provides scalable computing power for running applications. It allows users to choose the operating 
system, CPU, memory, storage, and network configurations according to their needs. EC2 instances 
can be quickly launched, stopped, or terminated, giving flexibility to handle varying workloads 
efficiently. They are commonly used for hosting websites, running applications, data analysis, and 
machine learning. With different pricing models such as On-Demand, Reserved, and Spot Instances,
EC2 helps optimize costs. It also offers strong security through AWS Identity and Access 
Management (IAM), key pairs, and security groups, making it a reliable and customizable cloud 
computing service.
EXP-02
An Amazon S3 (Simple Storage Service) bucket is a cloud-based storage service provided by AWS 
that allows users to store and retrieve any amount of data at any time. It works like an online folder 
where you can save files such as documents, images, videos, or backups. Each S3 bucket has a 
unique name and can hold an unlimited number of objects. It is highly durable, scalable, and secure,
ensuring that your data is always available and protected. Users can control access to their data 
using permissions, bucket policies, and AWS Identity and Access Management (IAM). S3 is 
commonly used for data backup, website hosting, content distribution, and big data analytics. Its 
pay-as-you-go pricing model and integration with other AWS services make it a flexible and cost￾effective storage solution.
EXP-03
An Amazon SQS (Simple Queue Service) queue is a fully managed message queuing service
provided by AWS that enables decoupling and communication between different parts of a 
distributed system. It allows applications or microservices to send, store, and receive messages 
asynchronously, ensuring smooth data flow even if some components are temporarily unavailable. 
SQS helps improve reliability and scalability by preventing message loss and handling large 
volumes of requests efficiently. There are two types of queues: Standard Queues (for high 
throughput and best-effort ordering) and FIFO Queues (for first-in-first-out order and exactly-once
processing).
EXP-04
Amazon SNS (Simple Notification Service) is a fully managed messaging and notification service
provided by AWS that allows applications, services, and users to communicate with each other 
easily. It uses a publish-subscribe (pub/sub) model, where a publisher sends messages to a topic, 
and all subscribers to that topic automatically receive the messages.
SNS is designed for real-time, push-based message delivery, meaning messages are instantly sent to
subscribers without them having to request or poll for updates. Subscribers can receive messages 
through various protocols such as email, SMS, HTTP/S endpoints, AWS Lambda functions, or SQS 
queues.
It is widely used for alerting systems, monitoring notifications, and event-driven applications. For 
example, it can notify system administrators via email when an application fails, or it can trigger 
AWS Lambda functions when a new message arrives.
EXP-05
Setting up a WordPress website using Amazon Lightsail involves launching a simplified, pre￾configured virtual server that comes with WordPress already installed. Lightsail is designed to make
deploying websites easy by bundling compute power, storage, and networking into a single package
with straightforward pricing. When you create a WordPress instance on Lightsail, AWS provides a 
managed environment that includes the web server, database, and necessary software, so you don’t 
have to configure these components manually.
This setup enables you to quickly deploy a fully functional WordPress site with options for 
managing DNS, attaching static IP addresses, and creating automatic backups. Lightsail also offers 
an intuitive web-based console and CLI tools to manage your instance. Because it abstracts much of
the underlying infrastructure complexity, Lightsail is ideal for users who want to launch and 
maintain WordPress websites with minimal technical overhead. Overall, Amazon Lightsail 
streamlines the process of hosting WordPress sites by offering a simple, cost-effective, and scalable
solution.
EXP-06
AWS Backup is a fully managed service that enables you to automate and centrally manage backups
across AWS resources such as EC2 instances, EBS volumes, RDS databases, and more. When used 
with EC2, AWS Backup automatically creates and manages backups of the instance’s attached EBS 
volumes, ensuring data protection without manual effort. These backups, stored as snapshots, can be
used to restore the entire EC2 instance or individual volumes if needed.
The service allows you to define backup plans with schedules, retention policies, and lifecycle 
rules, ensuring that backups occur automatically and are retained for the required period. It also 
provides encryption, access control, and monitoring features to maintain data security and 
compliance.
In short, AWS Backup offers a centralized, automated, and reliable way to protect EC2 data, 
reducing the risk of data loss and simplifying disaster recovery operations.
EXP-07
Amazon RDS (Relational Database Service) provides managed relational databases, including 
MySQL, in the cloud. Connecting to an RDS MySQL instance via MySQL Workbench involves 
using the database’s endpoint, port, and authentication credentials to access it remotely. The RDS 
instance must be configured to allow connections—typically by making it publicly accessible or 
accessible within a VPC, and by setting appropriate security group rules to permit inbound MySQL 
traffic on port 3306. This setup enables users to manage and interact with their cloud-hosted 
MySQL databases through the familiar MySQL Workbench interface, offering the same capabilities 
as with traditional on-premises databases but with the benefits of AWS’s managed infrastructure.
EXP-08
Amazon DynamoDB is a fully managed NoSQL database service that stores data in tables with 
items identified by primary keys. Creating a DynamoDB table involves defining its schema, 
including primary key attributes, and configuring its throughput capacity. Data operations such as 
inserting, retrieving, and deleting items are performed by specifying the table and the primary key 
values. Using the AWS CLI, these operations allow you to manage your DynamoDB tables 
programmatically—enabling efficient, scalable, and flexible data handling without the need for 
complex infrastructure management.
EXP-09
Amazon Rekognition is a powerful AWS service that uses machine learning to analyze images and 
videos. For object detection, Rekognition can automatically identify and locate multiple objects, 
scenes, and activities within an image. It recognizes a wide variety of objects—like cars, people, 
animals, furniture, and more—by returning labels with confidence scores and bounding boxes 
showing where each object appears in the image.
This makes it useful for applications like content moderation, inventory tracking, security 
monitoring, or any scenario where understanding the visual content of images is important. The 
service is fully managed and scales automatically, allowing developers to easily integrate object 
detection capabilities into their apps without needing deep expertise in computer vision or machine 
learning.
EXP-10
Amazon SageMaker is a fully managed service that enables developers and data scientists to build, 
train, and deploy machine learning models at scale. Creating a Jupyter Notebook instance in 
SageMaker provides an interactive environment where you can write and run code to prepare data, 
build models, and perform experiments—all without managing the underlying infrastructure.
Once the notebook instance is set up, you can use it to develop and train basic machine learning 
models by leveraging built-in algorithms or custom code. SageMaker handles the heavy lifting of 
resource provisioning, so you can focus on writing code for data preprocessing, model training, and 
evaluation. The platform also supports easy deployment of trained models for real-time predictions.



