# GitBook Upload Instructions

This folder contains complete documentation ready for GitBook.

---

## 📁 Folder Structure

```
gitbook-docs/
├── README.md (Home page)
├── SUMMARY.md (Table of contents - GitBook navigation)
├── admin/
│   └── system-admin-guide.md (Complete admin guide)
└── users/
    ├── user-guides.md (User guides index)
    ├── admission-officer.md
    ├── payment-workflow.md (Complete payment workflow)
    └── [other role guides]
```

---

## 🚀 How to Upload to GitBook

### Option 1: GitBook Web Interface (Easiest)

1. **Sign up / Login:**
   - Go to [https://www.gitbook.com](https://www.gitbook.com)
   - Sign up for free account or login

2. **Create New Space:**
   - Click **"New Space"**
   - Name it: **"MyISHRM User Guide"**
   - Select **"Import from files"**

3. **Upload Files:**
   - Select all files from `gitbook-docs/` folder
   - Or drag and drop the entire `gitbook-docs/` folder
   - GitBook will automatically:
     - Use README.md as home page
     - Use SUMMARY.md for navigation
     - Create sidebar from folder structure

4. **Publish:**
   - Click **"Publish"**
   - Your documentation will be live at:
     `https://your-org.gitbook.io/myishrm-user-guide`

5. **Share:**
   - Click **"Share"** button
   - Toggle **"Public"** to make accessible without login
   - Copy the public URL and share with users

---

### Option 2: GitHub Integration (Advanced)

1. **Create Public GitHub Repo:**
   ```bash
   cd gitbook-docs
   git init
   git add .
   git commit -m "Initial MyISHRM documentation"
   gh repo create myishrm-docs-public --public --source=.
   git push origin main
   ```

2. **Connect to GitBook:**
   - In GitBook, create new space
   - Select **"Sync with Git"**
   - Connect your GitHub repo
   - Select the repo: `myishrm-docs-public`
   - GitBook will auto-sync on every push

---

## ✅ What's Included

### For System Administrators
- ✅ Complete system setup guide
- ✅ Staff account creation process
- ✅ College → Course → Subject → Faculty workflow
- ✅ Academic setup instructions

### For End Users
- ✅ User guides index (by role)
- ✅ Admission Officer guide
- ✅ Complete payment & admission workflow
- ✅ All roles covered

### URLs Updated
- ✅ All URLs point to: `https://myishrm.flatwire.io`
- ✅ Internal links working (GitBook-compatible)

---

## 📊 Preview Before Upload

To preview locally (optional):

```bash
# Install GitBook CLI (optional)
npm install -g gitbook-cli

# Navigate to gitbook-docs
cd gitbook-docs

# Initialize GitBook
gitbook init

# Serve locally
gitbook serve

# Open browser: http://localhost:4000
```

---

## 🎯 Expected Result

After uploading, your users will see:

```
Home (README.md)
├── For System Administrators
│   └── System Administrator Guide
│       ├── Initial Setup
│       ├── Staff Account Management
│       └── Academic Setup
├── For End Users
│   ├── User Guides by Role
│   ├── Admission Officer Guide
│   ├── [Other role guides]
│   └── Payment & Admission Workflow
└── Support & Help
```

All internal links will be clickable and navigate within GitBook.

---

## 💡 Tips

1. **Navigation:** SUMMARY.md creates the left sidebar in GitBook
2. **Links:** Use relative paths (e.g., `[Text](users/admission-officer.md)`)
3. **Images:** Place in `assets/` folder and reference as `![Alt](assets/image.png)`
4. **Updates:** Edit files and re-upload, or use GitHub sync for auto-updates

---

## 🔗 Example Public URL

After publishing, your documentation will be accessible at a URL like:
`https://ishrm.gitbook.io/myishrm-user-guide`

Share this URL with your end users - they can access it without GitHub access!

---

## ✅ Ready to Upload!

Your documentation is ready. Simply upload the `gitbook-docs/` folder to GitBook!

**Portal:** https://myishrm.flatwire.io
**Documentation:** [Upload to GitBook and share the URL]
