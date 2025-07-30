# Vue + Vite + Deno Tutorial

A complete tutorial project demonstrating how to build a Vue.js application with Vite and Deno, featuring a full-stack TypeScript setup with a Deno backend.

## Make it your own!

You can deploy your own version of this Vue app to Deno Deploy immediately.
Just click the button to clone and deploy.

[![Deploy on Deno](https://deno.com/button)](https://app.deno.com/new?clone=https://github.com/denoland/tutorial-with-vue&mode=dynamic&entrypoint=api/main.ts&build=deno+task+build&install=deno+install)

## Overview

This project showcases how to:
- Build a Vue.js frontend with Vite and TypeScript
- Create a Deno backend API using Oak framework
- Serve both development and production builds
- Deploy to Deno Deploy

The app is a simple dinosaur explorer that displays a list of dinosaurs and shows detailed information when you click on one.

## Project Structure

```
├── api/                    # Deno backend server
│   ├── main.ts            # Main server file with API routes
│   ├── data.json          # Sample dinosaur data
│   └── util/              # Server utilities
├── src/                   # Vue.js frontend source
│   ├── components/        # Vue components
│   ├── router/           # Vue Router configuration
│   └── main.ts           # App entry point
├── public/               # Static assets
├── dist/                 # Built frontend (generated)
├── deno.json            # Deno configuration and imports
├── package.json         # NPM dependencies for Vite
└── vite.config.ts       # Vite configuration
```

## Prerequisites

- [Deno](https://deno.land/) installed on your machine
- Basic knowledge of Vue.js and TypeScript

## Installation & Setup

1. **Clone or download this project**

2. **Install Deno** (if not already installed):
   ```bash
   curl -fsSL https://deno.land/install.sh | sh
   ```
   
   On Windows, you can use PowerShell:
   ```powershell
   irm https://deno.land/install.ps1 | iex
   ```

3. **Install dependencies**:
   ```bash
   deno install
   ```

## Development

### Start the development servers:
```bash
npm run dev
```

This command starts:
- **Deno API server** on `http://localhost:8000` (Oak + TypeScript)
- **Vite dev server** on `http://localhost:3000` (Vue.js with HMR)

The Vite server automatically proxies API requests to the Deno server.

### Start servers individually:
```bash
# API server only
npm run dev:api

# Vite dev server only
npm run dev:vite
```

## Building for Production

### Build the Vue application:
```bash
npm run build
```

This creates an optimized build in the `dist/` directory.

### Serve the production build:
```bash
npm run serve
```

This builds the app and serves everything from the Deno server on `http://localhost:8000`.

## Key Features

### Frontend (Vue.js + Vite)
- ✅ Vue 3 with Composition API
- ✅ TypeScript support
- ✅ Vue Router for client-side routing
- ✅ Hot Module Replacement (HMR)
- ✅ Optimized production builds

### Backend (Deno + Oak)
- ✅ TypeScript-first development
- ✅ Oak framework for HTTP server
- ✅ CORS support for development
- ✅ Static file serving for production
- ✅ JSON API endpoints

### Development Experience
- ✅ API proxy during development
- ✅ Automatic server restart with `--watch`
- ✅ Single command to start everything
- ✅ Production-ready build process

## API Endpoints

- `GET /api/dinosaurs` - Get all dinosaurs
- `GET /api/dinosaurs/:name` - Get specific dinosaur by name

## Configuration Files

### `deno.json`
Defines Deno imports and tasks:
```json
{
  "imports": {
    "@oak/oak": "jsr:@oak/oak@^17.1.5",
    "@tajpouria/cors": "jsr:@tajpouria/cors@^1.2.1",
    "vue-router": "npm:vue-router@^4.5.1"
  }
}
```

### `vite.config.ts`
Configures Vite with Deno plugin and API proxy:
```typescript
export default defineConfig({
  server: {
    proxy: {
      "/api": "http://localhost:8000"
    }
  },
  plugins: [vue(), deno()]
});
```

## Deploying to Deno Deploy

1. **Push your code to GitHub**

2. **Connect to Deno Deploy**:
   - Go to [dash.deno.com](https://dash.deno.com)
   - Create a new project
   - Connect your GitHub repository

3. **Configure the deployment**:
   - Entry point: `api/main.ts`
   - Build command: `npm run build`
   - The built Vue app will be served alongside the API

4. **Environment variables** (if needed):
   - Set any required environment variables in the Deno Deploy dashboard

## Tutorial

This project is part of a comprehensive tutorial. You can follow along with the complete tutorial at: [Deno Docs - Vue.js Tutorial](https://docs.deno.com/runtime/tutorials/how_to_with_npm/vue/)

## Learn More

- [Deno Documentation](https://docs.deno.com/)
- [Vue.js Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Oak Framework](https://github.com/oakserver/oak)
- [Deno Deploy](https://deno.com/deploy)
