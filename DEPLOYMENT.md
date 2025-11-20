# ChurnGuard AI - GitHub Pages Deployment Guide

**Complete instructions for deploying to GitHub Pages and maintaining the live website**

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Repository Setup](#repository-setup)
3. [Deployment Process](#deployment-process)
4. [Configuration](#configuration)
5. [Verification](#verification)
6. [Maintenance](#maintenance)
7. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before deploying to GitHub Pages, ensure you have:

- **GitHub Account:** Active GitHub account with appropriate permissions
- **Git Installed:** Git version 2.20+ installed on your local machine
- **Repository Access:** Access to the target repository `iimweek32capstone`
- **SSH Key Setup:** SSH key configured for GitHub authentication (recommended)
- **Local Copy:** Complete project files on your local machine

### Install Git (if needed)

**macOS:**
```bash
brew install git
```

**Ubuntu/Debian:**
```bash
sudo apt-get install git
```

**Windows:**
Download from https://git-scm.com/download/win

### Verify Git Installation

```bash
git --version
# Should output: git version 2.x.x or higher
```

---

## Repository Setup

### Step 1: Create GitHub Repository

1. Log in to GitHub (https://github.com)
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Enter repository name: `iimweek32capstone`
5. Add description: "ChurnGuard AI - Strategic Business Plan Capstone Project"
6. Select "Public" (required for GitHub Pages)
7. Initialize with README (optional)
8. Click "Create repository"

### Step 2: Clone Repository Locally

```bash
# Navigate to your projects directory
cd ~/projects

# Clone the repository
git clone https://github.com/lalitnayyar/iimweek32capstone.git

# Navigate into the repository
cd iimweek32capstone
```

### Step 3: Add Project Files

Copy all project files into the cloned repository:

```bash
# Copy presentation slides
cp -r /home/ubuntu/churnguard_presentation ./

# Copy images
cp -r /home/ubuntu/images ./

# Copy documentation
cp /home/ubuntu/README.md ./
cp /home/ubuntu/BUSINESS_PLAN_REPORT.md ./
cp /home/ubuntu/QUICK_REFERENCE.md ./
cp /home/ubuntu/churnguard_analysis.py ./

# Copy website files (if separate)
cp /home/ubuntu/index.html ./
cp -r /home/ubuntu/css ./
cp -r /home/ubuntu/js ./
```

### Step 4: Verify File Structure

```bash
# List directory structure
tree -L 2

# Should show:
# .
# ├── README.md
# ├── BUSINESS_PLAN_REPORT.md
# ├── QUICK_REFERENCE.md
# ├── churnguard_analysis.py
# ├── index.html
# ├── churnguard_presentation/
# ├── images/
# ├── css/
# └── js/
```

---

## Deployment Process

### Step 1: Configure Git User (First Time Only)

```bash
# Set your Git username
git config --global user.name "Lalit Nayyar"

# Set your Git email
git config --global user.email "lalitnayyar@gmail.com"

# Verify configuration
git config --global --list
```

### Step 2: Add Files to Git

```bash
# Add all files to staging area
git add .

# Verify files are staged
git status
```

### Step 3: Create Initial Commit

```bash
# Commit files with descriptive message
git commit -m "Initial commit: ChurnGuard AI capstone project with presentation, business plan, and documentation"

# Verify commit
git log --oneline -1
```

### Step 4: Push to GitHub

```bash
# Push to main branch
git push -u origin main

# Verify push was successful
git log --oneline -1
```

### Step 5: Enable GitHub Pages

1. Go to repository settings: https://github.com/lalitnayyar/iimweek32capstone/settings
2. Scroll to "GitHub Pages" section
3. Under "Source," select "main" branch
4. Select "/" (root) as the folder
5. Click "Save"
6. Wait 1-2 minutes for deployment

### Step 6: Verify Deployment

Your website should now be live at:
```
https://lalitnayyar.github.io/iimweek32capstone
```

---

## Configuration

### GitHub Pages Settings

**Repository Settings Path:**
Settings → Pages

**Configuration Options:**

| Setting | Value |
|---------|-------|
| **Source** | Deploy from a branch |
| **Branch** | main |
| **Folder** | / (root) |
| **Custom Domain** | (optional) |
| **HTTPS** | Enabled (automatic) |

### Jekyll Configuration (Optional)

If using Jekyll for static site generation, create `_config.yml`:

```yaml
# Site title and description
title: ChurnGuard AI
description: Strategic Business Plan - IIMK Capstone Project
author: Lalit Nayyar

# Build settings
markdown: kramdown
theme: jekyll-theme-minimal

# Exclude files from build
exclude:
  - .git
  - .gitignore
  - node_modules
  - Gemfile
  - Gemfile.lock

# Include files
include:
  - .nojekyll

# URL configuration
url: "https://lalitnayyar.github.io"
baseurl: "/iimweek32capstone"
```

### .gitignore Configuration

Create `.gitignore` file:

```
# OS files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/
*.swp
*.swo

# Node modules
node_modules/
npm-debug.log

# Python
__pycache__/
*.pyc
*.pyo
.Python
env/
venv/

# Build files
dist/
build/
*.egg-info/

# Local testing
.jekyll-cache/
_site/
```

---

## Verification

### Step 1: Check Deployment Status

```bash
# View deployment status
curl -I https://lalitnayyar.github.io/iimweek32capstone

# Should return HTTP 200
```

### Step 2: Verify File Accessibility

Test key files are accessible:

- Main page: https://lalitnayyar.github.io/iimweek32capstone/
- README: https://lalitnayyar.github.io/iimweek32capstone/README.md
- Business Plan: https://lalitnayyar.github.io/iimweek32capstone/BUSINESS_PLAN_REPORT.md
- Presentation: https://lalitnayyar.github.io/iimweek32capstone/churnguard_presentation/slide_01_title.html

### Step 3: Test Responsive Design

1. Open website on desktop browser
2. Open website on mobile device
3. Test on tablet
4. Verify layout adapts correctly

### Step 4: Test Interactive Features

- Navigation menu
- Slide navigation
- Bookmarks (if implemented)
- Notes feature (if implemented)
- Search functionality (if implemented)

### Step 5: Cross-Browser Testing

Test on:
- Chrome/Chromium
- Firefox
- Safari
- Edge

### Step 6: Performance Testing

```bash
# Test page load time
curl -w "Time: %{time_total}s\n" -o /dev/null -s https://lalitnayyar.github.io/iimweek32capstone

# Use Google PageSpeed Insights
# https://pagespeed.web.dev/?url=https%3A%2F%2Flalitnayyar.github.io%2Fiimweek32capstone
```

---

## Maintenance

### Updating Content

When you need to update content:

```bash
# Make changes to files locally
# Edit files as needed

# Check what changed
git status

# Stage changes
git add .

# Commit changes
git commit -m "Update: Description of changes made"

# Push to GitHub
git push origin main

# Wait 1-2 minutes for deployment
```

### Adding New Files

```bash
# Copy new files to repository directory
cp /path/to/new/file ./

# Add to Git
git add new_file.html

# Commit and push
git commit -m "Add: Description of new file"
git push origin main
```

### Updating Images

```bash
# Copy updated images
cp /path/to/updated/images/* ./images/

# Add to Git
git add images/

# Commit and push
git commit -m "Update: New or updated images"
git push origin main
```

### Version Control Best Practices

1. **Commit Frequently:** Make small, focused commits
2. **Descriptive Messages:** Use clear commit messages
3. **Branch Strategy:** Use branches for major changes
4. **Pull Before Push:** Always pull latest changes first

```bash
# Pull latest changes
git pull origin main

# Make your changes
# ...

# Push your changes
git push origin main
```

---

## Troubleshooting

### Issue: Website Not Appearing

**Problem:** Site not accessible at GitHub Pages URL

**Solutions:**
1. Verify GitHub Pages is enabled in repository settings
2. Check that you're using correct URL: `https://USERNAME.github.io/REPO`
3. Wait 2-3 minutes for deployment
4. Check deployment status in repository settings

### Issue: Old Content Still Showing

**Problem:** Changes not appearing on live site

**Solutions:**
1. Hard refresh browser: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
2. Clear browser cache
3. Verify files were pushed: `git log --oneline`
4. Check file paths are correct
5. Wait for deployment to complete

### Issue: Images Not Loading

**Problem:** Images show as broken links

**Solutions:**
1. Verify image files exist in repository
2. Check image paths are relative: `./images/image.png`
3. Ensure image filenames match exactly (case-sensitive)
4. Verify images are added to Git: `git ls-files images/`

### Issue: Links Not Working

**Problem:** Navigation links or internal links broken

**Solutions:**
1. Use relative paths: `./page.html` not `/page.html`
2. Include file extension: `./page.html` not `./page`
3. Verify target files exist
4. Check for typos in file names

### Issue: Styling Not Applied

**Problem:** CSS not loading or styles not appearing

**Solutions:**
1. Verify CSS files are in repository
2. Check CSS paths are relative
3. Hard refresh browser to clear cache
4. Check for CSS errors in browser console (F12)
5. Verify CSS file is linked correctly in HTML

### Issue: JavaScript Not Working

**Problem:** Interactive features not functioning

**Solutions:**
1. Verify JavaScript files are in repository
2. Check JS paths are relative
3. Open browser console (F12) for error messages
4. Verify JavaScript syntax is correct
5. Check for conflicting scripts

### Issue: Slow Performance

**Problem:** Website loads slowly

**Solutions:**
1. Optimize image sizes (compress images)
2. Minimize CSS and JavaScript
3. Enable browser caching
4. Use CDN for large files (optional)
5. Reduce number of HTTP requests

---

## Advanced Configuration

### Custom Domain (Optional)

To use a custom domain:

1. Purchase domain from registrar (GoDaddy, Namecheap, etc.)
2. Go to repository settings → Pages
3. Enter custom domain in "Custom domain" field
4. Configure DNS records with your registrar:
   - Type: A
   - Name: @
   - Value: GitHub Pages IP (check GitHub docs for current IPs)
5. Wait for DNS propagation (can take 24 hours)

### SSL/TLS Certificate

GitHub Pages automatically provides free SSL/TLS certificates via Let's Encrypt:

1. Go to repository settings → Pages
2. Check "Enforce HTTPS" (recommended)
3. Wait for certificate provisioning

### Analytics (Optional)

Add Google Analytics to track visitors:

```html
<!-- Add to index.html before closing </head> tag -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

---

## Deployment Checklist

- [ ] GitHub account created and configured
- [ ] Repository created with correct name
- [ ] All project files copied to repository
- [ ] Git configured with user name and email
- [ ] Files added and committed to Git
- [ ] Changes pushed to GitHub
- [ ] GitHub Pages enabled in settings
- [ ] Website accessible at GitHub Pages URL
- [ ] All files loading correctly (HTML, CSS, JS, images)
- [ ] Responsive design verified on mobile
- [ ] Cross-browser testing completed
- [ ] Performance verified
- [ ] Links and navigation working
- [ ] Interactive features functioning
- [ ] Documentation accessible

---

## Support and Contact

**For deployment issues:**
- Check GitHub documentation: https://docs.github.com/en/pages
- Review GitHub Pages troubleshooting: https://docs.github.com/en/pages/getting-started-with-github-pages/troubleshooting-github-pages

**Student Contact:**
- **Name:** Lalit Nayyar
- **Email:** lalitnayyar@gmail.com
- **Course:** IIMK Professional Certificate in Data Science and AI for Managers

---

## Additional Resources

- **GitHub Pages Documentation:** https://docs.github.com/en/pages
- **Git Documentation:** https://git-scm.com/doc
- **Markdown Guide:** https://www.markdownguide.org/
- **HTML5 Reference:** https://developer.mozilla.org/en-US/docs/Web/HTML
- **CSS3 Reference:** https://developer.mozilla.org/en-US/docs/Web/CSS

---

**Last Updated:** November 2025  
**Version:** 1.0  
**Status:** Ready for Deployment
