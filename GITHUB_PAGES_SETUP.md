# 🚀 GitHub Pages Setup Guide

This guide will help you deploy your Samanvaya 2025 website to GitHub Pages with automated winners gallery powered by Google Drive.

## 📋 Prerequisites

1. **Google Drive Folder** with winner images
2. **Google API Key** with Drive API access
3. **GitHub repository** (you already have this!)

## 🔧 Step-by-Step Setup

### Step 1: Prepare Your Google Drive Folder

1. **Create a folder** in Google Drive for winner images
2. **Share the folder**: 
   - Right-click folder → Share
   - Change to "Anyone with the link" can view
   - Copy the folder ID from the URL (the long string after `/folders/`)
   - Example: `https://drive.google.com/drive/folders/1ABC123XYZ456...`
   - Folder ID: `1ABC123XYZ456...`

### Step 2: Get Google API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. **Enable Google Drive API**:
   - Go to "APIs & Services" → "Library"
   - Search for "Google Drive API"
   - Click "Enable"
4. **Create API Key**:
   - Go to "APIs & Services" → "Credentials"
   - Click "Create Credentials" → "API Key"
   - Copy the generated API key
   - (Optional) Restrict the key to Google Drive API only for security

### Step 3: Add GitHub Secrets

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret** and add these two secrets:

   **Secret 1:**
   - Name: `GOOGLE_API_KEY`
   - Value: Your Google API key from Step 2

   **Secret 2:**
   - Name: `WINNERS_DRIVE_FOLDER_ID`
   - Value: Your Google Drive folder ID from Step 1

### Step 4: Enable GitHub Pages

1. In your repository, go to **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Choose branch: `gh-pages`
4. Choose folder: `/ (root)`
5. Click **Save**

### Step 5: Deploy

1. **Push any changes** to the `main` branch, or
2. **Manually trigger** the workflow:
   - Go to **Actions** tab
   - Click "Deploy to GitHub Pages"
   - Click "Run workflow"

## 🎯 How It Works

1. **GitHub Actions** automatically runs when you push to `main`
2. **Secrets are injected** into your HTML file during build
3. **Site is deployed** to GitHub Pages on the `gh-pages` branch
4. **Winners gallery** automatically loads images from your Google Drive folder

## 📁 Managing Winner Images

After setup, managing winners is super easy:
- **Add images**: Just upload to your Google Drive folder
- **Remove images**: Delete from the folder
- **Reorder**: Rename files (they're sorted by creation date)

The website will automatically show new images within a few minutes!

## 🌐 Accessing Your Site

After deployment, your site will be available at:
```
https://VARevents.github.io/samanvaya2k25/
```

## 🔧 Troubleshooting

### "API Key invalid" Error
- Check that Google Drive API is enabled
- Verify API key is correct in GitHub Secrets
- Make sure API key has no restrictions blocking the request

### "Folder not found" Error
- Verify folder sharing is set to "Anyone with the link"
- Check that folder ID is correct in GitHub Secrets
- Make sure folder contains image files

### Images Not Loading
- Check that files in Drive folder are actually images (PNG, JPG, etc.)
- Verify folder permissions
- Images may take a few minutes to appear due to Google's caching

### Deployment Failed
- Check the Actions tab for error details
- Ensure both secrets are properly set
- Make sure the workflow has permissions to deploy

## 🎨 Customization

You can modify the winners gallery by editing `index.html`:
- Change autoplay speed (line ~1320: `4000` = 4 seconds)
- Modify carousel styling in the CSS section
- Add click-to-enlarge functionality

## 🔒 Security Notes

- ✅ API keys are stored securely in GitHub Secrets
- ✅ Keys are never exposed in your source code
- ✅ Keys are only injected during deployment
- ✅ Drive folder is read-only access

---

**🎉 That's it! Your automated winners gallery is now live!**

Just add winner photos to your Google Drive folder and they'll automatically appear on your website.