# Heroku Deployment Guide

## ✅ Fixed Issues

Your repository is now configured for Heroku deployment:

✅ **package-lock.json sync error** - Regenerated lockfile with Express  
✅ **Missing web server** - Added Express server (server.js)  
✅ **No start script** - Added to package.json  
✅ **Node.js version** - Specified engine requirements  
✅ **Procfile** - Explicit web dyno configuration  

## 🚀 Deploy to Heroku

### Option 1: Deploy via Heroku Dashboard (Easiest)

1. **Login to Heroku**: https://dashboard.heroku.com
2. **Create New App**:
   - Click "New" → "Create new app"
   - App name: `goldenmakana` (or your choice)
   - Region: Choose closest to your users
3. **Connect GitHub**:
   - Go to "Deploy" tab
   - Deployment method: Select "GitHub"
   - Connect to GitHub and search for: `goldenmakana`
   - Click "Connect"
4. **Enable Automatic Deploys** (Optional):
   - Click "Enable Automatic Deploys"
   - Every push to `main` will auto-deploy
5. **Manual Deploy**:
   - Scroll to "Manual deploy"
   - Branch: `main`
   - Click "Deploy Branch"

### Option 2: Deploy via Heroku CLI

```bash
# Install Heroku CLI (if not installed)
# macOS: brew tap heroku/brew && brew install heroku
# Or download: https://devcenter.heroku.com/articles/heroku-cli

# Login
heroku login

# Create app (or use existing)
heroku create goldenmakana

# Add GitHub remote (if not already added)
heroku git:remote -a goldenmakana

# Deploy
git push heroku main
```

### Option 3: Connect Existing Heroku App

If you already created a Heroku app:

```bash
cd /Users/tbohm/claude-projects/makana-health

# Add Heroku remote
heroku git:remote -a YOUR_HEROKU_APP_NAME

# Push to deploy
git push heroku main
```

## 📋 What's Included

### Server Configuration
- **server.js**: Express server serving static files
- **Procfile**: Tells Heroku to run `node server.js`
- **Security headers**: X-Frame-Options, XSS Protection, etc.
- **PORT binding**: Uses `process.env.PORT` for Heroku

### Package Configuration
```json
{
  "engines": {
    "node": "20.x",
    "npm": "10.x"
  },
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

## 🔍 Verify Deployment

After deployment:

```bash
# Check logs
heroku logs --tail -a goldenmakana

# Open app in browser
heroku open -a goldenmakana

# Check dyno status
heroku ps -a goldenmakana
```

Expected output:
```
=== web (Free): node server.js (1)
web.1: up 2024/05/20 22:30:00 +0000
```

## ⚙️ Environment Variables

If your site needs environment variables:

```bash
# Via CLI
heroku config:set API_KEY=your_key -a goldenmakana

# Via Dashboard
Settings → Config Vars → Reveal Config Vars → Add
```

## 🌐 Custom Domain

To use a custom domain:

1. Heroku Dashboard → Settings → Domains
2. Add domain: `www.makanahealth.com`
3. Configure DNS:
   - Add CNAME: `www` → `goldenmakana.herokuapp.com`
   - Or use Heroku's DNS target from dashboard

## 📊 Build Process

Heroku will:
1. Detect Node.js app (via package.json)
2. Install Node.js 20.x
3. Run `npm ci` (clean install from lockfile)
4. Execute Procfile: `web: node server.js`
5. Bind to $PORT and start serving

## 🐛 Troubleshooting

### "Application Error" after deployment
Check logs: `heroku logs --tail`

Common fixes:
- Ensure PORT is read from environment: `process.env.PORT`
- Check for syntax errors: `node server.js` locally
- Verify all dependencies installed: `npm install`

### Build fails with "lockfile out of sync"
```bash
# Regenerate locally and push
rm package-lock.json
npm install
git add package-lock.json
git commit -m "Sync package-lock.json"
git push
```

### Slow first request (cold start)
- Heroku free tier sleeps after 30 min inactivity
- Consider upgrading to Hobby ($7/mo) for always-on
- Or use a ping service to keep awake

## 💰 Pricing

- **Free Tier**: 550-1000 dyno hours/month (sleeps after 30 min)
- **Hobby**: $7/mo (always on, custom domains, SSL)
- **Professional**: $25-50/mo (advanced features)

## 🔄 Deployment Workflow

```
Local changes → Git commit → Push to GitHub → Heroku auto-deploys
```

Or manual:
```
git push heroku main → Heroku builds and deploys
```

## 📝 Testing Locally

Before deploying:

```bash
# Install dependencies
npm install

# Run locally (uses port 3000)
npm start

# Test in browser
open http://localhost:3000
```

## 🎯 Your Repository

- **GitHub**: https://github.com/tboehm-SF/goldenmakana
- **Heroku**: https://goldenmakana.herokuapp.com (after deployment)

---
Heroku configuration added: 2026-05-20  
Ready to deploy! 🚀
