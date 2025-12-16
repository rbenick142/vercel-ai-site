# Deployment Guide: GitHub + Vercel Setup

## Option 1: Using GitHub Web Interface (Recommended for first-time setup)

### Step 1: Create GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon in the top right → "New repository"
3. Name it: `vercel-ai-site` (or your preferred name)
4. Choose **Public** or **Private**
5. **DO NOT** initialize with README, .gitignore, or license (we already have these)
6. Click "Create repository"

### Step 2: Push Your Code to GitHub

After creating the repository, GitHub will show you commands. Run these in your terminal:

```powershell
cd "c:\Users\nicoa\.cursor\projects\vercel_ai_site"
git remote add origin https://github.com/YOUR_USERNAME/vercel-ai-site.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

### Step 3: Connect to Vercel

1. Go to [vercel.com](https://vercel.com) and sign in (or create an account)
2. Click "Add New..." → "Project"
3. Click "Import Git Repository"
4. Authorize Vercel to access your GitHub account if prompted
5. Select your `vercel-ai-site` repository
6. Vercel will auto-detect the settings:
   - **Framework Preset:** Other
   - **Root Directory:** `./` (leave as is)
   - **Output Directory:** `Nexus-AI-HTML`
7. Click "Deploy"
8. Your site will be live in ~1-2 minutes!

---

## Option 2: Using CLI Tools (Faster for future deployments)

### Install GitHub CLI

```powershell
# Using winget (Windows Package Manager)
winget install --id GitHub.cli

# Or download from: https://cli.github.com/
```

### Install Vercel CLI

```powershell
# Using npm (requires Node.js)
npm i -g vercel

# Or using winget
winget install --id Vercel.CLI
```

### After Installation

1. **Authenticate GitHub CLI:**
   ```powershell
   gh auth login
   ```

2. **Create GitHub Repository:**
   ```powershell
   cd "c:\Users\nicoa\.cursor\projects\vercel_ai_site"
   gh repo create vercel-ai-site --public --source=. --remote=origin --push
   ```

3. **Authenticate Vercel CLI:**
   ```powershell
   vercel login
   ```

4. **Deploy to Vercel:**
   ```powershell
   vercel
   ```
   Follow the prompts:
   - Link to existing project? **No**
   - Project name: `vercel-ai-site` (or your choice)
   - Directory: `./Nexus-AI-HTML`
   - Deploy? **Yes**

---

## Troubleshooting

### If you get authentication errors:
- Make sure you're logged into GitHub/Vercel in your browser
- For GitHub CLI: Run `gh auth login` again
- For Vercel CLI: Run `vercel login` again

### If deployment fails:
- Check that `vercel.json` is in the root directory
- Verify the `outputDirectory` in `vercel.json` matches your HTML folder name
- Check Vercel dashboard for error logs

### Custom Domain (Optional):
1. Go to your Vercel project dashboard
2. Click "Settings" → "Domains"
3. Add your custom domain
4. Follow DNS configuration instructions

---

## Next Steps After Deployment

1. **Customize Content:** Edit HTML files in `Nexus-AI-HTML/` to match your AI consulting business
2. **Update Branding:** Change "Nexus AI" to your business name throughout the site
3. **Add Real Content:** Replace placeholder text with your actual services, case studies, etc.
4. **Continuous Deployment:** Every push to `main` branch will automatically deploy to Vercel!

