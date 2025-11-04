# BrightenEnroll Project Structure

## Frontend Styling

### Tailwind CSS Setup
- **Input:** `Styles/tailwind.css` - Source file with Tailwind directives
- **Output:** `wwwroot/css/tailwind.css` - Compiled and minified CSS
- **Config:** `tailwind.config.js` - Tailwind configuration
- **PostCSS:** `postcss.config.js` - PostCSS plugins configuration

### Build Commands
```bash
npm run build:css  # Build production CSS
npm run watch:css  # Watch and rebuild automatically
npm run dev  # Alias for watch:css
```

## Component Structure

### Layouts
- **`Components/Layout/MainLayout.razor`** - Basic layout wrapper
- **`Components/Layout/DashboardLayout.razor`** - Admin dashboard layout with sidebar
  - Includes navigation menu
  - User profile section
  - Dynamic page titles

### Pages
- **`Components/Pages/LandingPage.razor`** - `/` - Landing page
- **`Components/Pages/LoginPage.razor`** - `/login` - Login page
- **`Components/Pages/Dashboard.razor`** - `/dashboard` - Main dashboard

### Page-Layout Mapping
| Page | Layout | Route |
|------|--------|-------|
| LandingPage | None (standalone) | `/` |
| LoginPage | None (standalone) | `/login` |
| Dashboard | DashboardLayout | `/dashboard` |
| Enrollment | DashboardLayout | `/enrollment` |
| Student Record | DashboardLayout | `/student-record` |
| Academics | DashboardLayout | `/academics` |
| Finance | DashboardLayout | `/finance` |
| Human Resource | DashboardLayout | `/human-resource` |

## Assets

### Images
- **`wwwroot/brighthenlogo.png`** - BrightenRoll logo
- **`wwwroot/kid.png`** - Login page illustration

### Stylesheets
- **`wwwroot/css/tailwind.css`** - Compiled Tailwind CSS (generated)
- **`wwwroot/css/app.css`** - Additional application styles
- **`Components/Layout/DashboardLayout.razor.css`** - Dashboard layout scoped styles

## Key Features

### Authentication Flow
1. Landing Page ? Login Page ? Dashboard
2. Login validation (basic client-side)
3. Navigation to dashboard on successful login

### Dashboard Features
- Statistics cards (Total Enrolled, Employees, Applications, Tuition)
- Charts (Total Income, Student Types)
- Sidebar navigation with active state
- User profile dropdown

### Responsive Design
- Mobile-first approach using Tailwind breakpoints
- Collapsible sidebar on mobile (md: breakpoint)
- Responsive grid layouts

## Development Workflow

### 1. Start CSS Watch Mode
```bash
npm run watch:css
```

### 2. Run the Application
- Open in Visual Studio
- Select your target platform (Windows, Android, iOS, Mac)
- Press F5 to run

### 3. Make Changes
- Edit Razor components
- Tailwind automatically rebuilds CSS
- Hot reload in Visual Studio (if supported)

## Technology Stack

- **.NET 9** - Framework
- **.NET MAUI** - Cross-platform UI
- **Blazor Hybrid** - Web UI in native apps
- **Tailwind CSS 3.4** - Utility-first CSS framework
- **Node.js & npm** - Build tools

## Important Notes

1. **Always run `npm run watch:css` during development**
2. **Run `npm run build:css` before deployment**
3. **Don't edit `wwwroot/css/tailwind.css` directly** - it's generated
4. **Custom styles go in `Styles/tailwind.css`**
5. **Use Tailwind utility classes in Razor files**

## Adding New Pages

1. Create the page in `Components/Pages/`
2. Add `@layout Layout.DashboardLayout` if it needs the dashboard layout
3. Add navigation link in `DashboardLayout.razor`
4. Add page title mapping in `GetPageTitle()` method
5. Rebuild CSS if you use new Tailwind classes

## Troubleshooting

- **CSS not loading:** Check `wwwroot/index.html` has `<link rel="stylesheet" href="css/tailwind.css" />`
- **Classes not working:** Run `npm run build:css` and refresh
- **Build errors:** Run `npm install` to restore packages
