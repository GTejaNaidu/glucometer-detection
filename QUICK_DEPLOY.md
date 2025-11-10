# ⚡ Quick Deploy Commands

## Copy and paste these commands one by one:

### 1️⃣ Initialize Git
```bash
cd C:\Users\tejan\OneDrive\Desktop\OCR
git init
```

### 2️⃣ Configure Git (Replace with your info)
```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### 3️⃣ Add All Files
```bash
git add .
```

### 4️⃣ Create First Commit
```bash
git commit -m "Initial commit: Advanced Glucometer Detection System"
```

### 5️⃣ Create GitHub Repository
1. Go to: https://github.com/new
2. Repository name: `glucometer-detection`
3. Make it Public
4. **DO NOT** check "Initialize with README"
5. Click "Create repository"

### 6️⃣ Connect to GitHub (Replace YOUR_USERNAME)
```bash
git remote add origin https://github.com/YOUR_USERNAME/glucometer-detection.git
git branch -M main
git push -u origin main
```

### 7️⃣ Deploy to Streamlit
1. Go to: https://share.streamlit.io
2. Sign in with GitHub
3. Click "New app"
4. Select your repository
5. Main file: `b.py`
6. Click "Deploy!"

---

## 🎉 Done!

Your app will be live at:
```
https://your-app-name.streamlit.app
```

---

## 📝 Update App Later

```bash
# Make changes to your code
# Then run:
git add .
git commit -m "Your update message"
git push origin main
```

Streamlit will auto-redeploy!
