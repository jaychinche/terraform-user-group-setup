# terraform-user-group-setup

Here is the content formatted as a Word document. You can copy this into a Word file or download it as a `.docx` file:

---

# **Terraform AWS IAM User Setup**  

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

---

