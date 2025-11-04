# Tailwind CSS Setup

This project uses Tailwind CSS v3 with a custom configuration.

## Installation

The project already has Tailwind CSS installed. If you need to reinstall dependencies:

```bash
npm install
```

## Build Commands

### Build CSS (Production)
Compiles and minifies the Tailwind CSS:

```bash
npm run build:css
```

### Watch CSS (Development)
Watches for changes and rebuilds automatically:

```bash
npm run watch:css
```

**Important:** Run this command in a separate terminal during development to automatically rebuild CSS when you make changes to your Razor components or the Tailwind input file.

## File Structure

- **`Styles/tailwind.css`** - Input file with Tailwind directives and custom styles
- **`wwwroot/css/tailwind.css`** - Generated output file (included in HTML)
- **`tailwind.config.js`** - Tailwind configuration
- **`postcss.config.js`** - PostCSS configuration

## Configuration

### Content Paths
The `tailwind.config.js` scans these paths for class names:
- `./Components/**/*.{razor,html,cshtml}`
- `./Pages/**/*.{razor,html,cshtml}`
- `./wwwroot/index.html`

### Custom Theme
Extended colors and fonts are configured in `tailwind.config.js`.

### Custom Classes
Custom component classes are defined in `Styles/tailwind.css`:
- `.btn-primary` - Primary button styles
- `.card` - Card component styles
- `.input-field` - Input field styles

## Usage

### In Razor Components
Simply use Tailwind utility classes:

```razor
<div class="flex items-center justify-center p-4">
    <button class="btn-primary">Click me</button>
</div>
```

### Adding Custom Styles
Add custom styles to `Styles/tailwind.css` using the `@layer` directive:

```css
@layer components {
    .my-custom-class {
        @apply bg-blue-500 text-white p-4 rounded;
    }
}
```

Then rebuild:
```bash
npm run build:css
```

## Development Workflow

1. **Start watch mode** (in a separate terminal):
   ```bash
   npm run watch:css
```

2. **Run your .NET MAUI app** as normal in Visual Studio

3. **Make changes** to your Razor components - Tailwind will automatically rebuild the CSS

4. **Reload the app** to see your changes

## Production Build

Before deploying, always run:

```bash
npm run build:css
```

This creates an optimized, minified CSS file.

## Troubleshooting

### CSS not updating
- Make sure `npm run watch:css` is running
- Check that your files are in the paths specified in `tailwind.config.js`
- Rebuild manually with `npm run build:css`

### Classes not working
- Ensure `wwwroot/css/tailwind.css` exists and is linked in `wwwroot/index.html`
- Clear browser cache
- Rebuild the CSS

### npm commands not working
- Run `npm install` to ensure all dependencies are installed
- Check that Node.js is installed: `node --version`
