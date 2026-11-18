# SelfHealing-EC2-Physical-Reset

A cloud-based Self-Healing EC2 monitoring system built using Python, AWS EC2, AWS Auto Scaling, Boto3, and Streamlit. The project monitors EC2 instance health, tracks Auto Scaling activities, displays running instances, and provides recovery status through a real-time dashboard with automatic 10-second refresh to improve cloud infrastructure availability and reliability.

# ☁️ Self-Healing EC2 – Automated Cloud Instance Recovery System

### Detect. Recover. Stay Online.

A cloud-based EC2 monitoring and automated recovery solution built using **Amazon Web Services (AWS), Python, Boto3, and Streamlit**. The system monitors EC2 instances through an AWS Auto Scaling Group and provides a real-time dashboard to track instance health, scaling activities, and recovery progress.

---

## 📌 Project Overview

Cloud-hosted applications depend on server availability and reliability. When an EC2 instance becomes unhealthy or fails, application availability can be affected.

**Self-Healing EC2** aims to reduce manual intervention by using AWS Auto Scaling to replace unhealthy instances automatically.

The project also provides a centralized Streamlit dashboard that allows administrators to monitor AWS infrastructure, view running instances, track instance health, and observe scaling activities.

## 🎯 Objectives

- Detect and monitor EC2 instance health.
- Automatically replace unhealthy instances using AWS Auto Scaling.
- Maintain the desired capacity of the Auto Scaling Group.
- Display real-time EC2 instance information.
- Track AWS scaling activities and recovery duration.
- Simplify cloud infrastructure monitoring through a user-friendly dashboard.

## ✨ Key Features

### 1. AWS Connection Monitoring
- Connects directly to AWS using Python Boto3.
- Displays AWS connection status.
- Supports AWS region configuration.

### 2. Auto Scaling Group Monitoring
- Displays Auto Scaling Group information.
- Shows desired, minimum, and maximum capacity.
- Tracks healthy, pending, and terminating instances.

### 3. EC2 Instance Monitoring
- Displays all current instances associated with the configured Auto Scaling Group.
- Shows instance ID and instance type.
- Displays instance state and health status.
- Shows availability zone and private IP address.
- Identifies the most recently launched instance.

### 4. Recovery Monitoring
- Displays recent AWS Auto Scaling activities.
- Tracks instance launch activity status.
- Calculates recorded AWS launch activity duration when timestamps are available.

### 5. Automatic Dashboard Refresh
- Refreshes monitoring information every 10 seconds.
- Updates instance and Auto Scaling Group status.
- Displays the latest dashboard update time.

---

## 🏗️ System Architecture

The project follows this architecture:

```text
             ADMIN / USER
                  |
                  ▼
         STREAMLIT DASHBOARD
                  |
                  ▼
             PYTHON
                  |
                  ▼
              BOTO3
                  |
                  ▼
             AWS CLOUD
                  |
          ┌───────┴────────┐
          ▼                ▼
    AUTO SCALING       AMAZON EC2
       GROUP            INSTANCES
          |                |
          └───────┬────────┘
                  |
                  ▼
          MONITORING OUTPUT
                  |
                  ▼
        INSTANCE HEALTH STATUS
         SCALING ACTIVITY LOGS
           RECOVERY TRACKING
```

### Workflow

1. The administrator opens the Streamlit dashboard.
2. Python Boto3 communicates with AWS services.
3. AWS Auto Scaling Group information is retrieved.
4. EC2 instance details and health information are collected.
5. The dashboard displays infrastructure status.
6. AWS Auto Scaling manages the replacement of unhealthy instances according to its configuration.
7. The dashboard refreshes automatically every 10 seconds.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Backend programming |
| Streamlit | Interactive monitoring dashboard |
| Boto3 | AWS SDK for Python |
| Amazon EC2 | Virtual cloud computing instances |
| AWS Auto Scaling | Automated instance replacement and capacity management |
| AWS IAM | Access control and permissions |
| Pandas | Instance data presentation |
| Visual Studio Code | Development environment |
| AWS Academy Learner Lab | Cloud environment for development and testing |

---

## 📂 Project Structure

```text
Self-Healing-EC2/
│
├── app.py
│
├── README.md
│
├── requirements.txt
│
├── .gitignore
│
└── assets/
    └── architecture.png
```

*This is the suggested repository structure. Include only files and folders that exist in your actual project.*

