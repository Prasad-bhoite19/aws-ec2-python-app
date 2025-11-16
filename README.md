# 🐍 Python Web App on AWS EC2 (Ubuntu)

Deploying a Python application on an **AWS EC2 Ubuntu server** using a **virtual environment**, running on **Port 5000**, and keeping the app alive in the **background with systemd**. Perfect for beginners learning cloud deployment ☁️🚀.

---

## 📁 Project Structure

python-app/
│── app.py

│── requirements.txt

│── README.md

---

## 🚀 Features

- 📦 Install dependencies using **pip + virtual environment**
- 🐧 Ubuntu-based EC2 deployment
- ⚙️ Run Python app on **Port 5000**
- 🔄 Keep the app running in **background** using systemd
- ☁️ Simple & clean deployment steps

---

# 📌 1. Launch EC2 Instance

- Select **Ubuntu 22.04 / 24.04**
- Instance Type: **t2.micro**
- Allow inbound rules:
  - **22** → SSH
  - **5000** → Python App

SSH into server:

ssh -i your-key.pem ubuntu@EC2_PUBLIC_IP

---

# 📌 2. Update Server

sudo apt update && sudo apt upgrade -y

---

# 📌 3. Install Python Tools

sudo apt install python3 python3-venv python3-pip -y

---

# 📌 4. Create Project Directory

mkdir ~/python-app
cd ~/python-app

Upload files:

- app.py  
- requirements.txt  

---

# 📌 5. Create Virtual Environment

python3 -m venv venv
source venv/bin/activate

---

# 📌 6. Install Requirements

pip install -r requirements.txt

---

# 📌 7. Run App Manually (Test)

python app.py

r

Open in browser:

http://EC2_PUBLIC_IP:5000

---

# 📌 8. Run App in Background Using systemd

Create service file:

sudo nano /etc/systemd/system/pythonapp.service

makefile
Paste:

[Unit]
Description=Python App Service
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/python-app
Environment="PATH=/home/ubuntu/python-app/venv/bin"
ExecStart=/home/ubuntu/python-app/venv/bin/python app.py
Restart=always

[Install]
WantedBy=multi-user.target

yaml
Copy code

Save & exit (CTRL+O, ENTER, CTRL+X)

---

# 📌 9. Enable & Start Service

sudo systemctl daemon-reload
sudo systemctl enable pythonapp
sudo systemctl start pythonapp
sudo systemctl status pythonapp

yaml
Copy code

You should see **active (running)**.

---

# 📌 10. Allow Port 5000 (Firewall)

sudo ufw allow 5000

yaml
Copy code

Make sure EC2 Security Group also allows **Port 5000**.

---

# 📌 11. Your App is Live 🎉

Visit:

http://EC2_PUBLIC_IP:5000

---

```python
🔧 Useful Commands
sudo systemctl restart pythonapp
Stop service
sudo systemctl stop pythonapp
View logs
powershell
Copy code
sudo journalctl -u pythonapp -f
🎉 Deployment Complete!
Your Python app is now:

✔ Running on EC2
✔ Using Virtual Environment
✔ Running on Port 5000
✔ Always running in background
✔ Ready for production
✔ Ready for GitHub 🚀

