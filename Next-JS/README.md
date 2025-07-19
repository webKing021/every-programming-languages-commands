# Next.js Commands Reference

## Installation & Setup

```bash
# Create a new Next.js app
npx create-next-app my-app

# Create a new Next.js app with TypeScript
npx create-next-app@latest --ts my-app
# or
npx create-next-app@latest my-app --typescript

# Create a new Next.js app with specific template
npx create-next-app my-app --example with-tailwindcss

# Create a new Next.js app with app directory
npx create-next-app@latest my-app --app

# Install dependencies in existing project
npm install next react react-dom
# or
yarn add next react react-dom
# or
pnpm add next react react-dom
```

## Development

```bash
# Start development server
npm run dev
# or
yarn dev
# or
pnpm dev

# Start development server on specific port
npm run dev -- -p 4000
# or
yarn dev -p 4000
# or
pnpm dev -- -p 4000

# Start development server with specific host
npm run dev -- -H 0.0.0.0
# or
yarn dev -H 0.0.0.0
# or
pnpm dev -- -H 0.0.0.0
```

## Building & Production

```bash
# Build for production
npm run build
# or
yarn build
# or
pnpm build

# Start production server
npm run start
# or
yarn start
# or
pnpm start

# Start production server on specific port
npm run start -- -p 4000
# or
yarn start -p 4000
# or
pnpm start -- -p 4000

# Export static site (for static site generation)
npm run export
# or
yarn export
# or
pnpm export
```

## Linting

```bash
# Run ESLint
npm run lint
# or
yarn lint
# or
pnpm lint

# Run ESLint with auto-fix
npm run lint -- --fix
# or
yarn lint --fix
# or
pnpm lint -- --fix
```

## Testing

```bash
# Run Jest tests
npm run test
# or
yarn test
# or
pnpm test

# Run Jest tests in watch mode
npm run test -- --watch
# or
yarn test --watch
# or
pnpm test -- --watch

# Run Cypress tests
npm run cypress
# or
yarn cypress
# or
pnpm cypress

# Open Cypress test runner
npm run cypress:open
# or
yarn cypress:open
# or
pnpm cypress:open
```

## Next.js CLI

```bash
# Display help information
npx next --help

# Display Next.js version
npx next --version

# Build and start production server
npx next build && npx next start

# Start with specific config file
npx next dev -c custom-config.js

# Build with specific config file
npx next build -c custom-config.js

# Start with specific config file
npx next start -c custom-config.js

# Enable telemetry
npx next telemetry enable

# Disable telemetry
npx next telemetry disable

# Show telemetry status
npx next telemetry status
```

## Environment Variables

```bash
# Start with specific environment
NODE_ENV=production npx next start

# Start with custom environment variables
API_URL=https://api.example.com npx next dev
```

## Debugging

```bash
# Enable debug mode
DEBUG=* npx next dev

# Debug specific parts
DEBUG=next:* npx next dev

# Node inspector
NODE_OPTIONS='--inspect' npx next dev
```

## Package Management

```bash
# Add a dependency
npm install package-name
# or
yarn add package-name
# or
pnpm add package-name

# Add a dev dependency
npm install --save-dev package-name
# or
yarn add --dev package-name
# or
pnpm add -D package-name

# Update dependencies
npm update
# or
yarn upgrade
# or
pnpm update
```

## Common Integrations

```bash
# Install Tailwind CSS
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# Install Chakra UI
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion

# Install Material UI
npm install @mui/material @emotion/react @emotion/styled

# Install Redux Toolkit
npm install @reduxjs/toolkit react-redux

# Install Axios
npm install axios

# Install React Query
npm install @tanstack/react-query

# Install Prisma
npm install -D prisma
npm install @prisma/client
npx prisma init

# Install NextAuth.js
npm install next-auth
```

## Deployment

```bash
# Deploy to Vercel
vercel

# Deploy to production on Vercel
vercel --prod

# Deploy to Netlify
netlify deploy

# Deploy to production on Netlify
netlify deploy --prod
```

## Miscellaneous

```bash
# Clear Next.js cache
rm -rf .next

# Generate TypeScript types for API routes
npx openapi-typescript https://api.example.com/openapi.json -o types/api.ts

# Install Storybook
npx sb init

# Run Storybook
npm run storybook
```