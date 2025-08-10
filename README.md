# Smart Attendance Monitoring (SAM)

A Face Recognition-Based Attendance Management System that:
- Uses real-time face detection and recognition to mark attendance.
- Automatically logs present students into a CSV file.
- Tracks absentees and bunkers.
- Uploads attendance to a MySQL database.
- Provides a web dashboard to view attendance reports by date.

---

## 📁 Project Structure

SAM/
├── train/ # Folder with face images of students

├── student-dashboard.html # Frontend web interface

├── fetchReport.php # Backend PHP script to retrieve data

├── attendance_db.sql # SQL structure for MySQL database

├── absentees.csv # Generated absentees list

├── bunk.csv # Generated bunkers list

├── [DD-MM-YY].csv # Daily attendance CSVs

├── face_attendance.py # Face recognition attendance script



## 🧠 Prerequisites

- Python 3.8 or higher
- XAMPP installed (for Apache and MySQL)
- Webcam enabled
- Required Python packages:
pip install face_recognition opencv-python numpy pandas


## 🎯 STEP 1: Setup MySQL Database (XAMPP)

1. Launch **XAMPP Control Panel**.
2. Start **Apache** and **MySQL**.
3. Open `http://localhost/phpmyadmin`.
4. Create a new database named:
attendance_db


5. Create a table inside `attendance_db`:

``CREATE TABLE attendance (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  timestamp TIME,
  date DATE
);``

## 🤖 STEP 2: Face Recognition Script (Python)
Place student face images inside the train/ folder.

The file name should be the student's name (e.g., John.jpg).

Open a terminal in the project folder.

Modify the scheduled time inside face_attendance.py:

``if current_time == "09:00":  # Modify as needed
    mg(1)``
    
Run the script:

``python face_attendance.py``

✅ This will:

Detect and recognize faces.

Create or update the attendance file for that period.

Update absentees.csv and bunk.csv.

Upload attendance into the MySQL database automatically.

## 🌐 STEP 3: Launch Web Dashboard
Option A: Using XAMPP
Place your student-dashboard.html and fetchReport.php in:

``C:\xampp\htdocs\SAM\``

Open browser:

``http://localhost/SAM/student-dashboard.html``

Fill in the form and select the date range. Click “View Report” to see the summary.

## 🗃 STEP 4: fetchReport.php Setup
Make sure fetchReport.php contains the correct credentials:

``$host = 'localhost';
$user = 'root';
$password = '';  // Change if you’ve set a password
$database = 'attendance_db';``

## ⚙️ Features
Detects students only once per session

Calculates attendance percentage based on CSVs

Generates real-time reports on the web dashboard

Absentee list and bunkers are updated dynamically

## 📌 Notes
Ensure the webcam is working and accessible to Python.

Change session times in the script if needed.

Web report uses only startDate and endDate for filtering.

The database will only store attendance entries from the current session.

All times and dates are based on system time.

## 🛠️ Future Enhancements
Export full report as PDF or Excel

Admin panel for managing student list

Notification system for absentees
