# De la Idea a Internet — Base Project

This is the base project for the workshop **"De la Idea a Internet: Crea y
Despliega tu Landing Page con Antigravity, Stitch y React"** by
**Cristian Delcid**, part of the
**Build with AI Zona Sur** event, hosted by **GDG Choluteca**.

It ships a clean template with the full stack pre-configured and a theme provider
to toggle between light and dark mode, ready to start building the event's
landing page.

## Tech Stack

- **React 19** + **TypeScript**
- **Vite** — dev server and build tooling
- **Tailwind CSS v4** — styling (CSS-first config, no `tailwind.config.ts`)
- **shadcn/ui** (`base-nova` style) — component primitives (built on **Radix UI**)
- **Lucide React** — icons
- **Open Sans** (Fontsource, local import) — typography
- **pnpm** — package manager

## Installed Packages

### Dependencies

| Package | Version | Purpose |
|---|---|---|
| `react` | ^19.2 | UI library |
| `react-dom` | ^19.2 | React DOM renderer |
| `vite` | ^8.1 | Dev server and bundler |
| `tailwindcss` | ^4.3 | Utility-first CSS framework |
| `@tailwindcss/vite` | ^4.3 | Tailwind Vite plugin |
| `shadcn` | ^4.11 | shadcn/ui CLI and runtime |
| `radix-ui` | ^1.6 | Headless UI primitives |
| `@base-ui/react` | ^1.6 | Base primitives for shadcn |
| `class-variance-authority` | ^0.7 | Component variant API |
| `clsx` | ^2.1 | CSS class concatenation utility |
| `tailwind-merge` | ^3.6 | Smart Tailwind class merging |
| `lucide-react` | ^1.21 | Icon library |
| `tw-animate-css` | ^1.4 | CSS animation utilities for Tailwind |
| `sonner` | ^2.0 | Toast notification component |
| `@fontsource-variable/open-sans` | ^5.2 | Open Sans font (variable) |
| `@fontsource-variable/geist` | ^5.2 | Geist font (shadcn peer dep) |

### Dev Dependencies

| Package | Version | Purpose |
|---|---|---|
| `typescript` | ~6.0 | Type checker |
| `@vitejs/plugin-react` | ^6.0 | React support for Vite |
| `@types/react` | ^19.2 | TypeScript types for React |
| `@types/react-dom` | ^19.2 | TypeScript types for React DOM |
| `@types/node` | ^24.13 | TypeScript types for Node.js |
| `oxlint` | ^1.69 | Blazing-fast linter |

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) 20+
- [pnpm](https://pnpm.io/) (`npm install -g pnpm`)

### Install dependencies

```bash
pnpm install
```

### Development environment

```bash
pnpm dev
```

The app runs at the URL Vite prints (default `http://localhost:5173`).

### Production build

```bash
pnpm build
```

The optimized output is generated in the `dist/` directory. To preview the
production build locally:

```bash
pnpm preview
```

## Other Scripts

```bash
pnpm lint        # run oxlint
```

## Adding shadcn/ui Components

```bash
pnpm dlx shadcn@latest add <component>
```

Components are placed in `src/components/ui` and can be imported via the `@` alias:

```tsx
import { Button } from "@/components/ui/button"
```

## Theme (Dark / Light)

The project includes a `ThemeProvider` in `src/components/theme-provider.tsx` that
supports three modes: `light`, `dark`, and `system`. The preference is persisted
in `localStorage`.

To use the theme from any component:

```tsx
import { useTheme } from "@/components/theme-provider"

function ThemeToggle() {
  const { theme, setTheme } = useTheme()
  return (
    <button onClick={() => setTheme(theme === "dark" ? "light" : "dark")}>
      Toggle theme
    </button>
  )
}
```
