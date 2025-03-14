# Quick Start Guide

This is a condensed version of the setup process for a Vite + React + Supabase + Tailwind CSS v4 + Shadcn UI project.

## 1. Project Setup

```bash
# Create Vite project
npm create vite@latest my-project
# Select "React" as framework
# Select "TypeScript" as variant

cd my-project
npm install

# Install Tailwind CSS v4
npm install tailwindcss @tailwindcss/vite

# Install Node.js type definitions
npm install -D @types/node

# Install Supabase
npm install @supabase/supabase-js

# Install React Router
npm install react-router-dom
```

## 2. Configuration Files

1. Update `src/index.css`:
```css
@import "tailwindcss";
```

2. Create `tsconfig.json` file:
```json
{
  "files": [],
  "references": [
    {
      "path": "./tsconfig.app.json"
    },
    {
      "path": "./tsconfig.node.json"
    }
  ],
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

3. Update `tsconfig.app.json` file:
```json
{
  "compilerOptions": {
    // ...other settings...
    "baseUrl": ".",
    "paths": {
      "@/*": [
        "./src/*"
      ]
    }
    // ...other settings...
  }
}
```

4. Update `vite.config.ts`:
```ts
import path from "path"
import tailwindcss from "@tailwindcss/vite"
import react from "@vitejs/plugin-react"
import { defineConfig } from "vite"
 
export default defineConfig({
  plugins: [react(), tailwindcss()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
})
```

5. Create `.env` file:
```
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

## 3. Setup Shadcn UI

```bash
# Initialize Shadcn UI
npx shadcn@latest init
# Choose a base color when prompted
# Enter "./src/components" as components path
# Enter "@/components" as components import alias

# Install basic UI components
npx shadcn@latest add button
npx shadcn@latest add input
npx shadcn@latest add card
npx shadcn@latest add form
```

## 4. Create Required Files

1. **Supabase client** (`src/lib/supabase.ts`) - Connect to your Supabase project
2. **Auth context** (`src/contexts/AuthContext.tsx`) - Handle authentication state
3. **Auth pages**:
   - Login page (`src/pages/Login.tsx`)
   - Register page (`src/pages/Register.tsx`)
   - Reset Password page (`src/pages/ResetPassword.tsx`)
4. **Home/Hero page** (`src/pages/Home.tsx`) - Landing page with authentication state
5. **App routing** (`src/App.tsx`) - Set up protected routes
6. **Update main.tsx** to include BrowserRouter and AuthProvider

## 5. Supabase Setup

1. Create a project at [supabase.com](https://supabase.com)
2. Get your project URL and Anon Key from Project Settings > API
3. Configure Authentication settings in the Supabase dashboard

## 6. Run the App

```bash
npm run dev
```

Visit `http://localhost:5173` to see your application running.

## Next Steps

- Add more pages and components as needed
- Set up database tables in Supabase
- Implement data fetching with Supabase client
- Add more authentication providers as needed
- Style your app further with Tailwind CSS classes 