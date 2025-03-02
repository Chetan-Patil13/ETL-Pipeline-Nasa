# 🚀 Airflow ETL Pipeline with Postgres and API Integration

## 📌 Project Overview

This project involves building an ETL (Extract, Transform, Load) pipeline using **Apache Airflow**, **PostgreSQL**, and **NASA's Astronomy Picture of the Day (APOD) API**. The pipeline is designed to extract data from the external API, transform it into a structured format, and load it into a **Postgres database**.

Airflow acts as the orchestrator, managing task dependencies and scheduling the entire workflow. **Docker** is used to containerize Airflow and Postgres services, ensuring an isolated and reproducible environment.

---

## 🔗 Key Components

### 🏗️ **Airflow for Orchestration**

- Defines, schedules, and monitors the ETL pipeline.
- Uses a **Directed Acyclic Graph (DAG)** to structure task dependencies.
- Handles task execution reliability and monitoring.

### 🗄️ **PostgreSQL Database**

- Stores the extracted and transformed data.
- Runs as a **Docker container**, ensuring easy management and persistent data storage.
- Utilizes **PostgresHook** and **PostgresOperator** in Airflow for interaction.

### 🌌 **NASA API (Astronomy Picture of the Day)**

- External API providing daily astronomy-related images and metadata.
- Includes fields such as `title`, `explanation`, and `image URL`.
- Accessed via **Airflow's SimpleHttpOperator** to extract data.

---

## 🎯 Project Objectives

✔ **Extract Data**:

- Fetch astronomy-related metadata daily from NASA's **APOD API**.

✔ **Transform Data**:

- Process and filter the API response to ensure a structured format.

✔ **Load Data**:

- Store the processed data in a **PostgreSQL database** for further analysis and reporting.

---

## 🏛️ Architecture & Workflow

The ETL pipeline follows the **DAG (Directed Acyclic Graph)** structure in Airflow, with the following key stages:

1️⃣ **Extract (E):**

- Uses `SimpleHttpOperator` to send `GET` requests to NASA's APOD API.
- Receives JSON responses containing image metadata.

2️⃣ **Transform (T):**

- Processes and extracts relevant fields (`title`, `explanation`, `url`, `date`).
- Ensures data is formatted correctly before loading into Postgres.
- Utilizes Airflow’s **TaskFlow API** (`@task` decorator) for transformation.

3️⃣ **Load (L):**

- Uses `PostgresHook` to insert structured data into a **Postgres table**.
- Creates the table automatically if it doesn't exist.

---

## 🛠️ Tech Stack

- **Apache Airflow** 🌀 – Workflow orchestration
- **PostgreSQL** 🗃️ – Database storage
- **Docker** 🐳 – Containerization
- **Python** 🐍 – Scripting and data processing
- **NASA APOD API** 🌠 – External data source

---

## 🏁 Getting Started

### 🔹 Prerequisites

Ensure you have the following installed:

- **Docker & Docker Compose**
- **Python 3.8+**
- **Git**

### 🔹 Installation & Setup

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/Chetan-Patil13/ETL-Pipeline-Nasa.git
   cd ETL-Pipeline-Nasa
   ```
2. **Start the Airflow & Postgres Services**:
   ```sh
   docker-compose up -d
   ```
3. **Access Airflow UI**:

   - Open [http://localhost:8080](http://localhost:8080)
   - Default credentials: `airflow/airflow`

4. **Trigger the DAG**:
   - Navigate to `ml_pipeline` in the **Airflow UI**
   - Click **Trigger DAG** ▶️

---

## 📊 Expected Output

- Data from NASA's APOD API gets extracted and stored in **Postgres**.
- The pipeline runs **daily** as per the schedule defined in Airflow.
- Logs and task status can be monitored in **Airflow UI**.

---

## 📌 Future Improvements

🔹 Add **data validation** before inserting into Postgres.
🔹 Implement **logging & alerting** for failures.
🔹 Integrate **visualization tools** like Power BI or Tableau.

---

## 🙌 Contribution

Feel free to fork this repository and contribute! Suggestions and pull requests are welcome. 😊

---

## 📜 License

This project is licensed under the **MIT License**.

---

🚀 **Happy Coding & Keep Exploring the Universe! 🌌**
