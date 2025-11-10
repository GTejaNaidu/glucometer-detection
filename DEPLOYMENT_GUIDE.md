# 🚀 Deployment Guide - GitHub & Streamlit Cloud

## Step-by-Step Guide to Deploy Your Application

---

## Part 1: Push to GitHub

### Step 1: Initialize Git Repository

Open Command Prompt in your project folder and run:

```bash
cd C:\Users\tejan\OneDrive\Desktop\OCR
git init
```

### Step 2: Add Files to Git

```bash
git add .
```

### Step 3: Create Initial Commit

```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
git commit -m "Initial commit: Advanced Glucometer Detection System"
```

### Step 4: Create GitHub Repository

1. Go to [GitHub.com](https://github.com)
2. Click the **"+"** icon (top right) → **"New repository"**
3. Fill in details:
   - **Repository name**: `glucometer-detection` (or your preferred name)
   - **Description**: "AI-powered glucometer reading detection system"
   - **Visibility**: Choose Public or Private
   - **DO NOT** initialize with README (we already have one)
4. Click **"Create repository"**

### Step 5: Connect Local to GitHub

Copy the commands from GitHub (they'll look like this):

```bash
git remote add origin https://github.com/YOUR_USERNAME/glucometer-detection.git
git branch -M main
git push -u origin main
```

**Replace `YOUR_USERNAME` with your actual GitHub username!**

### Step 6: Verify Upload

Refresh your GitHub repository page - you should see all your files!

---

## Part 2: Deploy to Streamlit Cloud

### Step 1: Go to Streamlit Cloud

1. Visit [share.streamlit.io](https://share.streamlit.io)
2. Click **"Sign in"** or **"Sign up"**
3. Sign in with your **GitHub account**

### Step 2: Authorize Streamlit

1. Click **"Authorize streamlit"** when prompted
2. Grant access to your repositories

### Step 3: Create New App

1. Click **"New app"** button
2. Fill in the deployment form:

   **Repository:**
   - Select your repository: `YOUR_USERNAME/glucometer-detection`
   
   **Branch:**
   - Select: `main`
   
   **Main file path:**
   - Enter: `b.py`
   
   **App URL (optional):**
   - Choose a custom subdomain or leave default
   - Example: `glucometer-detection.streamlit.app`

3. Click **"Deploy!"**

### Step 4: Wait for Deployment

- Initial deployment takes 2-5 minutes
- You'll see a progress indicator
- The app will automatically open when ready

### Step 5: Test Your App

1. Once deployed, you'll get a URL like:
   ```
   https://your-app-name.streamlit.app
   ```

2. Open the URL and test:
   - ✅ API key configuration screen
   - ✅ Login/Register
   - ✅ Upload image
   - ✅ Camera capture (requires HTTPS - works automatically on Streamlit Cloud)
   - ✅ Dashboard and analytics

---

## Part 3: Update Your App

### When You Make Changes:

```bash
# 1. Make your changes to the code
# 2. Stage the changes
git add .

# 3. Commit with a message
git commit -m "Description of your changes"

# 4. Push to GitHub
git push origin main
```

**Streamlit Cloud will automatically redeploy** when you push to GitHub!

---

## 🔧 Troubleshooting

### Issue: Git not recognized

**Solution:**
1. Install Git: [git-scm.com/download/win](https://git-scm.com/download/win)
2. Restart Command Prompt
3. Try again

### Issue: Authentication failed

**Solution:**
1. Use GitHub Personal Access Token instead of password
2. Go to GitHub → Settings → Developer settings → Personal access tokens
3. Generate new token with `repo` scope
4. Use token as password when pushing

### Issue: Streamlit deployment fails

**Common causes:**
1. **Missing requirements.txt** - Already created ✅
2. **Wrong main file** - Make sure it's `b.py`
3. **Large files** - Database will be created fresh on deployment
4. **Python version** - Streamlit Cloud uses Python 3.9+

**Solution:**
- Check deployment logs in Streamlit Cloud
- Fix errors and push again

### Issue: App crashes on startup

**Check:**
1. All dependencies in `requirements.txt`
2. No hardcoded file paths (use relative paths)
3. Database is created automatically
4. API key is entered by user (not hardcoded)

---

## 📱 Share Your App

Once deployed, share your app URL:
```
https://your-app-name.streamlit.app
```

**Features on Streamlit Cloud:**
- ✅ Free hosting
- ✅ Automatic HTTPS
- ✅ Camera access works
- ✅ Auto-redeploy on git push
- ✅ Custom domain support (paid plans)
- ✅ Password protection (paid plans)

---

## 🔒 Security Notes

### Important for Production:

1. **Database**: The SQLite database will be created fresh on each deployment
   - For persistent data, consider using external database (PostgreSQL, MongoDB)

2. **API Keys**: Users enter their own API keys
   - Keys are session-only (not saved)
   - Secure and private

3. **User Data**: 
   - Currently stored in SQLite
   - Resets on each deployment
   - Consider external database for production

---

## 💡 Pro Tips

### 1. Custom Domain
- Upgrade to Streamlit Cloud paid plan
- Add your custom domain
- Example: `app.yourdomain.com`

### 2. Environment Variables
Create `.streamlit/secrets.toml` for sensitive data:
```toml
# Don't commit this file!
[secrets]
admin_password = "your_secret"
```

### 3. Analytics
- Streamlit Cloud provides usage analytics
- Track visitors and performance
- Monitor errors

### 4. Multiple Environments
- Create branches: `dev`, `staging`, `main`
- Deploy each branch separately
- Test before pushing to main

---

## 📊 Monitoring

### Streamlit Cloud Dashboard:
- View app status
- Check logs
- Monitor resource usage
- Manage deployments

### Access Logs:
1. Go to Streamlit Cloud dashboard
2. Click on your app
3. View logs in real-time
4. Debug issues

---

## 🎉 Success Checklist

- [ ] Git repository initialized
- [ ] Files committed to Git
- [ ] GitHub repository created
- [ ] Code pushed to GitHub
- [ ] Streamlit Cloud account created
- [ ] App deployed successfully
- [ ] App URL accessible
- [ ] API key configuration works
- [ ] Login/Register works
- [ ] Image upload works
- [ ] Camera capture works (HTTPS)
- [ ] All features tested
- [ ] Shared with users

---

## 📞 Need Help?

### Resources:
- **Streamlit Docs**: [docs.streamlit.io](https://docs.streamlit.io)
- **GitHub Docs**: [docs.github.com](https://docs.github.com)
- **Streamlit Forum**: [discuss.streamlit.io](https://discuss.streamlit.io)

### Common Commands Reference:

```bash
# Check git status
git status

# View commit history
git log --oneline

# Create new branch
git checkout -b feature-name

# Switch branches
git checkout main

# Pull latest changes
git pull origin main

# View remotes
git remote -v

# Undo last commit (keep changes)
git reset --soft HEAD~1
```

---

**Congratulations! Your app is now live! 🎉**

Share your app URL with the world:
```
https://your-app-name.streamlit.app
```
