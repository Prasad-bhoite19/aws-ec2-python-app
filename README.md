# 🐍 aws-ec2-python-app

This project demonstrates how to deploy a **Python Flask application** on an **Amazon Linux EC2 instance** using:

- Python3  
- `pip`  
- Virtual Environment (`venv`)  
- Gunicorn  
- Running service on **Port 5000**

This README contains **all steps extracted from your terminal commands.**

---

## 📁 Project Structure

python-app/

├── app.py

├── requirements.txt

└── README.md

---

## 🚀 Features

- Run Python Flask app on **Amazon Linux**
- Install dependencies with `pip`  
- Use **virtual environment (venv)**  
- Run app manually using Python  
- Deploy using **Gunicorn**  
- Serve on **0.0.0.0:5000**

---

# ⚙️ Installation & Setup (Amazon Linux)

Below are the exact steps you used, formatted into a clean guide.

---

## 1️⃣ Check Python & pip Versions

```bash
python3 --version
pip --version

2️⃣ Install pip (if missing)
sudo yum install python3-pip -y

Verify:
pip --version

3️⃣ Create Project Directory
mkdir python-app
cd python-app

4️⃣ Create Application Files
touch app.py
touch requirements.txt

5️⃣ Install Requirements
pip install -r requirements.txt

6️⃣ Create Virtual Environment
sudo python3 -m venv myenv
Activate venv:
sudo bash myenv/bin/activate

7️⃣ Test App (Manual Run)
python3 app.py

Visit in browser:
http://EC2-PUBLIC-IP:5000
Stop with CTRL+C.

🚀 Run App in Background (Gunicorn)
You ran:
gunicorn -b 0.0.0.0:5000 app:app --daemon

This:
Starts Flask app using Gunicorn
Binds it to 0.0.0.0:5000
Runs in background using --daemon

🔧 Useful Commands
Stop Gunicorn Process
Check Running Processes
ps aux | grep gunicorn

🎯 Next Improvements
Add systemd service for auto-start
Add Nginx reverse proxy on port 80
Deploy with SSL/HTTPS
Add logging and monitoring

✍️ Author: Prasad
