# Capstone
SCTP Capstone project for group 2
# 🧠 SRE Capstone Project – Production-Grade Monitoring Stack on AWS  
*Built with Terraform · Docker · Grafana · CloudWatch · GitHub Actions*

![CI/CD Status](https://img.shields.io/github/actions/workflow/status/<your-org>/<repo>/terraform-ci.yml?label=Terraform%20CI)  
![License](https://img.shields.io/badge/license-MIT-blue.svg)  
![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws)  
![Terraform](https://img.shields.io/badge/Terraform-IaC-purple?logo=terraform)

---

## 📖 Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Repository Structure](#repository-structure)
- [Deployment Workflow](#deployment-workflow)
- [Features](#features)
- [Learning Outcomes](#learning-outcomes)
- [Setup & Usage](#setup--usage)
- [Runbook & Maintenance](#runbook--maintenance)
- [Customisation & Extensions](#customisation--extensions)
- [Security & Cost](#security--cost)
- [Capstone Assessment Criteria](#capstone-assessment-criteria)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## 🌐 Overview  
This capstone demonstrates the **end-to-end lifecycle of a Site Reliability Engineering (SRE) monitoring stack**—from provisioning infrastructure and deploying observability tools to integrating alerting and CI/CD pipelines.

The stack is deployed entirely on **AWS** and implements SRE principles:
- **Automation** via Terraform and GitHub Actions  
- **Observability** with Prometheus, Grafana, and CloudWatch  
- **Reliability metrics** and alerting thresholds based on SLI/SLOs  
- **Runbooks** for incident response and operational readiness  

🎯 **Goal:** Deliver a *production-grade*, *reproducible*, and *self-healing* monitoring stack that meets SRE maturity requirements.

---

## 🏗 Architecture  
![Architecture Diagram](docs/architecture-diagram.png)

**Components**
- **VPC:** Private/public subnets with internet gateway and routing
- **EC2 Instance:** Hosts the monitoring stack (Prometheus + Grafana)
- **ALB:** Fronts application targets and exposes key metrics
- **CloudWatch:** Native metrics and custom alarms (5xx, latency, CPU)
- **SNS:** Alerting pipeline (email / Slack / PagerDuty)
- **GitHub Actions:** CI/CD for Terraform and Docker deployments

---

## 🧱 Repository Structure
├── terraform/
│   ├── vpc.tf
│   ├── ec2.tf
│   ├── alb.tf
│   ├── cloudwatch.tf
│   ├── sns.tf
│   └── outputs.tf
├── monitoring/
│   ├── prometheus/
│   │   └── prometheus.yml
│   ├── grafana/
│   │   └── dashboards/
│   └── docker-compose.yml
├── .github/
│   └── workflows/
│       └── terraform-ci.yml
├── docs/
│   ├── architecture-diagram.png
│   ├── dashboards-preview.png
│   └── runbook.md
└── README.md
