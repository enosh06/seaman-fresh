# Render Backend Deployment Guide

## 🚀 Step 3: Deploy Backend to Render

### Part A: Setup Database First (TiDB Cloud - 3 minutes)

**You MUST do this first** because the backend needs database credentials.

1. Go to: https://tidbcloud.com/free-trial
2. Sign up (free, no credit card required)
3. Click "Create Cluster" → Select "Serverless Tier" (Free)
4. Wait 2-3 minutes for cluster creation
5. Click "Connect" → Copy these values:
   - **Host**: (e.g., `gateway01.us-east-1.prod.aws.tidbcloud.com`)
   - **Port**: (usually `4000`)
   - **User**: (your username)
   - **Password**: (your password)
   - **Database**: (database name, usually `test`)

**IMPORTANT**: Keep these credentials - you'll need them in Part B!

---

### Part B: Deploy Backend to Render (5 minutes)

1. Go to: https://dashboard.render.com/
2. Sign up with GitHub (easiest)
3. Click **"New +"** → **"Web Service"**
4. Click **"Connect a repository"** → Select `enosh06/seaman-fresh`
5. **Configure the service:**

   **Basic Settings:**
   - **Name**: `seaman-fresh-api`
   - **Region**: Oregon (US West) - Free tier
   - **Branch**: `main`
   - **Root Directory**: `server`
   - **Runtime**: Node
   - **Build Command**: `npm install`
   - **Start Command**: `node index.js`
   - **Instance Type**: Free

6. **Environment Variables** (Click "Advanced" → "Add Environment Variable"):
   
   Add these 6 variables:
   
   ```
   DB_HOST = (paste from TiDB - Part A)
   DB_USER = (paste from TiDB - Part A)
   DB_PASS = (paste from TiDB - Part A)
   DB_NAME = (paste from TiDB - Part A)
   DB_PORT = 4000
   JWT_SECRET = your-super-secret-key-change-this-123
   ```

7. Click **"Create Web Service"**

8. Wait 5-10 minutes for deployment

9. **Copy your backend URL** (e.g., `https://seaman-fresh-api.onrender.com`)

---

### Part C: Update Vercel Environment Variables

Once your backend is deployed:

1. Go to Vercel Dashboard: https://vercel.com/dashboard
2. Click on **seaman-fresh-client** project
3. Go to **Settings** → **Environment Variables**
4. Edit `VITE_API_URL`:
   - Change from `http://localhost:5000`
   - To: `https://seaman-fresh-api.onrender.com` (your Render URL)
5. Click **"Save"**
6. Go to **Deployments** → Click **"Redeploy"**

7. Repeat for **seaman-fresh-admin** project

---

## ✅ Final Result

After all steps:
- ✅ Database: TiDB Cloud (running)
- ✅ Backend: https://seaman-fresh-api.onrender.com
- ✅ Client: https://seaman-fresh-client.vercel.app
- ✅ Admin: https://seaman-fresh-admin.vercel.app

**Your app is LIVE! 🎉**

---

## 📝 Important Notes

1. **First Request Delay**: Render free tier "sleeps" after 15 minutes of inactivity. First request may take 30-50 seconds.
2. **Database Setup**: You need to run your SQL schema on TiDB. Use a tool like DBeaver or HeidiSQL to connect and import `schema.sql`.
3. **CORS**: If you get CORS errors, the backend is already configured to allow your Vercel domains.
