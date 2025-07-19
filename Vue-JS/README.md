# Vue.js Commands Reference

## Installation & Setup

```bash
# Install Vue CLI globally
npm install -g @vue/cli

# Check Vue CLI version
vue --version

# Create a new project with Vue CLI
vue create my-project

# Create a new project with specific preset
vue create --preset username/repo my-project

# Create a project with Vite
npm create vite@latest my-project -- --template vue

# Create a project with Vite and TypeScript
npm create vite@latest my-project -- --template vue-ts

# Add Vue to an existing project
npm install vue
```

## Vue CLI Commands

```bash
# Vue CLI UI
vue ui

# Add a plugin to an existing project
vue add plugin-name

# Add Vuetify to an existing project
vue add vuetify

# Add Vue Router to an existing project
vue add router

# Add Vuex to an existing project
vue add vuex

# Add TypeScript to an existing project
vue add typescript

# Add unit testing to an existing project
vue add unit-jest

# Add E2E testing to an existing project
vue add e2e-cypress

# Inspect webpack config
vue inspect

# Inspect specific webpack config
vue inspect --mode production

# Output webpack config to a file
vue inspect > webpack.config.js
```

## Development

```bash
# Start development server (Vue CLI)
npm run serve
# or
yarn serve
# or
pnpm serve

# Start development server (Vite)
npm run dev
# or
yarn dev
# or
pnpm dev

# Start development server on specific port (Vue CLI)
npm run serve -- --port 3001
# or
yarn serve --port 3001
# or
pnpm serve -- --port 3001

# Start development server on specific port (Vite)
npm run dev -- --port 3001
# or
yarn dev --port 3001
# or
pnpm dev -- --port 3001

# Start development server with specific mode
npm run serve -- --mode staging
# or
yarn serve --mode staging
# or
pnpm serve -- --mode staging
```

## Building & Production

```bash
# Build for production (Vue CLI)
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

# Build with specific mode
npm run build -- --mode staging
# or
yarn build --mode staging
# or
pnpm build -- --mode staging

# Build with bundle analyzer report (Vue CLI)
npm run build -- --report
# or
yarn build --report
# or
pnpm build -- --report

# Preview production build (Vue CLI)
npm run serve -- --mode production
# or
yarn serve --mode production
# or
pnpm serve -- --mode production

# Preview production build (Vite)
npm run preview
# or
yarn preview
# or
pnpm preview
```

## Testing

```bash
# Run unit tests
npm run test:unit
# or
yarn test:unit
# or
pnpm test:unit

# Run unit tests in watch mode
npm run test:unit -- --watch
# or
yarn test:unit --watch
# or
pnpm test:unit -- --watch

# Run E2E tests
npm run test:e2e
# or
yarn test:e2e
# or
pnpm test:e2e

# Run E2E tests headlessly
npm run test:e2e -- --headless
# or
yarn test:e2e --headless
# or
pnpm test:e2e -- --headless
```

## Linting & Formatting

```bash
# Lint code
npm run lint
# or
yarn lint
# or
pnpm lint

# Lint and fix code
npm run lint -- --fix
# or
yarn lint --fix
# or
pnpm lint -- --fix

# Format code with Prettier
npx prettier --write .
```

## TypeScript

```bash
# Type check
vue-tsc --noEmit
# or
npm run type-check

# Type check in watch mode
vue-tsc --noEmit --watch
# or
npm run type-check -- --watch
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

## Common Vue Libraries

```bash
# State Management
npm install vuex@next
npm install pinia

# Routing
npm install vue-router@next

# Forms
npm install vee-validate@next
npm install @vuelidate/core @vuelidate/validators

# Data Fetching
npm install axios

# UI Libraries
npm install vuetify@next
npm install primevue
npm install quasar
npm install element-plus
npm install bootstrap-vue@next

# Styling
npm install sass
npm install tailwindcss postcss autoprefixer
npm install @tailwindcss/forms @tailwindcss/typography

# Animation
npm install @vueuse/motion
npm install gsap

# Internationalization
npm install vue-i18n@next

# Testing
npm install --save-dev @vue/test-utils@next
npm install --save-dev vitest
npm install --save-dev cypress
```

## Environment Variables

```bash
# Start with specific environment (Vue CLI)
VUE_APP_API_URL=https://api.example.com npm run serve

# Build with specific environment (Vue CLI)
VUE_APP_API_URL=https://api.example.com npm run build

# Start with specific environment (Vite)
VITE_API_URL=https://api.example.com npm run dev

# Build with specific environment (Vite)
VITE_API_URL=https://api.example.com npm run build
```

## Debugging

```bash
# Debug with Vue Devtools
# Install Vue Devtools browser extension

# Debug tests
npm run test:unit -- --debug
# or
yarn test:unit --debug
# or
pnpm test:unit -- --debug
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
# Add to scripts: "predeploy": "npm run build", "deploy": "gh-pages -d dist"
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

## Vue 2 Specific Commands

```bash
# Create a Vue 2 project
vue create --preset vue2 my-project
# or
npm create vite@latest my-project -- --template vue-2

# Add Vue 2 to an existing project
npm install vue@2

# Add Vuex to Vue 2 project
npm install vuex@3

# Add Vue Router to Vue 2 project
npm install vue-router@3

# Add Composition API to Vue 2
npm install @vue/composition-api
```

## Miscellaneous

```bash
# Generate Vue component
npx vue-generate-component MyComponent

# Analyze bundle size (Vue CLI)
npm run build -- --report

# Analyze bundle size (Vite)
npm install --save-dev rollup-plugin-visualizer

# Check for outdated dependencies
npm outdated

# Update Vue to latest version
npm install vue@latest

# Clear cache (Vue CLI)
npm run serve -- --no-cache
# or
yarn serve --no-cache
# or
pnpm serve -- --no-cache
```