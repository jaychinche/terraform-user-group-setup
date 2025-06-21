
# 2) 🚀 Jenkins on AWS EC2 - Setup Guide

## 📅 Today I Learned

Today, I learned **what Jenkins is**, **why it's used**, and **how to install and configure it on an AWS EC2 instance** from scratch.

---

## 📌 What is Jenkins?

**Jenkins** is an open-source automation server used to build, test, and deploy applications automatically. It is widely used for **Continuous Integration (CI)** and **Continuous Deployment (CD)** in DevOps pipelines.

---

## ❓ Why Use Jenkins?

- Automates the software build and test process
- Enables frequent code integration and delivery
- Supports many plugins for Git, Docker, Slack, Email, etc.
- Works with any language or tech stack
- Improves team collaboration and release speed

---

## 🔧 Technologies Used

- **AWS EC2 (Ubuntu Server 22.04)**
- **Jenkins (LTS)**
- **Java 17**
- **Linux CLI**
- Optional tools:
  - **Git**
  - **Docker**

---

## ✅ Step-by-Step Jenkins Setup on AWS

### 🔸 1. Launch EC2 Instance

- **AMI**: Ubuntu Server 22.04 LTS
- **Instance Type**: `t2.micro` (Free Tier)
- **Key Pair**: `jenkins-key.pem`
- **Security Group Rules**:
  - `HTTP (port 80)`
  - `Custom TCP (port 8080)`
  - `SSH (port 22)`

---

### 🔸 2. Connect to EC2

```bash
chmod 400 jenkins-key.pem
ssh -i "jenkins-key.pem" ubuntu@<your-ec2-public-ip>
````

---

### 🔸 3. Install Jenkins

```bash
# Update packages
sudo apt update && sudo apt upgrade -y

# Install Java (required for Jenkins)
sudo apt install openjdk-17-jdk -y

# Add Jenkins repository and key
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update and install Jenkins
sudo apt update
sudo apt install jenkins -y

# Start and enable Jenkins service
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

---

### 🔸 4. Access Jenkins in Browser

Go to:

```txt
http://<your-ec2-public-ip>:8080
```

---

### 🔸 5. Unlock Jenkins

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

* Copy and paste this password into the Jenkins setup page in your browser.

---

### 🔸 6. Install Plugins & Create Admin User

* Select: ✅ `Install Suggested Plugins`
* Create admin user:

  * Username
  * Password
  * Email

---

### 🔸 7. Create Your First Jenkins Job

* Go to: `New Item > Freestyle Project`
* Add a build step:

```bash
echo "Hello from Jenkins"
```

* Click `Save` and then `Build Now`
* View `Console Output` to see your result

---

## 🛠 Optional Enhancements

### 📦 Install Git (for Git integration)

```bash
sudo apt install git -y
```

### 🐳 Install Docker (for containerized builds)

```bash
# Install Docker
sudo apt install docker.io -y

# Add Jenkins to Docker group
sudo usermod -aG docker jenkins

# Restart Jenkins
sudo systemctl restart jenkins
```

---

## 📚 Final Thoughts

By following these steps, I now understand:

* What Jenkins is and its role in CI/CD
* How to install and configure Jenkins on AWS EC2
* How to create basic Jenkins jobs
* How Jenkins can be extended with Git, Docker, and plugins

This setup provides a strong foundation for DevOps and automation workflows.

---

## 🔗 Resources

* Jenkins Official: [https://www.jenkins.io](https://www.jenkins.io)
* AWS EC2 Docs: [https://docs.aws.amazon.com/ec2/](https://docs.aws.amazon.com/ec2/)

<br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br> 
















# 1)**Terraform AWS IAM User Setup**  

Welcome to this simple Terraform project where I learned the basics of Terraform, including installation, usage, and how to create an IAM user in AWS using Terraform.  

---

## **📘 Introduction to Terraform**  

### **✅ What is Terraform?**  
Terraform is an **open-source Infrastructure as Code (IaC)** tool developed by **HashiCorp**. It allows you to define, provision, and manage infrastructure across a wide range of cloud providers like AWS, Azure, GCP, and many others — using declarative configuration files.  

### **✅ Why use Terraform?**  
- Infrastructure automation and version control  
- Repeatable deployments with minimal human error  
- Works across multiple cloud platforms  
- Easily handles dependencies  
- Efficient resource management through its state files  

---

## **🛠️ Prerequisites**  
- **AWS Account**  
- **AWS CLI** installed and configured (optional but recommended)  
- **[Terraform installed](https://developer.hashicorp.com/terraform/downloads)**  
- **Code Editor** like VS Code  

---

## **📁 Project Structure**  
```
terraform-user-group-setup/  
├── main.tf          # Terraform configuration to create AWS IAM user  
├── provider.tf      # AWS provider setup  
└── README.md        # Project documentation (this file)  
```

---

## **🔧 Terraform Installation Steps**  
1. **Download Terraform**: [Install Terraform](https://developer.hashicorp.com/terraform/downloads)  
2. **Verify installation**:  
   ```bash  
   terraform -v  
   ```

---

## **📂 Getting Started**  

### **Step 1: Create a Repository**  
Create a GitHub repository (e.g., `terraform-repo`).  

Clone it locally:  
```bash  
git clone https://github.com/your-username/terraform-repo.git  
cd terraform-repo  
```  

### **Step 2: Create Terraform Files**  

#### **🔹 main.tf**  
```hcl  
resource "aws_iam_user" "example_user" {  
  name = "new-example-user"  
}  
```  

#### **🔹 provider.tf**  
⚠️ **NEVER hard-code credentials in real projects.** Use environment variables or AWS CLI config instead.  
```hcl  
provider "aws" {  
  region     = "us-east-1"  
  access_key = "YOUR_ACCESS_KEY"     # Replace with env var or AWS CLI config  
  secret_key = "YOUR_SECRET_KEY"  
}  
```  

---

## **🏁 Terraform Commands**  
After writing your configuration files:  

1. **Initialize Terraform**:  
   ```bash  
   terraform init  
   ```  

2. **Plan your deployment**:  
   ```bash  
   terraform plan  
   ```  

3. **Apply the changes to AWS**:  
   ```bash  
   terraform apply  
   ```  
   Confirm **yes** when prompted.  

---

## **🔐 Security Tips**  
- Never commit AWS access keys to GitHub.  
- Use `.gitignore` to ignore `.terraform/` and `*.tfstate` files.  
- Use **Terraform Cloud** or **AWS Vault** for secure secrets management.  

---

## **🧼 Cleanup**  
To delete the created resources:  
```bash  
terraform destroy  
```  

---

## **🙌 Conclusion**  
With this setup, I learned how to:  
✔ Install and initialize Terraform  
✔ Write Terraform configuration files  
✔ Create an IAM user on AWS  
✔ Understand the basics of **Infrastructure as Code (IaC)**  

---

## **📸 Screenshot (Optional)**  
Add screenshots of your terminal output or AWS Console if needed.  

---

## **📌 References**  
- [Terraform Docs](https://developer.hashicorp.com/terraform)  
- [AWS IAM Documentation](https://docs.aws.amazon.com/iam/)  

✅ **Author:** Jay Chinche  
📅 **Date:** June 20, 2025  





















