# HawkBeam Render.com Deployment Guide

## 🚀 Quick Deployment Steps

### 1. **Push to GitHub**
First, make sure your code is pushed to a GitHub repository:

```bash
# If not already initialized
git init
git add .
git commit -m "Initial commit - HawkBeam construction website"

# Push to GitHub (replace with your repo URL)
git remote add origin https://github.com/yourusername/hawkbeam.git
git branch -M main
git push -u origin main
```

### 2. **Deploy on Render.com**

1. **Go to [Render.com](https://render.com)** and sign up/login
2. **Click "New +"** → **"Web Service"**
3. **Connect your GitHub repository**
4. **Configure the service:**

   - **Name**: `hawkbeam-construction`
   - **Region**: `Oregon (US West)`
   - **Branch**: `main`
   - **Root Directory**: Leave empty (uses root)
   - **Runtime**: `Node`
   - **Build Command**: `cd frontend && npm install && npm run optimize-images && npm run build`
   - **Start Command**: `cd frontend && npm run start`
   - **Plan**: `Free` (or upgrade as needed)

5. **Click "Create Web Service"**

### 3. **Environment Variables** (Optional)
If you're using EmailJS or other services, add these in Render dashboard:
- `VITE_EMAILJS_SERVICE_ID`
- `VITE_EMAILJS_TEMPLATE_ID`
- `VITE_EMAILJS_PUBLIC_KEY`

## 📁 Files Created for Deployment

### ✅ **render.yaml** (Root directory)
- Automated deployment configuration
- Handles build and start commands
- Optimizes images during build

### ✅ **_redirects** (frontend/public/)
- Handles React Router client-side routing
- Ensures all routes work properly

### ✅ **Updated package.json**
- Added `start` script for production
- Configured for Render.com hosting

### ✅ **Updated vite.config.js**
- Production optimizations
- Code splitting for better performance
- Proper port configuration

## 🔧 Build Process

The deployment will:

1. **Install Dependencies**: `npm install`
2. **Optimize Images**: Convert PNGs to WebP (saves 60-80% bandwidth)
3. **Build Production**: Create optimized bundle
4. **Start Server**: Serve static files with Vite preview

## 📊 Performance Optimizations

### **Image Optimization**
- ✅ WebP format (60-80% smaller)
- ✅ Responsive images (4 sizes per image)
- ✅ Automatic fallbacks

### **Code Splitting**
- ✅ Vendor chunks (React, React DOM)
- ✅ Router chunk (React Router)
- ✅ Animation chunk (Framer Motion)
- ✅ Icons chunk (React Icons)

### **Build Optimizations**
- ✅ Minification with Terser
- ✅ Asset optimization
- ✅ Tree shaking

## 🌐 Expected Results

### **Performance Metrics**
- **First Load**: 2-4 seconds
- **Subsequent Loads**: < 1 second (cached)
- **Lighthouse Score**: 90+ (Performance)
- **Bundle Size**: ~2-3MB (optimized)

### **Features Working**
- ✅ All animations and transitions
- ✅ Responsive design
- ✅ Contact form (with EmailJS)
- ✅ Image optimization
- ✅ Client-side routing

## 🔍 Troubleshooting

### **Build Fails**
- Check Node.js version (18+ recommended)
- Verify all dependencies are in package.json
- Check for syntax errors in components

### **Images Not Loading**
- Ensure images are in `frontend/src/assets/`
- Check import paths are correct
- Verify optimization script ran successfully

### **Routing Issues**
- Confirm `_redirects` file is in `frontend/public/`
- Check React Router configuration

### **Performance Issues**
- Run `npm run optimize-images` locally first
- Check bundle analyzer in build logs
- Verify code splitting is working

## 📱 Testing Deployment

After deployment:

1. **Test all routes**: Home, About, Services, Projects, Contact
2. **Check mobile responsiveness**
3. **Verify images load quickly**
4. **Test contact form**
5. **Check animations work smoothly**

## 🎯 Custom Domain (Optional)

To use a custom domain:

1. **In Render Dashboard**: Settings → Custom Domains
2. **Add your domain**: `www.hawkbeam.co.ke`
3. **Update DNS**: Point CNAME to Render URL
4. **SSL**: Automatically handled by Render

## 💡 Pro Tips

- **Free Tier**: 750 hours/month (enough for most sites)
- **Auto-Deploy**: Pushes to main branch auto-deploy
- **Logs**: Check build/runtime logs in Render dashboard
- **Monitoring**: Built-in uptime monitoring

Your HawkBeam construction website is now ready for professional deployment! 🏗️
