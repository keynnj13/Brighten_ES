# Quick Start Guide - BrightenEnroll ES

## Initial Setup (One-time)

1. **Install Node.js dependencies:**
   ```bash
   npm install
   ```

2. **Build Tailwind CSS:**
```bash
   npm run build:css
   ```

## Development

### Option 1: Manual Build (Simple)
Run this before starting your app:
```bash
npm run build:css
```

### Option 2: Watch Mode (Recommended for Active Development)

**Terminal 1** - Start CSS watch mode:
```bash
npm run watch:css
```
Leave this running while you develop. It will automatically rebuild CSS when you make changes.

**Visual Studio** - Run your app normally (F5)

## Project Overview

### Pages
- **Landing Page** (`/`) - Welcome page with login button
- **Login Page** (`/login`) - User authentication
- **Dashboard** (`/dashboard`) - Main admin dashboard with stats and charts

### Features
- ? Responsive design (mobile, tablet, desktop)
- ? Tailwind CSS (configured, not CDN)
- ? Reusable dashboard layout
- ? Active navigation states
- ? Custom components and utilities

## Common Tasks

### Adding a New Page
1. Create `Components/Pages/YourPage.razor`
2. Add route: `@page "/your-page"`
3. Add layout (optional): `@layout Layout.DashboardLayout`
4. Use Tailwind classes for styling

### Customizing Styles
Edit `Styles/tailwind.css`:
```css
@layer components {
    .my-button {
   @apply bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded;
    }
}
```
Then rebuild: `npm run build:css`

### Adding Navigation Links
Edit `Components/Layout/DashboardLayout.razor` - add a new `NavLink`:
```razor
<NavLink href="/your-page" class="flex items-center gap-3 px-4 py-3 mb-2 rounded-lg font-medium transition-all">
    <svg><!-- icon --></svg>
    Your Page
</NavLink>
```

## Troubleshooting

**Q: My styles aren't showing**
- Check that `npm run build:css` completed successfully
- Verify `wwwroot/css/tailwind.css` exists
- Clear browser cache (Ctrl+F5)

**Q: New Tailwind classes aren't working**
- Run `npm run build:css` to rebuild
- Check that your file is in the paths configured in `tailwind.config.js`

**Q: npm commands fail**
- Ensure Node.js is installed: `node --version`
- Delete `node_modules` and run `npm install` again

## File Structure
```
BrightenEnroll_ES/
??? Components/
?   ??? Layout/
?   ?   ??? DashboardLayout.razor      # Dashboard layout with sidebar
?   ?   ??? DashboardLayout.razor.css  # Layout styles
?   ?   ??? MainLayout.razor   # Basic layout
?   ??? Pages/
?       ??? LandingPage.razor    # Landing page
?     ??? LoginPage.razor            # Login page
?       ??? Dashboard.razor       # Dashboard page
??? Styles/
?   ??? tailwind.css      # Tailwind input file
??? wwwroot/
?   ??? css/
?   ?   ??? tailwind.css  # Generated CSS (don't edit)
?   ??? brighthenlogo.png
?   ??? kid.png
??? tailwind.config.js      # Tailwind configuration
??? postcss.config.js    # PostCSS configuration
??? package.json     # npm scripts and dependencies
```

## Deployment

Before deploying:
1. Build production CSS: `npm run build:css`
2. Test the app thoroughly
3. Commit all changes including `wwwroot/css/tailwind.css`

## Documentation
- **TAILWIND_SETUP.md** - Detailed Tailwind setup documentation
- **PROJECT_STRUCTURE.md** - Complete project structure guide
- **Components/Layout/README.md** - Dashboard layout documentation

## Need Help?
Check the documentation files mentioned above for more detailed information.
