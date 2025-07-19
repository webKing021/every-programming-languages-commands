# React.js Commands Reference

## Project Creation & Setup

```bash
# Create a new React application
npx create-react-app my-app

# Create a new React application with TypeScript
npx create-react-app my-app --template typescript

# Create a new React application with specific template
npx create-react-app my-app --template redux

# Create a Vite React project
npm create vite@latest my-app -- --template react

# Create a Vite React project with TypeScript
npm create vite@latest my-app -- --template react-ts

# Install dependencies in existing project
npm install
# or
yarn
# or
pnpm install
```

## Development

```bash
# Start development server (Create React App)
npm start
# or
yarn start
# or
pnpm start

# Start development server (Vite)
npm run dev
# or
yarn dev
# or
pnpm dev

# Start development server on specific port (Create React App)
PORT=3001 npm start
# or
PORT=3001 yarn start
# or
PORT=3001 pnpm start

# Start development server on specific port (Vite)
npm run dev -- --port 3001
# or
yarn dev --port 3001
# or
pnpm dev -- --port 3001
```

## Building & Production

```bash
# Build for production (Create React App)
npm run build
# or
yarn build
# or
pnpm build

# Build for production (Vite)
npm run build
# or
yarn build
# or
pnpm build

# Analyze bundle size (Create React App)
npm run build -- --stats
npx source-map-explorer 'build/static/js/*.js'

# Serve production build locally (Create React App)
npx serve -s build

# Serve production build locally (Vite)
npx serve -s dist
```

## Testing

```bash
# Run tests
npm test
# or
yarn test
# or
pnpm test

# Run tests in watch mode
npm test -- --watch
# or
yarn test --watch
# or
pnpm test -- --watch

# Run tests with coverage
npm test -- --coverage
# or
yarn test --coverage
# or
pnpm test -- --coverage

# Run specific test file
npm test -- src/components/Button.test.js
# or
yarn test src/components/Button.test.js
# or
pnpm test -- src/components/Button.test.js

# Run E2E tests with Cypress
npx cypress open
# or
npx cypress run
```

## Linting & Formatting

```bash
# Run ESLint
npm run lint
# or
yarn lint
# or
npx eslint .

# Run ESLint with auto-fix
npm run lint -- --fix
# or
yarn lint --fix
# or
npx eslint . --fix

# Run Prettier
npx prettier --check .

# Run Prettier with auto-fix
npx prettier --write .
```

## Ejecting (Create React App)

```bash
# Eject from Create React App (irreversible)
npm run eject
# or
yarn eject
# or
pnpm eject
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

# Remove a dependency
npm uninstall package-name
# or
yarn remove package-name
# or
pnpm remove package-name

# Update dependencies
npm update
# or
yarn upgrade
# or
pnpm update
```

## Common React Libraries

```bash
# State Management
npm install redux react-redux @reduxjs/toolkit
npm install zustand
npm install recoil
npm install jotai

# Routing
npm install react-router-dom

# Forms
npm install react-hook-form
npm install formik yup

# Data Fetching
npm install axios
npm install @tanstack/react-query
npm install swr

# UI Libraries
npm install @mui/material @emotion/react @emotion/styled
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
npm install antd
npm install react-bootstrap bootstrap

# Styling
npm install styled-components
npm install @emotion/react @emotion/styled
npm install tailwindcss postcss autoprefixer
npm install sass

# Animation
npm install framer-motion
npm install react-spring
npm install gsap

# Testing
npm install @testing-library/react @testing-library/jest-dom @testing-library/user-event --save-dev
npm install jest --save-dev
npm install cypress --save-dev
```

## Environment Variables

```bash
# Start with specific environment (Create React App)
REACT_APP_API_URL=https://api.example.com npm start

# Build with specific environment (Create React App)
REACT_APP_API_URL=https://api.example.com npm run build

# Start with specific environment (Vite)
VITE_API_URL=https://api.example.com npm run dev

# Build with specific environment (Vite)
VITE_API_URL=https://api.example.com npm run build
```

## Debugging

```bash
# Start with React DevTools
REACT_DEBUGGER=true npm start

# Debug tests
npm test -- --debug

# Debug with Node inspector
node --inspect-brk node_modules/.bin/jest --runInBand
```

## TypeScript

```bash
# Type check
npm run tsc
# or
yarn tsc
# or
pnpm tsc

# Type check in watch mode
npm run tsc -- --watch
# or
yarn tsc --watch
# or
pnpm tsc -- --watch

# Generate TypeScript declarations
npm run tsc -- --declaration
# or
yarn tsc --declaration
# or
pnpm tsc -- --declaration
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

# Deploy to GitHub Pages
npm install --save-dev gh-pages
# Add to package.json: "homepage": "https://username.github.io/repo-name"
# Add to scripts: "predeploy": "npm run build", "deploy": "gh-pages -d build"
npm run deploy
```

## Storybook

```bash
# Install Storybook
npx storybook init

# Start Storybook
npm run storybook
# or
yarn storybook
# or
pnpm storybook

# Build Storybook
npm run build-storybook
# or
yarn build-storybook
# or
pnpm build-storybook
```

## Miscellaneous

```bash
# Generate React component
npx generate-react-cli component Button

# Analyze bundle size
npm install --save-dev source-map-explorer
npm run build
npx source-map-explorer 'build/static/js/*.js'

# Check for outdated dependencies
npm outdated

# Update React to latest version
npm install react@latest react-dom@latest

# Clear cache (Create React App)
npm run start -- --no-cache
# or
yarn start --no-cache
# or
pnpm start -- --no-cache
```