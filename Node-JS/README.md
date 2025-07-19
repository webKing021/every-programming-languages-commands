# Node.js Commands Reference

## Installation & Version Management

```bash
# Install Node.js using NVM (Node Version Manager)
## Install NVM (Linux/macOS)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
## Install NVM (Windows - requires separate installation of nvm-windows)

# List available Node.js versions
nvm ls-remote

# Install specific Node.js version
nvm install 18.16.0

# Use specific Node.js version
nvm use 18.16.0

# Set default Node.js version
nvm alias default 18.16.0

# Check current Node.js version
node -v

# Check npm version
npm -v
```

## Project Initialization

```bash
# Initialize a new Node.js project
npm init

# Initialize a new Node.js project with default values
npm init -y

# Create a package.json with specific values
npm init --yes --scope=username

# Initialize a TypeScript Node.js project
npm init -y
npm install typescript @types/node ts-node --save-dev
npx tsc --init
```

## Package Management

```bash
# Install a package
npm install package-name

# Install a package as a development dependency
npm install package-name --save-dev

# Install a specific version of a package
npm install package-name@1.2.3

# Install packages globally
npm install -g package-name

# Update packages
npm update

# Update specific package
npm update package-name

# Remove a package
npm uninstall package-name

# List installed packages
npm list

# List globally installed packages
npm list -g

# List top-level installed packages
npm list --depth=0

# Check for outdated packages
npm outdated

# Install all dependencies from package.json
npm install

# Install only production dependencies
npm install --production

# Clean npm cache
npm cache clean --force
```

## Running Scripts

```bash
# Run a script defined in package.json
npm run script-name

# Run the start script
npm start

# Run the test script
npm test

# Run Node.js with a file
node app.js

# Run TypeScript file with ts-node
npx ts-node app.ts

# Run with environment variables
NODE_ENV=production node app.js

# Run with debugging enabled
node --inspect app.js

# Run with debugging enabled and break on start
node --inspect-brk app.js
```

## Development Tools

```bash
# Install nodemon for auto-restarting
npm install -g nodemon

# Run with nodemon
nodemon app.js

# Run with nodemon and specific extensions to watch
nodemon --ext js,json,hbs app.js

# Install ESLint
npm install eslint --save-dev

# Initialize ESLint configuration
npx eslint --init

# Run ESLint
npx eslint .

# Run ESLint with auto-fix
npx eslint . --fix

# Install Prettier
npm install prettier --save-dev

# Format code with Prettier
npx prettier --write .

# Check formatting with Prettier
npx prettier --check .
```

## TypeScript

```bash
# Install TypeScript
npm install -g typescript

# Initialize a TypeScript configuration file
tsc --init

# Compile TypeScript
tsc

# Compile TypeScript with watch mode
tsc --watch

# Run TypeScript directly
npx ts-node app.ts

# Type check without emitting files
tsc --noEmit
```

## Testing

```bash
# Install Jest
npm install jest --save-dev

# Run Jest tests
npx jest

# Run Jest tests with coverage
npx jest --coverage

# Run Jest tests in watch mode
npx jest --watch

# Install Mocha and Chai
npm install mocha chai --save-dev

# Run Mocha tests
npx mocha
```

## Database Tools

```bash
# Install MongoDB driver
npm install mongodb

# Install Mongoose (MongoDB ODM)
npm install mongoose

# Install MySQL driver
npm install mysql2

# Install PostgreSQL driver
npm install pg

# Install Sequelize ORM
npm install sequelize

# Install Prisma ORM
npm install prisma --save-dev
npm install @prisma/client

# Initialize Prisma
npx prisma init

# Generate Prisma client
npx prisma generate

# Run Prisma migrations
npx prisma migrate dev
```

## Web Frameworks

```bash
# Install Express.js
npm install express

# Install Express generator
npm install -g express-generator

# Generate Express application
express my-app

# Install Fastify
npm install fastify

# Install NestJS CLI
npm install -g @nestjs/cli

# Create a new NestJS project
nest new project-name
```

## Security

```bash
# Install security audit tools
npm install -g npm-audit-resolver

# Run security audit
npm audit

# Fix security issues automatically
npm audit fix

# Install Helmet (Express.js security)
npm install helmet

# Install CORS middleware
npm install cors
```

## Deployment & Production

```bash
# Install PM2 process manager
npm install -g pm2

# Start an application with PM2
pm2 start app.js

# Start an application with a name
pm2 start app.js --name "my-app"

# List running applications
pm2 list

# Monitor applications
pm2 monit

# View logs
pm2 logs

# Restart application
pm2 restart app-name

# Stop application
pm2 stop app-name

# Delete application from PM2
pm2 delete app-name

# Generate startup script
pm2 startup

# Save current PM2 configuration
pm2 save
```

## Documentation

```bash
# Install JSDoc
npm install -g jsdoc

# Generate documentation
jsdoc app.js -d docs

# Install TypeDoc (for TypeScript)
npm install -g typedoc

# Generate TypeScript documentation
typedoc --out docs src
```

## Miscellaneous

```bash
# Check for npm registry status
npm ping

# View npm configuration
npm config list

# Set npm configuration
npm config set key value

# Get npm configuration value
npm config get key

# Run script with environment variables from .env file
npm install dotenv

# Check for Node.js vulnerabilities
npx snyk test

# Analyze bundle size
npx webpack-bundle-analyzer stats.json

# Create a tarball of your package
npm pack

# Publish package to npm registry
npm publish
```