# Terraform Configuration for Private Service Connect (PSC) to Vertex AI (Gemini CLI) on Google Cloud

## 🛠️ What this project does
✅ Creates a custom VPC and firewall rules  
✅ Deploys two VM instances (`cli-vm` and `monitor-vm`)  
✅ Configures Cloud NAT and Cloud Router  
✅ Creates a Private Service Connect (PSC) endpoint for Vertex AI APIs  
✅ Configures private DNS zone and records to route traffic privately  
✅ Tests traffic routing and connectivity from VMs

## 🏗️ Project structure

| File           | Description                                   |
| -------------- | --------------------------------------------- |
| `main.tf`      | Main resources: VPC, VMs, NAT, firewall, etc. |
| `psc.tf`       | PSC endpoint and global internal address      |
| `dns.tf`       | Private DNS zone and A/CNAME records          |
| `variables.tf` | Input variables                               |
| `outputs.tf`   | Outputs after apply (e.g., VM IPs)            |
| `versions.tf`  | Terraform & provider version constraints      |




## 🚀 How to use

Make sure you're inside **Cloud Shell** and have Terraform installed.

1.  **Navigate to the project folder:**
    ```bash
    cd terraform-build
    ```

2.  **Initialize Terraform:**
    ```bash
    terraform init
    ```

3.  **Review the planned changes:**
    ```bash
    terraform plan
    ```

4.  **Apply the configuration:**
    ```bash
    terraform apply
    ```
    * Type `yes` when prompted to confirm the application.

5.  **After deployment, verify resources in Google Cloud Console:**
    * VPC
    * Cloud NAT & Router
    * VM instances (`cli-vm` and `monitor-vm`)
    * PSC endpoint
    * Private DNS zone

### 🧪 Test connectivity

* **SSH into `cli-vm`** and run Gemini CLI to test API access.
* **SSH into `monitor-vm`** and use `dig` and `ping` to confirm traffic routes through the PSC endpoint (IP `10.10.100.250`).
* **Use `tcpdump` on `cli-vm`** to observe DNS and API traffic.

### 🌱 Next steps

* Add more resources or configurations (e.g., IAM, logging).
* Read the Vertex AI networking guide for more details.
* Try Gemini CLI for generating prompts and interacting with Vertex AI.

### ⚙️ Requirements

* Google Cloud project with billing enabled.
* Terraform installed.
* Gemini CLI installed (if you plan to use it outside `cli-vm`).
* Node.js (for Gemini CLI).

### ✅ License

This project is licensed under the [MIT License](LICENSE).
