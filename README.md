# 👨‍💼 Face Recognition Attendance System using Flask & OpenCV

A smart attendance management system 🎯 built using **Flask**, **OpenCV**, and **SQLite**.  
This app captures faces via webcam, recognizes users using a trained KNN model 🧠, and records attendance in a database automatically.  
It supports multiple roles: **Admin**, **HR**, and **Employee** with secure authentication 🔐.

---

## 🚀 Features

✅ **User Authentication**
- Secure login/signup system using hashed passwords (`werkzeug.security`)
- Role-based access (Admin / HR / Employee)

✅ **Face Recognition Attendance**
- Uses `OpenCV` Haar Cascade classifier for face detection
- Trains a K-Nearest Neighbors (KNN) model on collected face images
- Automatically marks attendance with timestamp ⏰

✅ **Admin Panel**
- Add or delete users
- View and manage employee records

✅ **HR Dashboard**
- View daily attendance reports 📊
- Download attendance report as Excel (`.xlsx`)

✅ **Employee Dashboard**
- Mark attendance via webcam in real-time 🎥
- See personal attendance logs

---

## 🏗️ Project Structure

📁 Face-Recognition-Attendance/
├── app.py # Main Flask application
├── database.db # SQLite database file
├── haarcascade_frontalface_default.xml # Pre-trained Haar cascade for face detection
├── static/
│ ├── faces/ # Contains user face image folders
│ ├── face_recognition_model.pkl # Trained KNN model
│ ├── attendance_report.xlsx # Generated attendance reports
├── templates/
│ ├── login.html
│ ├── signup.html
│ ├── admin.html
│ ├── employee.html
│ ├── hr_dashboard.html
│ ├── attendance.html
│ └── reports.html
└── Attendance/ # Directory for daily attendance records

pgsql
Copy code

---

## 🧩 Database Schema (SQLite)

### 🗃️ `users` Table
| Column Name | Type | Description |
|--------------|------|-------------|
| `id` | INTEGER | Auto-incremented unique ID |
| `username` | TEXT | Unique username (e.g., HR, admin, employee) |
| `password` | TEXT | Hashed password |
| `role` | TEXT | Role type (`admin`, `hr`, or `user`) |

> 💡 A default HR account (`username: HR`, `password: HR`) is automatically created on first run.

---

### 🗂️ `attendance` Table
| Column Name | Type | Description |
|--------------|------|-------------|
| `id` | INTEGER | Auto-incremented record ID |
| `name` | TEXT | Full name of the employee |
| `roll` | TEXT | Unique employee ID / roll number |
| `time` | TEXT | Attendance marking time (HH:MM:SS) |
| `date` | TEXT | Attendance date (DD-MM-YY) |

---

## ⚙️ Installation & Setup

### 🧱 Prerequisites
- Python 3.8 or higher
- pip installed
- Webcam access enabled

### 📦 Install Dependencies
```bash
pip install flask opencv-python numpy pandas scikit-learn joblib werkzeug
▶️ Run the App
bash
Copy code
python app.py
Then open 🌐 http://127.0.0.1:5000 in your browser.

🧠 How It Works
Register User → Capture 50 face samples per user.

Train Model → Uses KNN classifier (n_neighbors=5) to encode faces.

Start Attendance → Captures frames and matches faces with trained model.

Mark Attendance → Inserts record into attendance table if not already marked.

Reports → HR can filter attendance by date range and download reports.

🔐 Roles & Permissions
Role	Access Level
👑 Admin	Add/delete users, manage system
💼 HR	View/download attendance reports
🙋 Employee	Mark attendance via webcam

🛠️ Tech Stack
Category	Technology
🧱 Backend	Flask (Python)
🧠 ML Model	K-Nearest Neighbors (scikit-learn)
🗄️ Database	SQLite
👁️ Computer Vision	OpenCV
🧾 Reports	pandas, Excel output
🔒 Security	werkzeug (Password Hashing)

📊 Example Attendance Output
Date	Name	Roll	Time
09-11-25	Biplov	001	09:12:35
09-11-25	Ramila	002	09:14:02

💡 Future Enhancements
Add face re-training scheduler 📅

Support cloud-based DB (e.g., PostgreSQL)

Integrate with company HRMS

Add real-time dashboard analytics 📈

🧾 License
This project is released under the MIT License.
Feel free to use, modify, and distribute it! 🤝

👨‍💻 Author
Biplov Paneru
📍 Nepal | 🌐 biplovp.com.np
🔗 GitHub | LinkedIn

⭐ If you find this project useful, don’t forget to give it a star on GitHub! 🌟
