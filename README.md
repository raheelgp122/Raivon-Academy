# 🎓 Raivon Academy

A free Learning Management System (LMS) for school students covering Computer Science, AI & Software Engineering.

## Project Structure

```
raivon-academy/
├── backend/          # FastAPI + SQLAlchemy + SQLite/PostgreSQL
│   ├── app/
│   │   ├── main.py           # App entry point
│   │   ├── database.py       # DB connection
│   │   ├── dependencies.py   # Auth dependency
│   │   ├── seed.py           # Course seed data (9 courses, 90+ lessons)
│   │   ├── models/
│   │   │   └── models.py
│   │   └── routers/
│   │       ├── auth.py
│   │       ├── courses.py
│   │       ├── enrollments.py
│   │       ├── progress.py
│   │       └── certificates.py
│   └── requirements.txt
├── frontend/         # React + Vite
│   ├── src/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
├── render.yaml       # One-click deploy to Render
└── README.md
```

---

## 🚀 Deploy in 5 Minutes (Recommended: Render + Vercel)

### Step 1 — Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/raivon-academy.git
git push -u origin main
```

---

### Step 2 — Deploy Backend on Render (Free)

1. Go to [render.com](https://render.com) → **New → Web Service**
2. Connect your GitHub repo
3. Set these settings:
   - **Root Directory:** `backend`
   - **Runtime:** Python 3
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `uvicorn app.main:app --host 0.0.0.0 --port $PORT`
4. Add environment variables:
   - `SECRET_KEY` → any long random string
   - `DATABASE_URL` → (leave blank for SQLite, or add Render PostgreSQL URL)
5. Click **Deploy** — your API will be at `https://raivon-api.onrender.com`

---

### Step 3 — Deploy Frontend on Vercel (Free)

1. Go to [vercel.com](https://vercel.com) → **New Project**
2. Import your GitHub repo
3. Set:
   - **Root Directory:** `frontend`
   - **Framework Preset:** Vite
4. Add environment variable:
   - `VITE_API_URL` → `https://raivon-api.onrender.com/api`
5. Click **Deploy** — your site is live!

---

## 💻 Local Development

### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
# API running at http://localhost:8000
# Docs at http://localhost:8000/docs
```

### Frontend

```bash
cd frontend
npm install
npm run dev
# App running at http://localhost:5173
```

---

## 📚 Courses Included (9 Total)

| # | Title | Category | Level |
|---|-------|----------|-------|
| 1 | Introduction to Computer Science | CS | Basics |
| 2 | Data Structures & Algorithms | CS | Intermediate |
| 3 | Advanced Algorithms & Complexity | CS | Advanced |
| 4 | AI for Beginners | AI | Basics |
| 5 | Machine Learning Fundamentals | AI | Intermediate |
| 6 | Deep Learning & Neural Networks | AI | Advanced |
| 7 | Web Development Basics | SE | Basics |
| 8 | Full-Stack Development with React & Node | SE | Intermediate |
| 9 | DevOps, Cloud & System Design | SE | Advanced |

---

## 🌍 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Create account |
| POST | `/api/auth/login` | Login |
| GET | `/api/auth/me` | Get current user |
| GET | `/api/courses` | List all courses |
| GET | `/api/courses/{id}/lessons` | Get lessons |
| GET | `/api/enrollments` | My enrollments |
| POST | `/api/enrollments` | Enroll in course |
| DELETE | `/api/enrollments/{id}` | Unenroll |
| GET | `/api/progress` | All progress |
| GET | `/api/progress/{course_id}` | Course progress |
| POST | `/api/progress` | Update progress |
| GET | `/api/certificates/{course_id}` | Get certificate |

---

## ⚙️ Environment Variables

### Backend
| Variable | Default | Description |
|----------|---------|-------------|
| `SECRET_KEY` | (hardcoded dev key) | JWT secret — **change in production!** |
| `DATABASE_URL` | `sqlite:///./raivon.db` | DB connection string |

### Frontend
| Variable | Default | Description |
|----------|---------|-------------|
| `VITE_API_URL` | `/api` (proxied) | Backend API base URL |
