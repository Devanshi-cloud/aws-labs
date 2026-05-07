## 💻 AWS CLI / Terminal Commands I used in this lab

I worked directly inside my Lightsail/Ubuntu server and configured everything step by step using Linux + AWS-related commands.

---

### 1. System update (base setup)

```bash
sudo apt update
```

👉 I refreshed my server package index so everything I install is up to date.

---

### 2. Install Python environment (for Django track)

```bash
sudo apt install python3-pip python3-venv -y
```

👉 I installed Python package manager and virtual environment tools.

---

### 3. Create isolated Django environment

```bash
python3 -m venv djangoenv
source djangoenv/bin/activate
```

👉 I created and activated a separate environment so my project dependencies don’t conflict with system packages.

---

### 4. Install Django framework

```bash
pip install django
```

👉 I installed Django inside my controlled environment.

---

### 5. Start Django server

```bash
python manage.py runserver 0.0.0.0:8000
```

👉 I exposed my Django application to the public network on port 8000.

---

### 6. Node.js setup (MERN stack)

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```

👉 I added Node.js repository to my system.

```bash
sudo apt install nodejs -y
```

👉 I installed Node.js runtime.

---

### 7. Backend initialization

```bash
npm init -y
```

👉 I created a Node.js project structure.

```bash
npm install express mongoose cors
```

👉 I installed required backend libraries for API + database communication.

---

### 8. Run backend server

```bash
node server.js
```

👉 I started my backend service and made it live on the configured port.

---

### 9. WordPress admin password retrieval (Bitnami instance)

```bash
cat /home/bitnami/bitnami_application_password
```

👉 I extracted the default WordPress admin password directly from the server.

---

## 🧠 One-line ownership summary

> I used Linux commands inside AWS Lightsail to set up environments, install frameworks (Django, Node.js), deploy applications, and retrieve WordPress credentials — effectively controlling both backend services and application runtime on my cloud server.
