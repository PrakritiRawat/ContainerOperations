# 🚢 evidently-docker-dashboard  🐳📊

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Ready-blue?logo=docker">
  <img src="https://img.shields.io/badge/Streamlit-App-orange?logo=streamlit">
  <img src="https://img.shields.io/badge/Evidently-AI-green">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python">
</p>


---

## 📌 Introduction
This guide walks through setting up an **Evidently AI-based Streamlit application** running inside a Docker container.

The application:
- 🧠 Uses **Evidently AI** for monitoring machine learning models.
- 📊 Provides an **interactive dashboard** via **Streamlit**.
- 📂 Organizes reports and projects efficiently.
- 🐳 Leverages **Docker** for easy deployment and environment management.

---

## 📂 Project Structure

```
📁 evidently-ai-streamlit
 ├── 📂 projects                # Different ML monitoring projects
 │    ├── 📂 project_1
 │    │    └── 📂 reports       # Monitoring reports
 │    ├── 📂 project_2
 │    │    └── 📂 reports
 │    └── ...
 │
 ├── 📂 src                     # Python scripts (UI and utilities)
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Helper functions
 │
 ├── 📂 static                  # Static assets (CSS, images)
 │    └── style.css             # Custom styling
 │
 ├── 📄 app.py                   # Main Streamlit application
 ├── 📄 Dockerfile               # Defines the containerized environment
 ├── 📄 requirements.txt         # Python dependencies
 ├── 📄 README.md                # Project documentation
```

---

## 📝 Main Application (Overview of `app.py`)

The `app.py` script:
- 📂 Loads available projects and reports dynamically.
- 🎯 Lets users select a project, period, and report.
- 🛠 Displays **Evidently AI** reports inside Streamlit.
- 🚨 Handles missing projects or reports gracefully.
- 🧩 Uses modular design with `src/ui.py` (UI) and `src/utils.py` (utilities).

### Key Functions:
- `display_sidebar_header()`: Renders navigation and branding in sidebar.
- `select_project()`: Lets users pick a project.
- `select_period()`: Allows selecting a reporting period.
- `select_report()`: Fetches reports available for the project.
- `display_report()`: Loads and shows the selected report dynamically.

---

## 🐳 Dockerfile (Containerizing the Streamlit App)

```dockerfile
# 🐍 Use official lightweight Python image
FROM python:3.10

# 📁 Set working directory
WORKDIR /app

# 📥 Copy and install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir --break-system-packages -r requirements.txt

# 📂 Copy the project files
COPY . /app/

# 📡 Expose Streamlit's default port
EXPOSE 8501

# 🚀 Launch the Streamlit app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

## 📋 Python Dependencies (`requirements.txt`)

```text
category_encoders==2.6.0
evidently==0.2.6
jupyter==1.0.0
jupyter_contrib_nbextensions==0.7.0
matplotlib==3.7.0
numpy==1.24.2
pandas==1.5.3
pyarrow==11.0.0
python-box==5.4.1
requests==2.28.2
streamlit==1.19.0
pyyaml==5.1
scikit-learn==1.2.1
scipy==1.10.1
seaborn==0.12.2
altair==4.0
```

✅ *Pinned versions ensure consistent environment builds.*

---

## 🛠 Steps to Run the Application

### 1️⃣ Clone the Repository and Navigate

```bash
git clone <repo-link>
cd "Evidently AI Sets Sail in Docker"
```

---

### 2️⃣ Build and Run Docker Containers

```bash
docker build -t evidently-streamlit .
docker run -p 8501:8501 evidently-streamlit
```

---

### 3️⃣ Access the Application

🌐 Open your browser and visit:  
[http://localhost:8501](http://localhost:8501)

---

## 🎯 Conclusion

✅ Deployed an **Evidently AI** dashboard using **Streamlit** inside **Docker**.  
✅ Implemented **dynamic project and report selection**.  
✅ Organized project using **modular code structure**.  
✅ Achieved **environment portability and scalability** using Docker.

---

## 🚀 Next Steps

🔒 Add user authentication for secured access to projects.  
📊 Implement report comparisons across different periods.  
☁️ Deploy the containerized app on **AWS EC2**, **GCP**, or **Azure** for cloud-based monitoring.

---

🎯 *Keep exploring Evidently AI + Streamlit and happy shipping, Captain Prakriti! 🚢🐳📊*

---
