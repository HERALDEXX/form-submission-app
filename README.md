# Form Submission App

A full-stack form submission application with PostgreSQL database, built with Node.js, Express, and vanilla JavaScript.

## 🌐 Live Demo

[View Live Application](https://form-submission-app-lme8.onrender.com/)

## 📋 Features

- ✅ Real-time form validation
- ✅ PostgreSQL database integration
- ✅ Toast notifications
- ✅ View all submissions
- ✅ Responsive design
- ✅ XSS protection

## 🚀 Quick Deploy to Render

### Prerequisites

- GitHub account
- Render account (free at [render.com](https://render.com))

### Deployment Steps

#### 1. Push Code to GitHub (if not already done)

```bash
git add .
git commit -m "Prepare for deployment"
git push origin main
```

#### 2. Create PostgreSQL Database on Render

1. Go to [Render Dashboard](https://dashboard.render.com/)
2. Click **"New +"** → **"PostgreSQL"**
3. Fill in details:
   - **Name**: `form-submission-db` (or any name)
   - **Database**: `form_submissions`
   - **User**: `form_user` (auto-generated)
   - **Region**: Choose closest to you
   - **Plan**: **Free**
4. Click **"Create Database"**
5. Wait for it to provision (1-2 minutes)
6. Copy the **Internal Database URL** (starts with `postgresql://`)

#### 3. Deploy Web Service on Render

1. Click **"New +"** → **"Web Service"**
2. Connect your GitHub repository: `HERALDEXX/form-submission-app`
3. Fill in details:
   - **Name**: `form-submission-app` (or any name)
   - **Region**: Same as database
   - **Branch**: `main`
   - **Root Directory**: Leave blank
   - **Runtime**: **Node**
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Plan**: **Free**

#### 4. Add Environment Variables

In the "Environment" section, add:

- **Key**: `DATABASE_URL`
- **Value**: Paste the Internal Database URL from step 2

#### 5. Deploy!

1. Click **"Create Web Service"**
2. Wait 2-3 minutes for deployment
3. Your app will be live at: `https://your-app-name.onrender.com`

### ⚠️ Important Notes

- **Free tier sleeps after 15 min of inactivity** - First request may take 30-60 seconds
- **750 hours/month free** - Plenty for personal projects
- **Database**: 90 days of inactivity before deletion (free tier)

---

## � Local Development

### Installation Steps

#### Step 1: Clone & Install

```bash
git clone https://github.com/HERALDEXX/form-submission-app.git
cd form-submission-app
npm install
```

#### Step 2: Install PostgreSQL

**Windows:**

1. Download from [postgresql.org](https://www.postgresql.org/download/windows/)
2. Install with default settings
3. Remember your postgres password
4. Default port: 5432

**Mac:**

```bash
brew install postgresql
brew services start postgresql
```

**Linux:**

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
```

#### Step 3: Create Database

```sql
# Access PostgreSQL
psql -U postgres

# Create database
CREATE DATABASE form_submissions;

# Exit
\q
```

#### Step 4: Configure Environment

```bash
# Copy example env file
cp .env.example .env

# Edit .env with your credentials
```

`.env` file:

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=form_submissions
PORT=3000
```

#### Step 5: Start Application

```bash
# Development mode (auto-restart)
npm run dev

# Production mode
npm start
```

#### Step 6: Test

Open browser: http://localhost:3000

---

## 🧪 API Testing

### Endpoints

**POST** `/api/submit` - Submit form

```bash
curl -X POST http://localhost:3000/api/submit \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","message":"Hello!"}'
```

**GET** `/api/submissions` - Get all submissions

```bash
curl http://localhost:3000/api/submissions
```

**GET** `/api/health` - Health check

```bash
curl http://localhost:3000/api/health
```

---

## 📦 Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: Node.js, Express.js
- **Database**: PostgreSQL
- **Notifications**: Toastify.js
- **Hosting**: Render.com

---

## 🔧 Troubleshooting

### Local Development Issues

**Database connection failed:**

- Check PostgreSQL is running: `pg_isready`
- Verify credentials in `.env`
- Ensure database exists: `psql -U postgres -l`

**Port already in use:**

- Change `PORT` in `.env` to 3001 or other
- Kill process: `lsof -ti:3000 | xargs kill` (Mac/Linux)

### Render Deployment Issues

**Build failed:**

- Check build logs in Render dashboard
- Ensure `package.json` has all dependencies
- Verify `npm start` script exists

**Database connection error:**

- Verify `DATABASE_URL` environment variable is set
- Check database is in same region as web service
- Ensure database is not suspended

**App sleeps/slow:**

- Normal for free tier - first request takes 30-60s
- Consider upgrading to paid tier for always-on

---

## � Project Structure

```
form-submission-app/
├── client/              # Frontend
│   ├── index.html      # Main HTML
│   ├── script.js       # Client-side logic
│   └── style.css       # Styling
├── server/             # Backend
│   ├── server.js       # Express server
│   └── db/
│       └── connection.js  # PostgreSQL connection
├── .env.example        # Environment template
├── .gitignore
├── package.json
└── README.md
```

---

## 👤 Author

**Herald Inyang**

- GitHub: [@HERALDEXX](https://github.com/HERALDEXX)

---

## 📄 License

ISC License - See package.json

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

**⭐ Star this repo if you find it helpful!**
