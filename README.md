# Wails + Svelte 5 Template

Modern Wails template using Svelte 5, Tailwind CSS v4, and shadcn-svelte components.

## Features

- Svelte 5 with TypeScript
- Tailwind CSS v4 for styling
- shadcn-svelte components (bits-ui)
- Vite 7 for frontend tooling
- Go backend with Wails v2

## Requirements

- Go 1.22+
- Node.js 20.19+ or 22.12+ (required by Vite 7)
- Wails CLI v2.11.0+

## Quick Start

```bash
# Create new project
wails init -n myapp -t https://github.com/bnema/wails-vite-svelte5-ts-taildwind-shadcn-template

# Install dependencies
cd myapp/frontend
npm install

# Start development
cd ..
wails dev
```

## Development

Add shadcn components:
```bash
npx shadcn-svelte@latest add [component-name]
```

## Building

Build production binary:
```bash
wails build
```

## Project Structure

```
├── frontend/          # Svelte frontend
│   ├── src/
│   └── package.json
├── app.go            # Backend logic
└── main.go           # Entry point
```

## License

MIT License

## Support

- GitHub Issues
- [Wails Discord](https://discord.gg/wails)
