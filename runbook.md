---

## ⚙️ Deployment Workflow  
1. Developer pushes to `main` branch.  
2. GitHub Actions pipeline triggers automatically:  
   - **Terraform job:** `init → fmt → validate → plan → apply`  
   - **Docker job:** Builds and deploys Prometheus + Grafana stack on EC2  
3. Prometheus begins scraping metrics; Grafana loads dashboards.  
4. CloudWatch alarms monitor thresholds and send alerts via SNS.  
5. Dashboards display live service health metrics and SLO compliance.

---

## 🧩 Features  
- **Terraform-based AWS infrastructure**  
- **Prometheus + Grafana** containerised with Docker Compose  
- **ALB metrics integration** (latency, error rate, throughput)  
- **CloudWatch + SNS alerting** pipeline  
- **Pre-built Grafana dashboards** for SLI/SLO visualisation  
- **CI/CD automation** via GitHub Actions  
- **Runbooks and incident response workflows**

---

## 🎓 Learning Outcomes  
Through this capstone, you’ll demonstrate:
- End-to-end automation using IaC and GitOps
- Observability principles (metrics, logs, alerts, dashboards)
- Practical SRE practices: SLIs, SLOs, incident response
- Security & compliance considerations in cloud environments
- Operational readiness documentation and monitoring maturity

---

## 🪄 Setup & Usage

### Prerequisites
- AWS Account with IAM permissions (EC2, VPC, CloudWatch, SNS)
- Terraform ≥ 1.6  
- Docker + Docker Compose  
- GitHub Repository with Secrets:
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`
  - *(optional)* `TF_TOKEN_app_terraform_io` for Terraform Cloud

### Deployment Steps
```bash
# 1. Clone repository
git clone https://github.com/<your-org>/<repo>.git
cd <repo>

# 2. Initialise Terraform
cd terraform
terraform init
terraform plan
terraform apply --auto-approve

# 3. Deploy monitoring stack
cd ../monitoring
docker compose up -d

Access Grafana via http://<EC2-Public-IP>:3000 (default: admin/admin).
