# Django Login App

A simple Django web application with user authentication including login, registration, and a protected home page.

## Project Structure

```
djangovs/
├── djangoproject/        # Main project settings and configuration
│   ├── settings.py      # Django settings
│   ├── urls.py          # Main URL routing
│   ├── wsgi.py          # WSGI application
│   └── asgi.py          # ASGI application
├── login/               # Login app
│   ├── views.py         # View functions (login, register, logout, home)
│   ├── urls.py          # App-specific URL routing
│   ├── models.py        # Database models
│   ├── templates/
│   │   └── login/
│   │       ├── base.html        # Base template with styling
│   │       ├── login.html       # Login page
│   │       ├── register.html    # Registration page
│   │       └── home.html        # Home page (logged-in users only)
│   └── static/          # Static files (CSS, JS, images)
├── manage.py            # Django management script
├── db.sqlite3           # SQLite database
├── venv/                # Virtual environment
└── requirements.txt     # Python dependencies
```

## Features

- **User Registration**: Create new user accounts with email validation
- **User Login**: Authenticate users with username and password
- **Protected Pages**: Home page accessible only to logged-in users
- **User Logout**: Securely log out users
- **Admin Interface**: Django admin panel at `/admin/`
- **Responsive UI**: Modern, gradient-based styling

## Setup Instructions

### 1. Prerequisites
- Python 3.7+
- pip (Python package manager)

### 2. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install django
```

### 4. Run Migrations
```bash
python manage.py migrate
```

### 5. Create Superuser (Admin)
```bash
python manage.py createsuperuser
```
Or use the pre-configured admin account (created during setup):
- Username: `admin`
- Password: `admin123`
- Email: `admin@example.com`

### 6. Start Development Server
```bash
python manage.py runserver
```

The application will be available at `http://localhost:8000/`

If port 8000 is already in use, specify a different port:
```bash
python manage.py runserver 8001
```

## Usage

### 1. Registration
- Navigate to `http://localhost:8000/register/`
- Fill in the registration form with username, email, and password
- Click "Register" to create a new account

### 2. Login
- Navigate to `http://localhost:8000/`
- Enter your username and password
- Click "Login" to access the home page

### 3. Home Page
- After successful login, you'll be redirected to the home page
- Click "Logout" to log out of your account

### 4. Admin Interface
- Navigate to `http://localhost:8000/admin/`
- Log in with the superuser credentials (admin / admin123)
- Manage users, groups, and permissions

## URL Routing

- `/` - Login page
- `/register/` - Registration page
- `/logout/` - Logout (redirects to login)
- `/home/` - Home page (protected, requires login)
- `/admin/` - Admin interface

## Database

The application uses SQLite database (`db.sqlite3`) for local development. This file stores:
- User accounts
- User authentication tokens
- Session information
- Admin logs

## Security Notes

**Important**: The included superuser credentials are for development only:
- Never commit real credentials to version control
- Change the superuser password before deploying to production
- Set `DEBUG = False` in production
- Use a secure `SECRET_KEY` in production
- Never share the `SECRET_KEY`

## Customization

### Change Database
To use PostgreSQL or MySQL, update `DATABASES` in `settings.py`:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### Add Custom CSS
Modify `login/templates/login/base.html` to customize styling.

### Extend User Model
Extend Django's User model in `login/models.py` for additional user information.

## Troubleshooting

### Port Already in Use
```bash
python manage.py runserver 8001  # Use a different port
```

### Database Errors
Reset the database:
```bash
rm db.sqlite3
python manage.py migrate
python manage.py shell << EOF
from django.contrib.auth.models import User
User.objects.create_superuser('admin', 'admin@example.com', 'admin123')
EOF
```

### Template Not Found
Ensure `APP_DIRS = True` is set in `settings.py` and templates are in `login/templates/login/`

## Requirements

- Django 6.0+
- Python 3.7+

## License

This project is open source and available under the MIT License.
