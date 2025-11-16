# 🚀 Python Flask App Deployment on Ubuntu (AWS EC2)  
A simple and production-ready **Python Flask Web Application** deployed on an **Ubuntu EC2 instance** using **Gunicorn** and **(optional) Nginx**.

---

## 📝 **📌 Project Description**
This project demonstrates how to deploy a **Python Flask Application** on an **Ubuntu EC2 server** using:

- ✔️ Python 3  
- ✔️ Flask  
- ✔️ Virtual Environment (venv)  
- ✔️ Gunicorn  
- ✔️ Ubuntu / EC2  
- ✔️ (Optional) Nginx for reverse proxy  

Perfect for beginners learning cloud + backend deployment. 🎉

---

## 🧰 **⚙️ Tech Stack**
| Component | Technology |
|----------|------------|
| Language | Python 3 |
| Framework | Flask |
| Web Server | Gunicorn |
| OS | Ubuntu (EC2) |
| Optional Reverse Proxy | Nginx |
| Dependency Manager | pip / requirements.txt |

---

# 📁 **Project Structure**
python-app/
│── app.py
│── requirements.txt
│── myenv/ # Virtual environment

yaml
Copy code

---

# 🛠️ **Complete Setup Steps (Ubuntu EC2)**

Follow these steps **in exact order** 👇

---

## 🔹 **1️⃣ Update Server**
```bash
sudo apt update -y
sudo apt upgrade -y
🔹 2️⃣ Check Python & Pip
bash
Copy code
python3 --version
pip --version
If pip missing:

bash
Copy code
sudo apt install python3-pip -y
🔹 3️⃣ Create Project Directory
bash
Copy code
mkdir python-app
cd python-app/
🔹 4️⃣ Create Required Files
bash
Copy code
touch app.py
touch requirements.txt
ls
🔹 5️⃣ Edit app.py
Example Flask app:

python
Copy code
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello from Flask on EC2!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
🔹 6️⃣ Edit requirements.txt
text
Copy code
flask
gunicorn
🔹 7️⃣ Install Dependencies
bash
Copy code
pip install -r requirements.txt
🔹 8️⃣ Create Virtual Environment
bash
Copy code
sudo python3 -m venv myenv
sudo bash myenv/bin/activate
(Your prompt changes to)

scss
Copy code
(myenv) ubuntu@ip-xx-xx-xx-xx
🔹 9️⃣ Run Flask App (Test)
bash
Copy code
python3 app.py
Open in browser:
http://YOUR_EC2_PUBLIC_IP:5000

🔥 Production Deployment with Gunicorn
🔹 10️⃣ Run Gunicorn
bash
Copy code
gunicorn -b 0.0.0.0:5000 app:app --daemon
Gunicorn now runs app in background.

📌 (Optional) Enable Gunicorn as System Service
Create service file:

bash
Copy code
sudo nano /etc/systemd/system/gunicorn.service
Paste:

ini
Copy code
[Unit]
Description=Gunicorn Service
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/python-app
Environment="PATH=/home/ubuntu/python-app/myenv/bin"
ExecStart=/home/ubuntu/python-app/myenv/bin/gunicorn -b 0.0.0.0:5000 app:app

[Install]
WantedBy=multi-user.target
Enable service:

bash
Copy code
sudo systemctl daemon-reload
sudo systemctl enable gunicorn
sudo systemctl start gunicorn
sudo systemctl status gunicorn
🌐 (Optional) Use Nginx Reverse Proxy
Install nginx:

bash
Copy code
sudo apt install nginx -y
Edit default site:

bash
Copy code
sudo nano /etc/nginx/sites-available/default
Add:

nginx
Copy code
server {
    listen 80;

    location / {
        proxy_pass http://127.0.0.1:5000;
    }
}
Restart Nginx:

bash
Copy code
sudo systemctl restart nginx
Now open:
http://YOUR_EC2_PUBLIC_IP

🎉 Deployment Completed Successfully!
Your Flask application is now:

🔥 Running on EC2

🔥 Served by Gunicorn

🔥 (Optional) Reverse proxied via Nginx

🔥 Fully production ready
