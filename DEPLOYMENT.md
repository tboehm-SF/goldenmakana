# Makana Health - GitHub to Netlify Deployment Guide

## ✅ Completed Setup

### 1. GitHub Repository Created
- **Repository**: https://github.com/tboehm-SF/goldenmakana
- **Branch**: main
- **Status**: Public repository
- **Files**: 66 files committed and pushed

### 2. Project Structure
```
goldenmakana/
├── .gitignore              # Excludes node_modules, env files, build artifacts
├── README.md               # Project documentation
├── package.json            # Node.js dependencies
├── netlify.toml            # Netlify configuration
├── index.html              # Homepage
├── about.html, careers.html, etc. # Main pages
├── hcp-portal/             # Healthcare professional portal pages
├── products/               # Individual product pages (18 products)
├── js/                     # JavaScript modules
│   ├── makana-init.js
│   ├── makana-contact.js
│   ├── makana-personalization.js
│   └── ... (6 total)
└── netlify/
    └── functions/          # Netlify serverless functions
        └── contact-lookup.js

```

### 3. Local Project Location
- **Path**: `/Users/tbohm/claude-projects/makana-health`
- **Git Remote**: `origin` → `https://github.com/tboehm-SF/goldenmakana.git`

## 🔄 Next Steps: Connect Netlify to GitHub

To link your existing Netlify site to the new GitHub repository:

### Option 1: Via Netlify UI (Recommended)
1. Go to https://app.netlify.com/sites/goldenmakana/settings
2. Navigate to **Build & Deploy** → **Continuous Deployment**
3. Click **Link repository**
4. Select **GitHub** and authorize Netlify to access your repos
5. Choose: `tboehm-SF/goldenmakana`
6. Set build settings:
   - **Base directory**: (leave empty)
   - **Build command**: `echo 'Static site'` or leave empty
   - **Publish directory**: `.` (root)
7. Click **Deploy site**

### Option 2: Via Netlify CLI
```bash
cd /Users/tbohm/claude-projects/makana-health
netlify link --repo tboehm-SF/goldenmakana
netlify deploy --prod
```

## ⚙️ Configuration Files

### netlify.toml
- **Build**: Static site (no build step required)
- **Functions**: Enabled at `netlify/functions/`
- **Security Headers**: X-Frame-Options, CSP, XSS Protection
- **Redirects**: API routes → Netlify Functions

### package.json
- **Dev dependency**: netlify-cli for local development
- **Scripts**: 
  - `npm run dev` - Local development server
  - `npm run deploy` - Deploy to Netlify

## 🔐 Environment Variables

If your site requires environment variables, add them in Netlify:
1. Netlify Dashboard → Site Settings → Environment Variables
2. Add any API keys or secrets needed by the functions

## 📊 Deployment Flow

Once linked:
```
Push to GitHub → Netlify auto-deploys → Live at goldenmakana.netlify.app
```

- **Automatic deployments**: Every push to `main` branch
- **Deploy previews**: Automatic for pull requests
- **Rollback**: Available in Netlify Dashboard

## ✨ Benefits of GitHub Integration

✅ **Version Control**: Full history of all changes  
✅ **Collaboration**: Team members can contribute via PRs  
✅ **CI/CD**: Automatic deployments on every push  
✅ **Preview Deploys**: Test changes before merging  
✅ **Rollback**: Easy revert to previous versions  
✅ **Branch Deploys**: Test different versions simultaneously  

## 🚀 Testing Locally

```bash
cd /Users/tbohm/claude-projects/makana-health
npx serve .
# Or use Netlify Dev for functions support:
npx netlify dev
```

## 📝 Important Notes

- Your Netlify site URL remains: **https://goldenmakana.netlify.app**
- No downtime during the GitHub connection
- Existing deployment will stay live until you push changes
- All your Netlify Functions are preserved in the repository

---
Repository created: 2026-05-20  
Migration completed by: Claude Code
