# Django Commands Reference

## Environment Setup

```bash
# Create a virtual environment
python -m venv .venv

# Activate virtual environment (Windows)
.venv\Scripts\activate

# Activate virtual environment (macOS/Linux)
source .venv/bin/activate

# Install Django
pip install Django
```

## Project Management

```bash
# Create a new Django project
django-admin startproject project_name

# Create a new app within a project
python manage.py startapp app_name
# or
django-admin startapp app_name

# Run development server
python manage.py runserver

# Run development server on specific port
python manage.py runserver 8080
```

## Database Operations

```bash
# Create migrations based on model changes
python manage.py makemigrations

# Apply migrations to database
python manage.py migrate

# Show migration status
python manage.py showmigrations

# Create a specific migration for an app
python manage.py makemigrations app_name

# Apply specific migration
python manage.py migrate app_name migration_name

# Rollback to a specific migration
python manage.py migrate app_name migration_name

# Create a superuser for admin access
python manage.py createsuperuser

# Reset database for an app
python manage.py flush
```

## Database Connections

```bash
# Install MySQL client
pip install mysqlclient

# Install PostgreSQL client
pip install psycopg2
```

## Shell and Testing

```bash
# Open Django shell
python manage.py shell

# Open Django shell with IPython
python manage.py shell -i ipython

# Run tests
python manage.py test

# Run tests for a specific app
python manage.py test app_name

# Run tests with coverage
coverage run --source='.' manage.py test
coverage report
```

## Static Files

```bash
# Collect static files
python manage.py collectstatic

# Collect static files without asking for confirmation
python manage.py collectstatic --noinput
```

## Deployment

```bash
# Check for deployment issues
python manage.py check --deploy

# Generate a requirements file
pip freeze > requirements.txt
```

## Django Extensions

```bash
# Install Django Extensions
pip install django-extensions

# Generate ERD diagram (requires graphviz)
python manage.py graph_models -a -o project_diagram.png
```

## Tailwind CSS Integration

```bash
# Update pip
python -m pip install --upgrade pip

# Install Django Tailwind
pip install django-tailwind

# Install Django Tailwind with live reload
pip install 'django-tailwind[reload]'

# Initialize Tailwind in your project
python manage.py tailwind init

# Install Tailwind dependencies
python manage.py tailwind install

# Start Tailwind development server
python manage.py tailwind start
```

## Django REST Framework

```bash
# Install Django REST Framework
pip install djangorestframework

# Install Markdown support for the browsable API
pip install markdown

# Install filtering support
pip install django-filter
```

## Internationalization

```bash
# Make messages for translation
python manage.py makemessages -l es

# Compile translation messages
python manage.py compilemessages
```

## Cache Management

```bash
# Clear cache
python manage.py clearcache

# Create cache table
python manage.py createcachetable
```

## Security

```bash
# Generate a new secret key
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```