---

## ⚙️ Installation and Setup

### Prerequisites

Make sure you have installed:

- Python 3.10 or later
- Visual Studio Code
- AWS CLI
- An active AWS account or AWS Academy Learner Lab
- Git

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Self-Healing-EC2.git
```

### Step 2: Navigate to the Project Folder

```bash
cd Self-Healing-EC2
```

### Step 3: Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
python -m pip install streamlit boto3 pandas
```

### Step 5: Configure AWS Credentials

Configure your AWS CLI credentials using your authorized AWS environment.

```bash
aws configure
```

For AWS Academy Learner Lab, use the temporary credentials and configuration instructions provided by the lab.

Verify your AWS identity:

```bash
aws sts get-caller-identity
```

### Step 6: Configure the AWS Region

The project uses:

```python
REGION = "us-east-1"
GROUP_NAME = "Self_Healing"
```

Ensure that your Auto Scaling Group exists in the configured AWS region.

### Step 7: Run the Dashboard

```bash
python -m streamlit run app.py
```

Open the dashboard in your browser:

```text
http://localhost:8501
```

---

## 🔐 Required AWS Permissions

The application requires appropriate AWS permissions to retrieve monitoring information.

| AWS Permission | Purpose |
|---|---|
| autoscaling:DescribeAutoScalingGroups | Retrieve Auto Scaling Group information |
| autoscaling:DescribeScalingActivities | Retrieve scaling activity history |
| ec2:DescribeInstances | Retrieve EC2 instance information |

AWS credentials should never be hardcoded into the source code or uploaded to GitHub.

---

## 🧪 Testing and Validation

The following test cases can be used to validate the project:

| Test Case | Expected Result |
|---|---|
| AWS connection verification | AWS connection succeeds |
| Auto Scaling Group retrieval | Group details are displayed |
| EC2 instance retrieval | Current instance information appears |
| Instance health monitoring | Health status is displayed |
| Instance termination test | AWS Auto Scaling attempts replacement when configured to do so |
| Dashboard refresh | Monitoring information updates every 10 seconds |
| AWS credential expiration | Dashboard displays an appropriate AWS error |

---

## 📊 Expected Outcomes

- Centralized monitoring of AWS EC2 instances.
- Improved visibility into Auto Scaling activities.
- Reduced manual monitoring effort.
- Automated replacement of unhealthy instances through AWS Auto Scaling.
- Better understanding of cloud infrastructure availability and recovery.

---

## ⚠️ Current Limitations

- The dashboard currently focuses on read-only AWS monitoring.
- Monitoring depends on valid AWS credentials and IAM permissions.
- AWS Academy temporary credentials may expire.
- Recovery duration can vary depending on AWS infrastructure and instance configuration.
- Large-scale failure scenarios and production workloads require further testing.
- The application currently monitors one configured Auto Scaling Group.

**Note:** The duration of an AWS launch activity is not necessarily the complete time required for a replacement instance to become healthy and reach the InService state.

---

## 🚀 Future Enhancements

- Add a secure manual EC2 reset feature.
- Integrate Amazon CloudWatch alarms and metrics.
- Add graphical recovery-time analytics.
- Support multiple Auto Scaling Groups.
- Introduce email or notification alerts.
- Add historical instance monitoring and recovery reports.
- Deploy the dashboard to a cloud-hosted environment.
- Improve security with role-based access control.

---

## 💡 Real-World Applications

- E-commerce platforms
- Banking and financial applications
- Cloud-hosted websites
- Enterprise IT infrastructure
- Online booking systems
- Application hosting environments

**Example:** If an EC2 instance hosting an e-commerce application becomes unhealthy, AWS Auto Scaling can launch a replacement instance to help maintain application availability.

---

## 👨‍💻 Project Information

**Project Name:** Self-Healing EC2 – Automated Cloud Instance Recovery System

**Project Domain:** Cloud Computing / AWS / DevOps

**Institution:** SR University

**Development Tools:** Python, Streamlit, Boto3, AWS

**Project Region:** US East (N. Virginia) – `us-east-1`

---

## 📜 License

This project is developed for educational and academic purposes. You may add an open-source license such as the MIT License if you intend to distribute it under those terms.

---

### ⭐ Support

If you find this project interesting, consider giving the repository a ⭐ on GitHub.

**Self-Healing EC2 – Detect. Recover. Stay Online.**
