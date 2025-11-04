# Dashboard Layout

The `DashboardLayout` is a reusable layout component for all dashboard-related pages in the BrightenEnroll application.

## Features

- **Sidebar Navigation**: Fixed sidebar with logo and navigation menu
- **Active State**: Automatically highlights the current page in the navigation
- **Top Bar**: Displays page title and user profile
- **Responsive**: Collapsible sidebar for mobile devices
- **Logout**: Built-in logout button that redirects to login page

## Usage

To use the DashboardLayout in a page, add this directive at the top of your Razor file:

```razor
@page "/your-page"
@layout Layout.DashboardLayout
```

## Navigation Menu Items

The layout includes the following menu items:
- Dashboard (`/dashboard`)
- Enrollment (`/enrollment`)
- Student Record (`/student-record`)
- Academics (`/academics`)
- Finance (`/finance`)
- Human Resource (`/human-resource`)

## Page Titles

Page titles are automatically set based on the current route. The mapping is defined in the `GetPageTitle()` method.

## Customization

### Adding New Menu Items

Edit `Components/Layout/DashboardLayout.razor` and add a new `NavLink`:

```razor
<NavLink href="/your-new-page" class="flex items-center gap-3 px-4 py-3 mb-2 rounded-lg font-medium transition-all">
    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <!-- Your icon SVG path -->
    </svg>
    Your Page Name
</NavLink>
```

### Updating Page Title Mapping

Add your page to the switch statement in the `GetPageTitle()` method:

```csharp
return currentPath switch
{
// ...existing cases...
"your-new-page" => "Your Page Title",
    _ => "Dashboard"
};
```

## Styling

The layout uses:
- **Tailwind CSS**: For utility classes
- **DashboardLayout.razor.css**: For component-scoped styles (navigation active states)

Active navigation links are styled with:
- Blue background (`#eff6ff`)
- Blue text (`#2563eb`)
- Blue right border (4px)

## User Profile

The user profile section currently displays:
- Avatar (generated from UI Avatars API)
- Name: "Moni Roy"
- Role: "Admin"

To customize, update the user profile section in the Top Bar.
