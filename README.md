# Wails + Svelte 5 Template

Modern Wails template using Svelte 5, Tailwind CSS, and shadcn-svelte components.

## Features

- Svelte 5 with TypeScript
- Tailwind CSS for styling
- shadcn-svelte components
- Vite for frontend tooling
- Go backend with Wails

## Requirements

- Go 1.21+
- Node.js 18+
- Wails CLI v2.7.0+

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
npx shadcn-svelte@next add [component-name]
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
