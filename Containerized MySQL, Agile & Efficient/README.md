# 🐬 Setting Up MySQL in a Docker Container with a Custom Initialization Script 🚀

## 📌 Prerequisites
Before you begin, make sure you have the following:
- ✅ **Docker Installed**: Install Docker on your system ([Get Docker](https://docs.docker.com/get-docker/)).
- ✅ **Docker Running**: Ensure the Docker engine is up and active.
- ✅ **SQL Initialization Script**: Create an SQL file (e.g., `Prakriti_demo.sql`) containing your database and table setup.

---

## 📂 Project Directory Structure
Organize your project files like this:

```
project-directory/
│── Dockerfile
│── Prakriti_demo.sql
```

🔖 *Keeping files structured ensures a clean and efficient build process.*

---

## 🛠️ Step 1: Create the Dockerfile
Inside your project directory, create a `Dockerfile` with the following content:

```dockerfile
# 🏗️ Start from the official MySQL image
FROM mysql:latest

# 📥 Copy the SQL initialization script into the container
COPY Prakriti_demo.sql /docker-entrypoint-initdb.d/

# 📡 Expose MySQL's default port
EXPOSE 3306
```

⚙️ *This tells Docker to spin up a MySQL server and automatically execute your custom SQL script during initialization.*

---

## 📝 Step 2: Create the SQL Initialization Script
Create a file named `Prakriti_demo.sql`:

```sql
CREATE DATABASE Prakriti;
USE Prakriti;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

INSERT INTO students (name, age) VALUES 
('Alice', 22), 
('Bob', 24);
```

🗂 *This script will automatically create a `Prakriti` database and populate the `students` table when the container starts.*

---

## 🏗️ Step 3: Build the Custom Docker Image
Build your Docker image by running:

```bash
docker build -t mysql-prakriti-custom .
```

🛠️ *This creates a custom image tagged as `mysql-prakriti-custom`.*

---

## 🚀 Step 4: Launch the MySQL Container
Run the following command to start a container using your custom image:

```bash
docker run --name mysql-prakriti-container -e MYSQL_ROOT_PASSWORD=root -d mysql-prakriti-custom
```

### 📖 Breakdown:
- 📦 `--name mysql-prakriti-container`: Names the container.
- 🔑 `-e MYSQL_ROOT_PASSWORD=root`: Sets the root password.
- 🔄 `-d`: Runs the container in detached (background) mode.
- 🖼️ `mysql-prakriti-custom`: Specifies the custom image to use.

---

## 🔎 Step 5: Access the Container Shell
To interactively access your running container:

```bash
docker exec -it mysql-prakriti-container bash
```

📂 *You'll enter the container's internal bash shell.*

---

## 💻 Step 6: Connect to MySQL Server
Inside the container, log into the MySQL server:

```bash
mysql -u root -p
```
🔑 *Enter the password (`root`) when prompted.*

---

## 📊 Step 7: Verify the Database and Tables
Once logged in:

- 🔍 List all databases:

```sql
SHOW DATABASES;
```

- 🔄 Switch to the `Prakriti` database:

```sql
USE Prakriti;
```

- 📈 Display the contents of the `students` table:

```sql
SELECT * FROM students;
```

✨ *You should see your pre-populated data.*

---

## 🎯 Final Result
You have now:
- 🛠️ Built a custom MySQL Docker image.
- 🚀 Initialized a database (`Prakriti`) and a table (`students`) automatically.
- ✅ Verified the setup successfully.

---

## 📚 Bonus Tips
- 🧹 **To stop the container**:  
  ```bash
  docker stop mysql-prakriti-container
  ```
- 🗑️ **To remove the container**:  
  ```bash
  docker rm mysql-prakriti-container
  ```
- 🔄 **To rebuild the image after changes**:  
  ```bash
  docker build --no-cache -t mysql-prakriti-custom .
  ```

---

## 🌟 Conclusion
> **Congratulations!** 🚀  
> You have successfully set up a fully functional MySQL database inside a Docker container with automatic initialization using your custom script! This setup is perfect for rapid prototyping, development environments, and learning purposes.

🎨 *Happy coding, and keep building amazing things!* ✨

---