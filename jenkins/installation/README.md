# 🚀 Jenkins Installation on Linux (Ubuntu)

This guide walks you through installing the **LTS (Long Term Support)** version of Jenkins on an Ubuntu-based Linux system.

---

## 📋 Prerequisites

Before installing Jenkins, ensure Java is installed on your system.

### ✅ Step 1: Install Java (OpenJDK 21)

```bash
sudo apt update
sudo apt install fontconfig openjdk-21-jre
```

### 🔍 Verify Java Installation

```bash
java -version
```

Expected output:

```
openjdk version "21.0.7" 2025-04-15
OpenJDK Runtime Environment (build 21.0.7+6-Ubuntu-0ubuntu124.04)
OpenJDK 64-Bit Server VM (build 21.0.7+6-Ubuntu-0ubuntu124.04, mixed mode, sharing)
```

---

## ⚙️ Step 2: Install Jenkins (LTS Version)

### 📥 Add Jenkins Repository and Key

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### 🔄 Update Packages and Install Jenkins

```bash
sudo apt-get update
sudo apt-get install jenkins
```

---

## 🚦 Step 3: Start and Check Jenkins Service

```bash
sudo systemctl status jenkins
```

You should see output indicating that Jenkins is **active (running)**.

---

## 📎 Reference

- 🔗 Jenkins Official Installation Guide: [jenkins.io/doc/book/installing/linux](https://www.jenkins.io/doc/book/installing/linux/)

---

## ✅ Done!

Your Jenkins LTS is now installed and running on your Ubuntu server! 🎉

---

## 🚀 Step 4: Enable Jenkins to Start on Boot

To ensure Jenkins starts automatically when your server restarts, enable its systemd service:

```bash
sudo systemctl enable jenkins
```

This command configures Jenkins to launch on every system boot, ensuring your CI/CD pipeline stays active after reboots.

---

## 🌐 Step 5: Access Jenkins Web Interface

Once Jenkins is running, open your browser and go to:

```
http://<Your-Server-IP>:8080/
```

> Replace `<Your-Server-IP>` with the actual IP address of your Ubuntu server.

---

## 🔑 Step 6: Retrieve the Initial Admin Password

When you access Jenkins for the first time via the web interface, it will prompt you for an **Unlock Key**.

To get the key, run the following command on the server where Jenkins is installed:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

This command will output a long alphanumeric key. Copy and paste this into the Jenkins setup screen in your browser to proceed with the initial setup.

---

## ✅ Jenkins is Ready!

After entering the unlock key, Jenkins will guide you through:
- Installing recommended plugins
- Creating the first admin user
- Configuring basic system settings

You're now ready to start building with Jenkins! 🚀