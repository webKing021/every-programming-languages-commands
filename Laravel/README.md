# Laravel Commands Reference

## Installation & Setup

```bash
# Install Laravel installer
composer global require laravel/installer

# Create a new Laravel project
laravel new project-name

# Create a new Laravel project via Composer
composer create-project --prefer-dist laravel/laravel project-name

# Create a new Laravel project with specific version
composer create-project --prefer-dist laravel/laravel project-name "8.*"

# Start development server
php artisan serve

# Start development server on specific host/port
php artisan serve --host=0.0.0.0 --port=8080
```

## Configuration

```bash
# Generate application key
php artisan key:generate

# Clear configuration cache
php artisan config:clear

# Cache configuration
php artisan config:cache

# List all available commands
php artisan list

# Display help for a command
php artisan help command-name
```

## Database

```bash
# Run migrations
php artisan migrate

# Run migrations with seed
php artisan migrate --seed

# Rollback last migration
php artisan migrate:rollback

# Rollback all migrations
php artisan migrate:reset

# Refresh migrations (rollback and migrate)
php artisan migrate:refresh

# Refresh migrations with seed
php artisan migrate:refresh --seed

# Create a migration
php artisan make:migration create_users_table

# Create a migration for specific table
php artisan make:migration add_column_to_users_table --table=users

# Run specific seeder
php artisan db:seed --class=UserSeeder

# Create a seeder
php artisan make:seeder UserSeeder

# Create a factory
php artisan make:factory PostFactory --model=Post
```

## Models & Controllers

```bash
# Create a model
php artisan make:model User

# Create a model with migration
php artisan make:model User --migration

# Create a model with controller
php artisan make:model User --controller

# Create a model with factory
php artisan make:model User --factory

# Create a model with all resources
php artisan make:model User -mfsc

# Create a controller
php artisan make:controller UserController

# Create a resource controller
php artisan make:controller UserController --resource

# Create an API controller
php artisan make:controller API/UserController --api
```

## Routes & Middleware

```bash
# List all routes
php artisan route:list

# Clear route cache
php artisan route:clear

# Cache routes
php artisan route:cache

# Create middleware
php artisan make:middleware CheckAge
```

## Views & Frontend

```bash
# Clear view cache
php artisan view:clear

# Cache views
php artisan view:cache

# Install frontend scaffolding (Laravel 7 and below)
php artisan ui bootstrap
php artisan ui vue
php artisan ui react

# Install frontend scaffolding with auth
php artisan ui bootstrap --auth
php artisan ui vue --auth
php artisan ui react --auth

# Compile assets (requires npm install first)
npm run dev

# Watch assets for changes
npm run watch

# Compile assets for production
npm run production
```

## Authentication & Authorization

```bash
# Create authentication scaffolding (Laravel 8+)
composer require laravel/ui
php artisan ui bootstrap --auth

# Install Breeze (Laravel 8+)
composer require laravel/breeze --dev
php artisan breeze:install

# Install Jetstream (Laravel 8+)
composer require laravel/jetstream
php artisan jetstream:install livewire
# or
php artisan jetstream:install inertia

# Create a policy
php artisan make:policy PostPolicy

# Create a policy for a model
php artisan make:policy PostPolicy --model=Post
```

## Queues & Jobs

```bash
# Create a job
php artisan make:job ProcessPodcast

# Run queue worker
php artisan queue:work

# Run queue worker once
php artisan queue:work --once

# Run queue worker for specific queue
php artisan queue:work --queue=high,default

# Run queue worker with timeout
php artisan queue:work --timeout=60

# Restart queue workers
php artisan queue:restart

# Create a listener
php artisan make:listener SendPodcastNotification

# Create an event
php artisan make:event PodcastProcessed
```

## Testing

```bash
# Run tests
php artisan test

# Run specific test file
php artisan test --filter=ExampleTest

# Create a test
php artisan make:test UserTest

# Create a unit test
php artisan make:test UserTest --unit
```

## Cache & Storage

```bash
# Clear application cache
php artisan cache:clear

# Create a symbolic link for storage
php artisan storage:link

# Clear compiled views
php artisan view:clear

# Clear expired password reset tokens
php artisan auth:clear-resets
```

## Artisan Tinker

```bash
# Start Tinker (REPL)
php artisan tinker
```

## Maintenance Mode

```bash
# Put application in maintenance mode
php artisan down

# Put application in maintenance mode with message
php artisan down --message="Upgrading Database" --retry=60

# Bring application out of maintenance mode
php artisan up
```

## Packages & Resources

```bash
# Create a resource
php artisan make:resource UserResource

# Create a collection resource
php artisan make:resource Users --collection

# Create a mail class
php artisan make:mail OrderShipped

# Create a notification
php artisan make:notification InvoicePaid

# Create a command
php artisan make:command SendEmails

# Create a channel
php artisan make:channel OrderChannel

# Create a component
php artisan make:component Alert
```

## Optimization

```bash
# Optimize class autoloader
composer dump-autoload -o

# Optimize for production
php artisan optimize

# Clear optimization cache
php artisan optimize:clear
```

## Deployment

```bash
# Deploy with minimal downtime
php artisan down --refresh=15
php artisan migrate --force
php artisan optimize
php artisan up
```

## Scheduling

```bash
# Run scheduled tasks
php artisan schedule:run

# Run scheduled tasks in foreground
php artisan schedule:work
```

## Miscellaneous

```bash
# Create a request
php artisan make:request StoreUserRequest

# Create a rule
php artisan make:rule Uppercase

# Create a provider
php artisan make:provider RiakServiceProvider

# Create a trait
php artisan make:trait HasTimestamps

# Create an interface
php artisan make:interface RepositoryInterface

# Create an exception
php artisan make:exception CustomException
```