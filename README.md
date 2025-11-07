# ☁️ AWS Cloud Computing Experiments – Free Tier Labs

This repository contains detailed step-by-step AWS Cloud experiments demonstrating essential cloud services such as EC2, S3, RDS, DynamoDB, SNS, SQS, Rekognition, SageMaker, and more — all using the **AWS Free Tier**.

---

## 🧪 Experiment 1: Launch an EC2 Instance and Connect via SSH

### 🎯 Objective
To learn how to launch and configure a virtual server using Amazon EC2, set up security groups, and connect to the instance using SSH.

### 🏁 Outcome
Students will be able to launch an EC2 instance, configure its security settings, and establish a secure connection using SSH.

### ⚙️ Step-by-Step Procedure
1. Open [AWS](https://aws.amazon.com/) and sign in.
2. Navigate to **EC2 Dashboard** → Click **Launch Instance**.
3. Name your instance (e.g., `MyEC2Instance`).
4. Choose **Amazon Linux 2 AMI (Free Tier eligible)**.
5. Select instance type: `t2.micro`.
6. Create a **Key Pair** → select `.pem` format → download securely.
7. Configure Security Group → Add Rule:
   - **Type:** SSH  
   - **Protocol:** TCP  
   - **Port:** 22  
   - **Source:** My IP
8. Launch the instance and wait for it to run.
9. Copy the **Public IPv4 address**.
10. Change key permission:
   ```bash
   chmod 400 your-key-name.pem
   ```
11. Connect using SSH:
   ```bash
   ssh -i "your-key-name.pem" ec2-user@<your-ec2-public-ip>
   ```

### 🧩 Description
An **Amazon EC2 (Elastic Compute Cloud)** instance is a virtual server in AWS providing scalable computing power. It allows flexible configurations of CPU, memory, storage, and OS to meet user needs. Common uses include web hosting, data analysis, and ML workloads. With secure access via IAM, key pairs, and security groups, EC2 offers reliability, scalability, and cost-effectiveness.

---

## 🧪 Experiment 2: Create an Amazon SQS Queue and Send Messages Using AWS CLI

### 🎯 Objective
To understand how to create and manage **Simple Queue Service (SQS)** queues and send messages using AWS CLI.

### 🏁 Outcome
Students will learn to create an SQS queue and manage messages via CLI commands.

### ⚙️ Step-by-Step Procedure
1. Install AWS CLI → [Download here](https://aws.amazon.com/cli/)
2. Configure CLI:
   ```bash
   aws configure
   ```
   Enter:
   - Access Key ID  
   - Secret Access Key  
   - Region (e.g., us-east-1)  
   - Output format: `json`
3. Create a queue:
   ```bash
   aws sqs create-queue --queue-name MyQueue
   ```
4. List queues:
   ```bash
   aws sqs list-queues
   ```
5. Get queue URL:
   ```bash
   aws sqs get-queue-url --queue-name MyQueue
   ```
6. Send a message:
   ```bash
   aws sqs send-message --queue-url <your-queue-url> --message-body "Hello from Cloud Lab"
   ```
7. Receive the message:
   ```bash
   aws sqs receive-message --queue-url <your-queue-url>
   ```

### 🧩 Description
**Amazon SQS** is a fully managed message queuing service for decoupling distributed systems. It supports asynchronous communication between microservices and ensures reliability through **Standard** and **FIFO** queue types.

---

## 🧪 Experiment 3: Create an SNS Topic, Subscribe via Email, and Publish a Message

### 🎯 Objective
To demonstrate how to use **Amazon SNS** to create topics, subscribe endpoints, and publish messages.

### 🏁 Outcome
Students will create an SNS topic, subscribe via email, and send notifications.

### ⚙️ Step-by-Step Procedure
1. Open **Simple Notification Service (SNS)** in AWS.
2. Create a **Standard topic** named `MyTopic`.
3. Create a **Subscription**:
   - Protocol: Email  
   - Endpoint: Your valid email
4. Confirm subscription via email.
5. Publish a message:
   - Subject: *Test Notification*  
   - Message: *This is a test message from AWS SNS.*

### 🧩 Description
**Amazon SNS** uses a publish-subscribe model for push-based communication across services and users. It’s widely used for event notifications, monitoring, and automation triggers.

---

## 🧪 Experiment 4: Create an S3 Bucket and Upload Files

### 🎯 Objective
To learn how to create and manage an **Amazon S3** bucket.

### ⚙️ Step-by-Step Procedure
1. Open **S3** service in AWS.
2. Click **Create bucket** → give it a unique name.
3. Choose region → leave defaults → click **Create**.
4. Open bucket → click **Upload** → add files → **Upload**.

### 🧩 Description
**Amazon S3 (Simple Storage Service)** is an object storage service for secure, scalable, and durable data storage. Common uses include website hosting, backups, and analytics.

---

## 🧪 Experiment 5: Deploy a WordPress Website Using Amazon Lightsail

### 🎯 Objective
To learn how to deploy a **WordPress** site using Lightsail Free Tier.

### ⚙️ Step-by-Step Procedure
1. Open **Amazon Lightsail**.
2. Create an instance → Platform: Linux/Unix → Blueprint: WordPress.
3. Choose Free Tier plan → Name the instance → Create.
4. Access WordPress at:
   ```
   http://<public-ip>
   ```
5. Admin login:
   ```
   http://<public-ip>/wp-admin
   ```
   Default user: `user`  
   Password: Retrieve via SSH →  
   ```bash
   cat bitnami_application_password
   ```

### 🧩 Description
**Lightsail** simplifies WordPress deployment by bundling compute, storage, and networking in one package with predictable pricing.

---

## 🧪 Experiment 6: Configure AWS Backup for EC2 and Restore Data

### 🎯 Objective
To automate EC2 backups using **AWS Backup**.

### ⚙️ Procedure
1. Open **AWS Backup** → Create Backup Plan.
2. Define plan name, frequency, and retention.
3. Assign EC2 instance as resource.
4. Monitor backup job and restore from the vault when needed.

### 🧩 Description
**AWS Backup** centralizes automated backup management across services. It supports encryption, lifecycle rules, and compliance tracking.

---

## 🧪 Experiment 7: Launch RDS MySQL Instance and Connect via MySQL Workbench

### 🎯 Objective
To create and connect to an **Amazon RDS** MySQL database.

### ⚙️ Procedure
1. Open **Amazon RDS** → Create Database.
2. Engine: MySQL → Free Tier.
3. Configure credentials → Enable public access → Launch.
4. Connect using:
   - Hostname: RDS endpoint  
   - Port: 3306  
   - User & Password as configured  
5. Create database:
   ```sql
   CREATE DATABASE labdb;
   ```

### 🧩 Description
**Amazon RDS** provides scalable, managed relational databases with automated backups and patching.

---

## 🧪 Experiment 8: Create a DynamoDB Table and Perform CRUD Operations

### ⚙️ Procedure
```bash
aws configure

aws dynamodb create-table   --table-name StudentRecords   --attribute-definitions AttributeName=StudentID,AttributeType=S   --key-schema AttributeName=StudentID,KeyType=HASH   --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1

aws dynamodb put-item   --table-name StudentRecords   --item '{"StudentID": {"S": "101"}, "Name": {"S": "John"}, "Dept": {"S": "CSE"}}'

aws dynamodb get-item   --table-name StudentRecords   --key '{"StudentID": {"S": "101"}}'

aws dynamodb delete-item   --table-name StudentRecords   --key '{"StudentID": {"S": "101"}}'
```

### 🧩 Description
**Amazon DynamoDB** is a fully managed NoSQL service supporting key-value and document data structures for high-performance applications.

---

## 🧪 Experiment 9: Analyze an Image Using Amazon Rekognition

### ⚙️ Procedure
1. Upload image to S3 bucket.
2. Run:
   ```bash
   aws rekognition detect-labels      --image "S3Object={Bucket=my-bucket,Name=my-image.jpg}"      --max-labels 10      --min-confidence 70
   ```
3. Review JSON output for detected objects.

### 🧩 Description
**Amazon Rekognition** uses AI to detect objects, faces, and scenes in images and videos, providing powerful visual analysis capabilities.

---

## 🧪 Experiment 10: Train a Simple ML Model Using Amazon SageMaker

### ⚙️ Procedure
1. Create **SageMaker Notebook Instance** → `ml.t2.medium`.
2. Open Jupyter → Python 3 kernel.
3. Run:
   ```python
   from sklearn.datasets import load_iris
   from sklearn.model_selection import train_test_split
   from sklearn.ensemble import RandomForestClassifier
   from sklearn.metrics import accuracy_score

   data = load_iris()
   X_train, X_test, y_train, y_test = train_test_split(data.data, data.target)
   model = RandomForestClassifier()
   model.fit(X_train, y_train)
   predictions = model.predict(X_test)
   print("Model Accuracy:", accuracy_score(y_test, predictions))
   ```

### 🧩 Description
**Amazon SageMaker** offers a managed ML environment to build, train, and deploy models easily using Jupyter notebooks and built-in algorithms.

---

## 📘 Author
**Laxmidhar Penta**

## 🏷️ License
This project is licensed under the [MIT License](LICENSE).

---
