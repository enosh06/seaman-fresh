# How to Create a TiDB Serverless Cluster (Free Database)

## 📋 Step-by-Step Guide with Screenshots

### Step 1: Sign Up (1 minute)
1. Go to: https://tidbcloud.com/free-trial
2. Click **"Start Free"** or **"Sign Up"**
3. Sign up with:
   - GitHub (easiest - one click)
   - OR Google
   - OR Email

### Step 2: Verify Email (if using email)
1. Check your email inbox
2. Click the verification link
3. Return to TiDB Cloud

### Step 3: Create Your First Cluster (2 minutes)

Once logged in, you'll see the dashboard:

1. **Click "Create Cluster"** (big green button)

2. **Choose Cluster Type:**
   - Select **"Serverless"** (NOT Dedicated)
   - This is the FREE tier - no credit card required
   - Click **"Create"**

3. **Configure Cluster:**
   
   **Cluster Name:**
   - Enter: `seaman-fresh-db` (or any name you like)
   
   **Cloud Provider:**
   - Select: **AWS** (recommended)
   
   **Region:**
   - Select: **US East (N. Virginia)** or closest to you
   - Free tier is available in most regions
   
   **Cluster Tier:**
   - Should show: **"Serverless Tier - Free"**
   - Storage: 5 GB (free)
   - No payment method required

4. **Click "Create"** button at the bottom

### Step 4: Wait for Cluster Creation (2-3 minutes)
- You'll see a progress screen
- Status will change from "Creating" → "Available"
- **Don't close the page!**

### Step 5: Get Connection Details (IMPORTANT!)

Once the cluster shows **"Available"**:

1. Click **"Connect"** button on your cluster

2. You'll see a connection dialog with:
   
   **Connection String** (looks like this):
   ```
   mysql -u '<username>' -h <host> -P 4000 -D test -p
   ```

3. **COPY AND SAVE THESE VALUES:**

   📝 **Write these down or save in a text file:**
   
   ```
   Host: gateway01.us-east-1.prod.aws.tidbcloud.com
   Port: 4000
   User: <your-username>
   Password: <click "Generate Password" or use the one shown>
   Database: test
   ```

4. **Generate Password:**
   - Click **"Generate Password"** button
   - **COPY IT IMMEDIATELY** - you can't see it again!
   - Save it in a safe place

### Step 6: Test Connection (Optional but Recommended)

You can test the connection using:

**Option A: TiDB Cloud SQL Editor (Easiest)**
1. In TiDB dashboard, click **"SQL Editor"**
2. Click **"Connect"**
3. Try running: `SHOW DATABASES;`
4. If it works, you're connected! ✅

**Option B: MySQL Client**
If you have MySQL installed:
```bash
mysql -u 'your-username' -h your-host -P 4000 -D test -p
```
Enter your password when prompted.

---

## ✅ What You Should Have Now:

A text file with these 5 values:
```
DB_HOST=gateway01.us-east-1.prod.aws.tidbcloud.com
DB_PORT=4000
DB_USER=your-username-here
DB_PASS=your-password-here
DB_NAME=test
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "No Create Cluster Button"
**Solution:** You might need to verify your email first. Check your inbox.

### Issue 2: "Payment Method Required"
**Solution:** You selected "Dedicated" instead of "Serverless". Go back and select Serverless.

### Issue 3: "Can't See Password"
**Solution:** Click "Generate Password" button. Copy it IMMEDIATELY - it won't show again.

### Issue 4: "Connection Refused"
**Solution:** 
- Make sure you're using Port 4000 (not 3306)
- Check if your cluster status is "Available" (not "Creating")

---

## 📊 Import Your Database Schema

After creating the cluster, you need to import your tables:

### Method 1: Using TiDB SQL Editor (Easiest)
1. In TiDB Dashboard → Click **"SQL Editor"**
2. Open your `schema.sql` file
3. Copy all the SQL code
4. Paste into SQL Editor
5. Click **"Run"**

### Method 2: Using MySQL Workbench or DBeaver
1. Download DBeaver: https://dbeaver.io/download/
2. Create new connection with your TiDB credentials
3. Import your `schema.sql` file

---

## 🎯 Next Step

Once you have your 5 database credentials, go back to the Render deployment and add them as environment variables!
