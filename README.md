# 🚀 aws-ec2-python-app
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
 
 │── readme.md

---

# 🛠️ **Complete Setup Steps (Ubuntu EC2)**

Follow these steps **in exact order** 👇

---

## 🔹 **1️⃣ Update Server**
```bash
sudo apt update -y
sudo apt upgrade -y
```bash
🔹 2️⃣ Check Python & Pip
```
python3 --version
pip --version
```bash
If pip missing:
```
sudo apt install python3-pip -y
```bash
🔹 3️⃣ Create Project Directory
mkdir python-app
cd python-app/
```bash
🔹 4️⃣ Create Required Files
touch app.py
touch requirements.txt
ls
```bash
🔹 5️⃣ Edit app.py and requirements.txt
```bash
🔹 7️⃣ Install Dependencies
pip install -r requirements.txt
```bash
🔹 8️⃣ Create Virtual Environment
sudo python3 -m venv myenv
sudo bash myenv/bin/activate
(Your prompt changes to)
(myenv) ubuntu@ip-xx-xx-xx-xx
```bash
🔹 9️⃣ Run Flask App (Test)
python3 app.py
```bash
Open in browser:
http://YOUR_EC2_PUBLIC_IP:5000
```bash
🔥 Production Deployment with Gunicorn

🔹 10️⃣ Run Gunicorn
gunicorn -b 0.0.0.0:5000 app:app --daemon
Gunicorn now runs app in background.

```bash
🎉 Deployment Completed Successfully!
Your Flask application is now:

🔥 Running on EC2
🔥 Served by Gunicorn
🔥 (Optional) Reverse proxied via Nginx
🔥 Fully production ready

```

## 👨‍💻 Author

**Prasad**  
🚀 Cloud & DevOps Enthusiast  
🔗 Passionate about AWS, EC2, S3, RDS, DevOps, and Full-Stack Development  
