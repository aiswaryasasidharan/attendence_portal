This is the beginning of my project lets go

to make virtual environment we used uv

```
uv init
```

```
uv venv venv
```

```text
Attendence/
│
├── admin.py              → Admin dashboard logic
├── analytics.py          → Attendance analytics
├── clients.py            → Supabase client builder
├── config.py             → Environment/config loader
├── logger.py             → Central logging system
├── student.py            → Student attendance UI + logic
├── supabase_client.py    → (deprecated now, merged into clients)
├── utils.py              → Shared helpers (dates, etc.)
│
├── admin_main.py         → Streamlit entry for admin
├── student_main.py       → Streamlit entry for student
│
├── logs/
│   └── app.log           → Combined logs
│
├── pyproject.toml        → Project dependencies
├── requirements.txt      → For pip installs
├── versions.py           → Prints package versions
```

### How real logs look like

```text

| INFO | Attendence.student | student.py:45 | show_student_panel() | Fetching open classes from Supabase…

| DEBUG | Attendence.clients | clients.py:22 | create_supabase_client() | Supabase client initialized successfully.

| ERROR | Attendence.student | student.py:78 | show_student_panel() | Failed to fetch roll map

| ERROR | Attendence.student | student.py:78 | show_student_panel() | Traceback (most recent call last):

| ERROR | Attendence.student | student.py:78 | show_student_panel() |   File "Attendence/student.py", line 65, in show_student_panel

| ERROR | Attendence.student | student.py:78 | show_student_panel() |     roll_map_response = supabase.table("roll_map")...

| ERROR | Attendence.student | student.py:78 | show_student_panel() | postgrest.exceptions.APIError: invalid input syntax for integer: ""

| WARNING | Attendence.admin | admin.py:102 | toggle_classroom() | Classroom '8 C' was already open.

| INFO | Attendence.admin | admin.py:150 | download_attendance_report() | Report generated: attendance_matrix_8C_20251201.csv


```

# 🧠 Smart Attendance System

A modular and secure web-based attendance tracking system for classrooms, built using **Streamlit**, **Supabase**, and **GitHub**. The system supports **role-based access** with separate panels for **Admins** and **Students**.

---

## 🔐 Admin Panel

> 🔓 Accessible only with valid admin credentials
---
### 📚 Class Management

* ➕ **Create Class** with default code and daily attendance limit
* 📂 **Select and Manage Classes**
* ⚙️ **Update Attendance Code & Daily Limit**
* 🔃 **Toggle Attendance Status** (Open/Close)
* 🚫 Only **one class** can be open for attendance at a time
---
### 📈 Attendance Matrix

* 📊 View attendance in a **date-wise pivot table**
* ✅ "P" entries marked in green | ❌ "A" entries marked in red
* ⬇️ **Download matrix as CSV**
* 🚀 **Push CSV to GitHub repository** (auto-commits with timestamped filenames)
---
### 🗑️ Delete Class

* Permanently deletes:

  * Class settings
  * Attendance records
  * Roll-number mappings
* ❗ Requires `"DELETE"` confirmation to proceed

---

## 🎓 Student Panel

> 🧑‍🎓 No login required — attendance can only be marked when a class is **open**
---
### 📝 Submit Attendance

* 🔍 **Select open class**
* 🧾 **Enter Roll Number & Name**

  * Name gets **locked to roll number** after first submission
 ---
 
* 🔐 **Enter Valid Attendance Code**
  
* ❌ Blocked if:

  * Wrong code is entered
  * Student already marked attendance for the day
  * Class has reached its daily attendance limit
---
### 📋 View Personal Attendance

* 🧑‍💼 **Displays only student's own records**
* 📅 Shows attendance across all dates in a structured table
* ✅ Filtered view ensures data privacy and focus

---

## ⚙️ Tech Stack

| Layer         | Technology       |
| ------------- | ---------------- |
| Frontend      | Streamlit        |
| Database      | Supabase         |
| Backend Logic | Python + Pandas  |
| Storage       | GitHub API (CSV) |
| Visualization | Matplotlib       |

---


