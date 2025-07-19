# Flask Commands Reference

## Environment Setup

```bash
# Create a virtual environment
python -m venv venv

# Activate virtual environment (Windows)
venv\Scripts\activate

# Activate virtual environment (macOS/Linux)
source venv/bin/activate

# Install Flask
pip install Flask
```

## Basic Flask Commands

```bash
# Set Flask application (Windows)
set FLASK_APP=app.py

# Set Flask application (macOS/Linux)
export FLASK_APP=app.py

# Enable development mode (Windows)
set FLASK_DEBUG=1

# Enable development mode (macOS/Linux)
export FLASK_DEBUG=1

# Run Flask application using Python
python app.py

# Run Flask application using Flask CLI
flask run

# Run with debug mode
flask run --debug

# Run on different host/port
flask run --host=0.0.0.0 --port=8080
```

## Flask Extensions

### Flask-SQLAlchemy

```bash
# Install Flask-SQLAlchemy
pip install Flask-SQLAlchemy

# Install database drivers
pip install psycopg2-binary  # PostgreSQL
pip install mysqlclient      # MySQL
```

### Flask-Migrate

```bash
# Install Flask-Migrate
pip install Flask-Migrate

# Initialize migrations
flask db init

# Create a migration
flask db migrate -m "Initial migration"

# Apply migration
flask db upgrade

# Downgrade to previous migration
flask db downgrade
```

### Flask-WTF (Forms)

```bash
# Install Flask-WTF
pip install Flask-WTF
```

### Flask-Login (Authentication)

```bash
# Install Flask-Login
pip install Flask-Login
```

### Flask-RESTful

```bash
# Install Flask-RESTful
pip install Flask-RESTful
```

### Flask-JWT-Extended

```bash
# Install Flask-JWT-Extended
pip install Flask-JWT-Extended
```

## Testing

```bash
# Install pytest
pip install pytest

# Run tests
pytest

# Run tests with coverage
pip install pytest-cov
pytest --cov=app tests/
```

## Deployment

### Gunicorn

```bash
# Install Gunicorn
pip install gunicorn

# Run with Gunicorn
gunicorn app:app

# Run with specific workers and threads
gunicorn --workers=3 --threads=2 app:app
```

### uWSGI

```bash
# Install uWSGI
pip install uwsgi

# Run with uWSGI
uwsgi --http 127.0.0.1:5000 --module app:app
```

## Project Management

```bash
# Generate requirements file
pip freeze > requirements.txt

# Install from requirements file
pip install -r requirements.txt
```

## Flask CLI Custom Commands

```bash
# List all available Flask commands
flask --help

# Run a custom Flask command
flask custom-command
```

## Environment Variables

```bash
# Install python-dotenv
pip install python-dotenv
```

## Flask Application Factory

```bash
# Run Flask app with application factory
export FLASK_APP=project.app:create_app()
flask run
```

## Flask Blueprints

```bash
# No specific commands, but common pattern for organizing code
# See Flask documentation for implementation details
```

## Flask-Admin

```bash
# Install Flask-Admin
pip install Flask-Admin
```

## Flask-Caching

```bash
# Install Flask-Caching
pip install Flask-Caching
```

## Flask-Cors

```bash
# Install Flask-Cors
pip install Flask-Cors
```

## Flask-Mail

```bash
# Install Flask-Mail
pip install Flask-Mail
```

## Flask-SocketIO

```bash
# Install Flask-SocketIO
pip install Flask-SocketIO
```