
# 🚗 Vehicle Insurance Prediction ML Project

This is a full-scale **Machine Learning Project** that simulates a real-world data science workflow for predicting vehicle insurance outcomes. The project demonstrates end-to-end MLOps capabilities including data ingestion, transformation, model training, evaluation, deployment, and CI/CD integration using **FastAPI**, **MongoDB**, **AWS**, **Docker**, and **GitHub Actions**.

---

## 🔧 Tech Stack & Tools

| Area                | Tools / Services Used                                                 |
|---------------------|-----------------------------------------------------------------------|
| Language            | Python 3.10                                                           |
| Environment         | Conda, pip, Virtual Environments                                      |
| Data Storage        | MongoDB Atlas                                                         |
| Web Framework       | FastAPI                                                               |
| Deployment          | Docker, AWS EC2, AWS ECR, GitHub Actions CI/CD                        |
| Monitoring & Logs   | Python Logging, Custom Exception Handling                             |
| Model Registry      | AWS S3                                                                |
| CI/CD Pipeline      | GitHub Actions Self-Hosted Runner (on AWS EC2)                        |
| Version Control     | Git, GitHub                                                            |

---

## 📁 Project Setup Instructions

### 1. 📦 Project Scaffold & Environment
```bash
# Clone and initialize project
python template.py

# Setup Python environment
conda create --name vehicleproj python=3.10 -y
conda activate vehicleproj

# Install dependencies
pip install -r requirements.txt
pip list  # Confirm installation

# Local package setup
# setup.py and pyproject.toml used for managing local packages
````


---

## ☁️ MongoDB Atlas Setup

1. **Create MongoDB Cluster**

   * Sign up at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
   * Create project, M0 cluster, and deployment.

2. **Set up access**

   * Add user and IP range: `0.0.0.0/0`

3. **Get Connection String**

   * Replace `<password>` with your credentials.

4. **Push local data to MongoDB**

   * Use `mongoDB_demo.ipynb` from `notebook/` directory.

5. **Browse uploaded data**

   * MongoDB Atlas > Database > Browse Collections

---

## 📝 Logging, Exception Handling & EDA

* `logging/` - Custom logger setup
* `exception/` - Custom exception handling class
* `EDA and Feature Engineering` notebooks included

---

## 📊 Data Pipeline Architecture

### 🛠 Data Ingestion

* MongoDB connection via `configuration.mongo_db_connection.py`
* Data ingestion logic in `components/data_ingestion.py`
* Artifact and config entities defined in:

  * `entity/config_entity.py`
  * `entity/artifact_entity.py`

```bash
# Setup MongoDB URL (Linux/Mac)
export MONGODB_URL="mongodb+srv://<username>:<password>..."
echo $MONGODB_URL
```

### ✅ Data Validation

* Defined schema in `config/schema.yaml`
* Util functions in `utils/main_utils.py`
* Modular pipeline similar to ingestion step

### 🔄 Data Transformation

* Preprocessing logic and feature transformation
* Custom transformers in `entity/estimator.py`

### 🧠 Model Training

* Model training module with performance tracking
* Pluggable training pipeline

---

## ☁️ AWS S3 Integration for Model Storage

### 🔐 IAM & Credential Setup

* Create user with `AdministratorAccess`
* Export credentials to environment variables

```bash
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."
```

### 🪣 S3 Bucket Configuration

* Bucket Name: `nitesh-model-mlopsproj`
* Region: `us-east-1`

### 📁 S3 Model Storage

* `src/aws_storage/s3_operations.py` manages pull/push
* `entity/s3_estimator.py` contains S3 estimator class

---

## 📈 Model Evaluation & Pusher

* Threshold-based comparison logic for model updates
* AWS S3 push logic embedded
* Integration with existing training pipeline

---

## ⚙️ Prediction & Web Deployment

### 🚀 FastAPI App Setup

* `app.py` serves the prediction interface
* `static/` and `template/` directories support UI

---

## 🐳 Docker + GitHub Actions CI/CD Pipeline

### 🧱 Docker Setup

* `Dockerfile` and `.dockerignore` added
* Containerizes entire ML workflow and app

### 🔁 GitHub Actions Workflow

* Self-hosted runner setup on AWS EC2
* Workflow config: `.github/workflows/aws.yaml`

### 🧪 Secrets for GitHub

* AWS\_ACCESS\_KEY\_ID
* AWS\_SECRET\_ACCESS\_KEY
* AWS\_DEFAULT\_REGION
* ECR\_REPO

---

## ☁️ AWS EC2 Deployment

### 🖥️ EC2 Server Setup

* Ubuntu 24.04, T2 Medium (3.5Rs/hr)
* Port `5080` activated for public web access

```bash
# Install Docker on EC2
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
```

### 🔗 Connect Runner to GitHub

* Self-hosted runner installed & connected
* CI pipeline auto-triggers on commit

---

## 🌐 Launch the App

Once deployed, visit:

```
http://<your-ec2-public-ip>:5080
```

Also, model training endpoint:

```
http://<your-ec2-public-ip>:5080/training
```

---

## 📌 Key Features

* ✅ Modular, production-grade ML pipeline
* 🌐 Scalable cloud deployment with MongoDB + AWS
* 🧪 Fully dockerized + CI/CD ready
* 🧾 Custom logging, exception, config, schema management
* 🧠 On-demand model training, prediction, and version control

---

## 💼 Ideal For

* Showcasing MLOps skills
* Job portfolios in Data Science/ML Engineering
* Real-world machine learning pipeline practice

---

## 🙌 Credits

Made with ❤️ by Nitesh Kumar
Special thanks to the open-source community and mentors.

---

## 📬 Contact

**LinkedIn**: [linkedin.com/in/niteshdiat](https://www.linkedin.com/in/niteshdiat/)
**Email**: [nit51196@gmail.com](mailto:nit51196@gmail.com)

---


