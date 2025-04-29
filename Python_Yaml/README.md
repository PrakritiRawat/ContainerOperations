# student-management-yaml

---

## 📌 Overview

Welcome to the **Student Management System**, a simple yet powerful Python application that reads and processes student data from a YAML file.

This script allows users to:
- View student records 📖
- Filter students based on GPA 📊
- Learn how to handle structured data in **Python** using **YAML**!

---

## 🚀 Features

- ✅ Read student data from a YAML file 📂
- ✅ Display all students with their details 👨‍🎓👩‍🎓
- ✅ Filter students based on minimum GPA 📈
- ✅ User-friendly terminal-based interaction 🖥️

---

## 🛠️ Prerequisites

Make sure you have the following installed:

- **Python** (>=3.6) 🐍
- **PyYAML** library 📜

---

## ⚙️ Installation

Install the required dependency:

```bash
pip install pyyaml
```


---

## 📄 Create the YAML File

Create a file named **`students.yaml`** with the following structure:

```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

✅ Feel free to modify or extend this dataset!

---

## 🏗️ Running the Application

1️⃣ Make sure `students.yaml` and `app.py` are in the **same directory**.

2️⃣ Run the script:

```bash
python app.py


3️⃣ Follow on-screen instructions to filter students based on minimum GPA.

---

## 🖥️ Expected Output

Example:

```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

✅ Works dynamically based on user input!

---

## 🎯 Customization Options

- 🔹 **Add or remove** student details easily inside `students.yaml`
- 🔹 Extend `app.py` to include **sorting features** (by name, GPA, etc.)
- 🔹 Implement **CRUD operations** (Create, Read, Update, Delete students dynamically)

---

# 🚀 Conclusion

This project demonstrates:

- 📖 Reading structured YAML data in Python
- 📊 Filtering and processing datasets
- 🖥️ Building interactive terminal applications

---


