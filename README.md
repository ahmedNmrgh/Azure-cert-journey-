# 🚀 My 1-Month AZ-104 Preparation Journey

While preparing for the **AZ-104: Microsoft Azure Administrator** exam, I committed to a **1-month journey** where I balanced theory, labs, and practice tests. To keep myself motivated, I documented everything on GitLab as a living blog of my progress. By the end of the month, I had not only studied but also built a full demo environment to tie the concepts together.

This post walks you through my weekly routine, the hands-on project I built, and the lessons that made the biggest difference.

---

## 📅 My Weekly Plan

### Week 1 – Foundations

* Set up my GitLab repo to track progress.
* Reviewed **Azure core services** (Compute, Networking, Storage).
* Completed MS Learn modules for **Azure Resource Manager (ARM)** and **Subscriptions/Resource Groups**.
* Hands-on: Deployed my first VM with CLI and Portal, practiced with role assignments.

➡️ Goal: Build strong fundamentals and get comfortable with the portal + CLI.

### Week 2 – Networking & Identity

* Focused on **VNets, subnets, NSGs, and VNet peering**.
* Learned about **Entra ID (Azure AD)**, RBAC, and role assignments.
* Hands-on: Built a hub-and-spoke VNet setup with Bastion for secure access.
* Documented every command and JSON snippet into my GitLab blog.

➡️ Goal: Understand connectivity and identity, which are big topics on the exam.

### Week 3 – Storage & Compute

* Reviewed **Storage Accounts, replication, SAS tokens, private endpoints, and private DNS zones**.
* Learned about **Azure Load Balancers vs Application Gateway vs Traffic Manager**.
* Hands-on: Built **Web Tier VMs behind a Load Balancer** + **Application Gateway with WAF**.
* Practiced deploying ARM templates from GitLab CI/CD pipeline.

➡️ Goal: Practice exam-level scenarios like secure storage and load balancing.

### Week 4 – Monitoring, Backup & Review

* Worked on **Azure Monitor, Metrics, Logs, Alerts, and Action Groups**.
* Practiced setting up **Backup and Recovery Vaults**.
* Hands-on: Connected VMs to Log Analytics, set up alerts for CPU thresholds.
* Took **Whizlabs and Microsoft practice tests**.
* Final project: Built and deployed my **multi-region demo architecture**.

➡️ Goal: Tie everything together and be exam-ready.

---

## 🖼 My Demo Project

To reinforce learning, I created a **hub-and-spoke, multi-region architecture**:

![AZ-104 Demo Architecture](az104-demo.png)

### Key Components:

* **Hub VNet (UK South)** → Bastion, shared services.
* **Spoke VNet (North Europe)** → Application VM + App Gateway WAF.
* **Spoke VNet (East US)** → Database VM + Internal Load Balancer.
* **Web Tier** → 2 Linux VMs behind a Public Load Balancer.
* **Storage with Private Endpoint** → Private DNS + blob access from US subnet.

Template: [`az104-demo.json`](az104-demo.json).

---

## ⚡ Deployment from GitLab

I automated deployments using **GitLab CI/CD**:

`.gitlab-ci.yml` snippet:

```yaml
stages:
  - deploy

az104_deploy:
  stage: deploy
  script:
    - az group create --name az104-rg --location uksouth
    - az deployment group create --resource-group az104-rg --template-file az104-demo-extended.json
```

This way, each commit to my GitLab repo could trigger a deployment.

---

## 🎯 Exam-Relevant Learning Outcomes

* **Networking** → VNet peering, private DNS, endpoints.
* **Identity** → RBAC, Bastion, role assignments.
* **Compute & Storage** → VMs, OS disks, storage redundancy.
* **Security** → Application Gateway WAF, private storage.
* **Automation** → ARM Templates + GitLab pipelines.

---

