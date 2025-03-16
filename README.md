# FastAPI  with AI-Powered RAG Pipeline

## 🚀 Project Overview
This FastAPI microservice provides:
- ✅ **User Authentication & Role-Based Access Control (RBAC)** (via JWT & Oso)
- ✅ **CRUD operations for User Profiles**
- ✅ **RAG (Retrieval-Augmented Generation) Pipeline** for querying uploaded documents
- ✅ **AI Integration using GPT-4o-mini**
- ✅ **File Upload Support** (PDF, DOCX, TXT)

## 🛠️ Tech Stack
- **FastAPI** - API framework
- **JWT (PyJWT)** - Authentication
- **Oso** - RBAC
- **OpenAI GPT-4o-mini** - AI Processing
- **pdfminer.six, python-docx** - Document Processing
- **SQLite/PostgreSQL** - Database

---

## ⚡ Getting Started

### 1️⃣ Clone the Repository
```bash
$ https://github.com/sharan122/Advanced-FastAPI-Service-with-AI-Integration.git
$ cd fastapi_app
```

### 2️⃣ Install Dependencies
```bash
$ pip install -r requirements.txt
```

### 3️⃣ Set Up Environment Variables
Create a `.env` file and add:
```ini
SECRET_KEY=your_secret_key
OPENAI_API_KEY=your_openai_api_key
DATABASE_URL=postgresql://username:password@localhost:5432/db_name  # Use PostgreSQL in production
```

### 4️⃣ Run the Application
```bash
$ uvicorn app.main:app --reload
```

### 5️⃣ Access the API
- Swagger UI: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- Redoc: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

## 📌 API Endpoints

### **Authentication & RBAC**
#### 🔐 Register a User
```http
POST /users
```
**Payload:**
```json
{
  "username": "testuser",
  "password": "securepass",
  "role" : "admin", #optional
}
```

#### 🔑 Login & Get Token
```http
POST /login
```
**Payload:**
```json
{
  "username": "testuser",
  "password": "securepass"
}
```

### **User Profile Management**
#### 🏠 Get User Profile
```http
GET /users/id
```
#### Edit Users
```http
PUT /users/id
{
  "username": "testuser",
  "email": "youremail"
}
```
#### delete Users
```http
DELETE /users/id
{
  "user_id : "id"
}
```

### **RAG Pipeline**
#### 📂 Upload Document
```http
POST /rag/upload/
```
**Payload:** `multipart/form-data` with a file

#### 🔍 Query a Document
```http
POST /rag/query/
```
**Payload:**
```json
{
  "filename": "sample.pdf",
  "question": "What is this document about?"
}
```
#### 🔍 RBAC
```http
POST /rbac/assaign-role
```
**Payload:**
```json
{
  "user_id": "id",
  "role": "admin"
}
```
---

