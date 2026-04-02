# AWS WordPress Deployment with Automated S3 Backup

This repository contains a containerized WordPress and MySQL deployment hosted on an **AWS EC2** instance. It features persistent storage using an **EBS Volume** and automated off-site backups to **Amazon S3**.

---

## 🏗️ Architecture
* **Instance:** EC2 t3.micro (Ubuntu 24.04)
* **Orchestration:** Docker Compose
* **Database:** MySQL 8.0
* **Storage:** 8GB EBS Volume mounted at `/mnt/mysql-data`
* **Backup:** AWS CLI v2 syncing to S3 (`wordpress-backup-mariam-2026`)

---

## 📂 Project Files
* **provision.sh:** Script for system updates, Docker installation, and EBS mounting.
* **docker-compose.yml:** Defines the WP and MySQL services with volume persistence.
* **backup.sh:** Automates the backup of the project directory to the cloud.
* **.env.example:** Template for environment variables.

---

## 🛠️ How to Run
1. Run `./provision.sh` to prepare the server and storage.
2. Configure your credentials in a `.env` file.
3. Launch the site with `docker-compose up -d`.
4. Execute `./backup.sh` to secure your data to S3.

---

## 🔍 Troubleshooting Highlights
* **Bucket Resolution:** Corrected naming conventions to match `wordpress-backup-mariam-2026`.
* **CLI Configuration:** Fixed region mismatch by targeting `us-east-1` instead of specific AZ endpoints.
* **Persistence:** Successfully mapped Docker volumes to a physical EBS mount point to prevent data loss.
