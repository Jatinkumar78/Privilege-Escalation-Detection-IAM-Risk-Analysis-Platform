# 🛡️Privilege Escalation Detection & IAM Risk Analysis
Platform

A web-based security analysis tool that models Identity and Access Management (IAM) as a graph to detect:

- Privilege escalation paths  
- Over-privileged accounts  
- Conflicting roles (Separation of Duties violations)  
- MITRE ATT&CK mapped risk insights  

Built using Flask + NetworkX with dynamic JSON ingestion and interactive graph visualization.

---

## 🚀 Problem Statement

In enterprise environments, misconfigured IAM structures can allow low-privileged users to escalate to administrative access through hidden inheritance chains.

This tool transforms IAM configurations into a graph model and automatically detects structural risks.

---

## 🧠 Core Features

### ✅ Dynamic JSON Ingestion
Upload a dataset containing:
- Users  
- Roles  
- Permissions  
- Role inheritance  

Dashboard updates instantly based on uploaded file.

### ✅ Privilege Escalation Detection
- Models role inheritance as a directed graph  
- Uses shortest-path traversal to detect paths to `admin`  
- Assigns severity based on number of hops  

### ✅ Over-Privileged Account Detection
Flags users with:
- Admin access (direct or inherited)  
- High-risk permissions such as:
  - `assign_roles`
  - `modify_groups`
  - `reset_passwords`

### ✅ Conflict Detection (Separation of Duties)
Detects:
- Conflicting role combinations  
- Conflicting permission combinations  

### ✅ MITRE ATT&CK Mapping
Risky permissions are mapped to:
- Technique ID  
- Tactic  
- Description  

### ✅ Interactive Graph Visualization
- Users and roles displayed visually  
- Inheritance chains shown as edges  
- Zoom, drag, and hover for metadata  

---

## 🏗️ Architecture

IAM JSON Dataset  
        ↓  
Validation Layer  
        ↓  
Graph Construction (NetworkX)  
        ↓  
Escalation & Risk Detection Engine  
        ↓  
Structured Risk Report  
        ↓  
Graphical Visualization (vis-network)  

---

## 📁 Project Structure

```
iam-privilege-detector/
│
├── app.py
├── iam_data.json
├── mitre_map.json
├── requirements.txt
├── README.md
│
├── uploads/
│
└── templates/
    ├── index.html
    ├── graph.html
    └── playbook.html
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repository

```
git clone https://github.com/YOUR_USERNAME/iam-privilege-detector.git
cd iam-privilege-detector
```

### 2️⃣ Create Virtual Environment

**Windows**
```
python -m venv venv
venv\Scripts\activate
```

**Mac/Linux**
```
python3 -m venv venv
source venv/bin/activate
```

### 3️⃣ Install Dependencies

```
pip install -r requirements.txt
```

### 4️⃣ Run Application

```
python app.py
```

Open in browser:

http://127.0.0.1:5000

---

## 📄 Expected JSON Format

```
{
  "users": [
    {"name": "alice", "roles": ["support_staff"]}
  ],
  "roles": {
    "support_staff": {
      "permissions": ["view_tickets"],
      "inherits": ["group_editor"]
    },
    "group_editor": {
      "permissions": ["modify_groups"],
      "inherits": ["admin"]
    },
    "admin": {
      "permissions": ["full_access"],
      "inherits": []
    }
  }
}
```

---

## 🧪 Use Cases

- Security audits  
- IAM architecture reviews  
- Red team / blue team simulations  
- Hackathon security prototype  
- Academic cybersecurity projects  

---

## 🔒 Disclaimer

Use only in authorized environments.  
Intended for educational and research purposes.

---

## 👨‍💻 Author & Developer

Your Name - JATIN KUMAR
            NISARG CHASMAWALA (SHROFF)
            SANTHAKUMAR PARIVALLAL
Cybersecurity Project – Privilege Escalation Detection & IAM Risk Analysis
Platform
