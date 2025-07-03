# 🔐 Secure File Sharing System

A secure file-sharing system between two types of users: **Ops Users** and **Client Users**. The application is built using **Python REST APIs** with file-type restrictions, encrypted download URLs, and user verification.

---

## 🚀 Features

### 👤 Operation (Ops) User
- ✅ Login
- 📤 Upload Files (`.pptx`, `.docx`, `.xlsx` only)

### 👥 Client User
- 📝 Sign Up (returns secure **encrypted URL**)
- 📧 Email Verification
- 🔐 Login
- 📥 Download Files (via secure URL)
- 📂 View List of Uploaded Files

---

## 🔧 Tech Stack

| Layer          | Technology Used       |
|----------------|------------------------|
| Framework      | `FastAPI` / `Flask`    |
| Database       | `MongoDB` / `PostgreSQL` |
| Auth           | JWT / Token-Based Auth |
| Security       | Encrypted download URLs |
| File Storage   | Local / AWS S3         |
| Testing        | `Pytest` / `Unittest`  |

---

## 🧪 Test Cases (Examples)

### ✔️ Login Test (Ops & Client)
```python
def test_login_valid_user():
    response = client.post("/login", json={"email": "test@user.com", "password": "secret"})
    assert response.status_code == 200
```

### ✔️ Upload File Type Restriction
```python
def test_upload_file_invalid_type():
    with open("file.txt", "rb") as f:
        response = client.post("/upload", files={"file": f})
    assert response.status_code == 400
```

### ✔️ Secure Download Link Generation
```python
def test_download_secure_url():
    response = client.get("/download-file/{file_id}")
    assert "download-link" in response.json()
```

---

## 🔐 Security & Access Control

- Encrypted download links via UUID + Hash
- Only **Client Users** can access download URLs
- Role-based access checks on endpoints
- Email verification required before login

---

## 📥 API Endpoints Summary

| Method | Endpoint                     | Access       | Description                         |
|--------|------------------------------|--------------|-------------------------------------|
| POST   | `/login`                     | Ops/Client   | User Login                          |
| POST   | `/upload`                    | Ops only     | Upload file (`docx`, `pptx`, `xlsx`)|
| POST   | `/signup`                    | Public       | Client signup                       |
| GET    | `/verify-email?token=...`    | Public       | Email verification                  |
| GET    | `/download-file/{id}`        | Client only  | Get secure download URL             |
| GET    | `/files`                     | Client only  | List all uploaded files             |

---

## 🧑‍💻 How to Run Locally

```bash
# Clone the repository
git clone https://github.com/your-username/secure-file-sharing.git
cd secure-file-sharing

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the app (FastAPI example)
uvicorn main:app --reload
```

---

## 🌐 Deployment Plan (Production Ready)

- 🚀 **Cloud Hosting**: Render, Railway, Heroku, or AWS EC2
- 🐳 **Dockerize** the application for platform consistency
- 🔐 **Use Gunicorn + Uvicorn** for serving FastAPI or Gunicorn for Flask
- ☁️ **AWS S3 / Firebase Storage** for file handling in production
- 🔒 **TLS/SSL**: Use Let’s Encrypt or Cloudflare for HTTPS
- 📈 **Monitoring**: Use Sentry, Prometheus, or similar tools

---

## 📦 Postman Collection

Ensure the Postman collection includes:
- Signup
- Login
- Upload
- Download URL generation
- Email verification (mock or live)
- File listing

📁 Include the exported file in your repo as:
```
postman_collection.json
```

---

## 📂 Repository Structure

```
secure-file-sharing/
│
├── app/
│   ├── main.py
│   ├── models.py
│   ├── routes/
│   ├── controllers/
│   ├── utils/
│
├── tests/
│   ├── test_auth.py
│   ├── test_upload.py
│
├── postman_collection.json
├── requirements.txt
└── README.md
```

---

## 📧 Contact

For any queries, email: **dk8400663713@gmail.com**

---

> _"Security is not a product, but a process."_ – Bruce Schneier
