

# 🐳 streamlit-in-docker

---

## 🚀 Prerequisites
Before setting up the environment, ensure you have the following installed on your system:

- 🐳 **Docker** (Make sure the Docker daemon is running)
- 🐍 **Python 3.9+** (Verify with `python --version`)
- 📦 **pip** (Verify with `pip --version` and ensure it's updated)
- 📊 **Basic knowledge of Streamlit** (for building UI components)

---

## 📂 Project Directory Structure

```
project_root/
│── .streamlit/
│   └── config.toml
│── src/
│   └── main.py
│── Dockerfile
│── requirements.txt
│── README.md
```

✅ *Organized structure ensures clean builds and easy development.*

---

## 📜 File Descriptions

### 1️⃣ `.streamlit/config.toml`
Configures Streamlit's server behavior for optimal local development:

```toml
[server]
headless = true
runOnSave = true
fileWatcherType = "poll"
```

---

### 2️⃣ `src/main.py`
Contains the **core Streamlit application** including:

- 🏠 **Home Page**: Introduction to the app.
- 📊 **Data Explorer**: Upload and inspect CSV files interactively.
- 📈 **Visualization Page**: Generate dynamic charts and graphs.

---

### 3️⃣ `Dockerfile`
Defines the **Dockerized Streamlit environment**:

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app/
EXPOSE 8501
CMD ["streamlit", "run", "src/main.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

### 4️⃣ `requirements.txt`
Specifies Python dependencies:

```
streamlit
pandas
numpy
matplotlib
plotly
```

---

## ⚡ How to Run the Project

1️⃣ Navigate to the project directory:

```bash
cd path/to/project_root
```

---

2️⃣ Build the Docker image:

```bash
docker build -t streamlit-app .
```

---

3️⃣ Run the container:

```bash
docker run -p 8501:8501 streamlit-app
```

---

4️⃣ Access the application in your browser:  
🌐 [http://localhost:8501](http://localhost:8501)

---

## 🎯 Conclusion
✅ You now have a **fully functional, containerized Streamlit development environment** ready for fast prototyping and data app development!  
✅ Docker ensures **environment consistency**, while Streamlit provides **rapid UI deployment**.

---

🎨 **Happy Streamlit-ing inside Docker, Prakriti!** 🚀🐳

---
