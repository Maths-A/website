# Deployment Guide

## Overview

The website is built using Vite and generates static files that can be deployed to any static hosting service.

## Building for Production

```bash
npm run build
```

This creates a `dist/` directory with all production-ready files.

## Deployment Options

### Option 1: GitHub Pages

1. Build the project:
   ```bash
   npm run build
   ```

2. The `dist/` folder contains all necessary files. You can:
   - Push the `dist/` folder to the `gh-pages` branch
   - Or configure GitHub Actions to build and deploy automatically

### Option 2: Netlify

1. Connect your GitHub repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Deploy!

### Option 3: Vercel

1. Import your GitHub repository to Vercel
2. Vercel will auto-detect Vite
3. Deploy with default settings

### Option 4: Traditional Web Hosting

1. Build the project:
   ```bash
   npm run build
   ```

2. Upload the contents of the `dist/` folder to your web server via FTP/SFTP

3. Ensure your web server is configured to:
   - Serve `index.html` as the default file
   - Handle client-side routing (if needed in the future)

## Environment Variables

Currently, the website doesn't use environment variables. If you need to add them:

1. Create a `.env` file in the root directory
2. Add variables prefixed with `VITE_`:
   ```
   VITE_API_URL=https://api.example.com
   ```
3. Access in code:
   ```javascript
   const apiUrl = import.meta.env.VITE_API_URL;
   ```

## Custom Domain

### For GitHub Pages:
1. Add a `CNAME` file to the `public/` directory with your domain
2. Configure DNS records with your domain provider

### For Netlify/Vercel:
1. Add custom domain in the hosting dashboard
2. Follow DNS configuration instructions

## Performance Optimization

The built files are already optimized:
- ✅ Minified CSS and JavaScript
- ✅ Optimized images (consider using WebP format for better compression)
- ✅ Gzip compression (enabled on most hosting platforms)

## SSL/HTTPS

Most modern hosting platforms (GitHub Pages, Netlify, Vercel) provide free SSL certificates automatically.

For traditional hosting, you may need to:
- Use Let's Encrypt for free SSL
- Or purchase an SSL certificate from your hosting provider

## Monitoring

Consider adding:
- Google Analytics (add tracking code to `index.html`)
- Error monitoring (e.g., Sentry)
- Performance monitoring (e.g., Lighthouse CI)

## Troubleshooting

### Images not loading
- Ensure image paths are correct relative to the `public/` directory
- Check that images are copied to `dist/` after build

### Fonts not loading
- Verify font files are in `public/ressources/fonts/`
- Check font-face declarations in CSS

### JavaScript not working
- Check browser console for errors
- Ensure JavaScript is enabled
- Verify all imports are correct

## Maintenance

To update the website:
1. Make changes to source files
2. Test locally with `npm run dev`
3. Build with `npm run build`
4. Deploy the new `dist/` folder

## Rollback

If you need to rollback:
1. Keep previous `dist/` folder as backup
2. Or use version control to revert to previous commit
3. Rebuild and redeploy
