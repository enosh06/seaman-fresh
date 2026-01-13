# Vercel Deployment - Quick Guide

## 🚀 Deploy Client (2 minutes)

### Step 1: Import Project
1. Go to: https://vercel.com/new
2. Click "Import Git Repository"
3. If prompted, authorize Vercel to access GitHub
4. Select: `enosh06/seaman-fresh`

### Step 2: Configure Client
- **Project Name**: `seaman-fresh-client`
- **Framework**: Vite (auto-detected)
- **Root Directory**: Click "Edit" → Select `client` folder
- **Build Settings**: (Leave as default)
  - Build Command: `npm run build`
  - Output Directory: `dist`

### Step 3: Environment Variables
Click "Environment Variables" and add:
- Key: `VITE_API_URL`
- Value: `http://localhost:5000` (temporary - we'll update after backend deployment)

### Step 4: Deploy
Click "Deploy" button and wait ~2 minutes

**Save the URL** you get (e.g., `https://seaman-fresh-client.vercel.app`)

---

## 🔧 Deploy Admin Panel (2 minutes)

### Step 1: Import Again
1. Go to: https://vercel.com/new
2. Select the SAME repository: `enosh06/seaman-fresh`

### Step 2: Configure Admin
- **Project Name**: `seaman-fresh-admin`
- **Framework**: Vite
- **Root Directory**: Click "Edit" → Select `admin-panel` folder

### Step 3: Environment Variables
Add TWO variables:
1. Key: `VITE_API_URL`
   Value: `http://localhost:5000` (temporary)

2. Key: `VITE_STORE_URL`
   Value: `https://seaman-fresh-client.vercel.app` (your client URL from above)

### Step 4: Deploy
Click "Deploy"

**Save this URL too** (e.g., `https://seaman-fresh-admin.vercel.app`)

---

## ✅ After Both Deploy Successfully

You'll have:
- ✅ Client: https://seaman-fresh-client.vercel.app
- ✅ Admin: https://seaman-fresh-admin.vercel.app
- ⏳ Backend: (Next step - Render.com)

**Note**: The apps won't fully work yet because the backend isn't deployed. That's Step 3!
