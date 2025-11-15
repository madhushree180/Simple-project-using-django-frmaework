# Student API - Django REST Framework

A Django REST API for managing student records with user authentication and admin capabilities.

## Features

- ✅ Student CRUD operations
- ✅ User registration and authentication
- ✅ JWT token-based authentication
- ✅ Admin user management
- ✅ Interactive API documentation (Swagger/Redoc)
- ✅ Comprehensive error handling

## Tech Stack

- **Backend**: Django 5.2.7
- **API**: Django REST Framework 3.16.1
- **Authentication**: djangorestframework-simplejwt 5.5.1
- **Documentation**: drf-spectacular 0.28.0
- **Database**: SQLite (default)

## Project Structure

```
Project/
├── api/                          # API app (views, serializers, URLs)
│   ├── views.py                 # API endpoints
│   ├── serializers.py           # DRF serializers
│   ├── urls.py                  # API routes
│   └── models.py
├── students/                     # Students app (models)
│   ├── models.py                # Student model
│   ├── views.py
│   └── migrations/
├── django_rest_main/            # Project settings
│   ├── settings.py              # Django configuration
│   ├── urls.py                  # Main URL router
│   └── wsgi.py
├── manage.py                    # Django CLI
├── requirements.txt             # Python dependencies
├── .gitignore                  # Git ignore rules
├── .env.example                # Environment variables template
└── README.md                   # This file
```

## Installation

### Prerequisites

- Python 3.8+
- pip

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/django-student-api.git
   cd django-student-api
   ```

2. **Create a virtual environment**
   ```bash
   # Windows
   python -m venv env
   env\Scripts\activate
   
   # macOS/Linux
   python3 -m venv env
   source env/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Create environment file**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and update settings as needed.

5. **Run migrations**
   ```bash
   python manage.py migrate
   ```

6. **Create superuser (admin)**
   ```bash
   python manage.py createsuperuser
   ```

7. **Run development server**
   ```bash
   python manage.py runserver
   ```

   The API will be available at: `http://localhost:8000/api/`

## API Endpoints

### Students
- `GET /api/students/` - Get all students
- `POST /api/students/` - Create a new student
- `GET /api/students/<id>/` - Get student detail
- `PUT /api/students/<id>/` - Update student (coming soon)
- `DELETE /api/students/<id>/` - Delete student (coming soon)

### Authentication
- `POST /api/register/` - Register new user
- `POST /api/token/` - Get JWT token
- `POST /api/token/refresh/` - Refresh JWT token

### Admin
- `GET /api/users/` - Get all users (admin only)
- `POST /api/users/` - Create user (admin only)

### Documentation
- Swagger UI: `http://localhost:8000/api/schema/swagger-ui/`
- Redoc: `http://localhost:8000/api/schema/redoc/`
- OpenAPI Schema: `http://localhost:8000/api/schema/`

## Example Usage

### Register a user
```bash
curl -X POST http://localhost:8000/api/register/ \
  -H "Content-Type: application/json" \
  -d '{"username":"john","email":"john@example.com","password":"secure123"}'
```

### Get all students
```bash
curl http://localhost:8000/api/students/
```

### Create a student
```bash
curl -X POST http://localhost:8000/api/students/ \
  -H "Content-Type: application/json" \
  -d '{"student_id":"S001","name":"John Doe","branch":"CS"}'
```

## Environment Variables

Create a `.env` file based on `.env.example`:

```
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
DATABASE_URL=sqlite:///db.sqlite3
```

## Development

### Create migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### Run tests
```bash
python manage.py test
```

### Collect static files
```bash
python manage.py collectstatic
```

## Production Deployment

Before deploying to production:

1. Set `DEBUG=False` in settings
2. Update `ALLOWED_HOSTS` with your domain
3. Use a strong `SECRET_KEY`
4. Use PostgreSQL instead of SQLite
5. Configure CORS if needed
6. Set up proper logging
7. Use environment variables for sensitive data

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## Support

For support, email your-email@example.com or open an issue on GitHub.

## Roadmap

- [ ] Add PUT/PATCH endpoints for student updates
- [ ] Add DELETE endpoints for student removal
- [ ] Add filtering and search capabilities
- [ ] Add pagination
- [ ] Add rate limiting
- [ ] Add comprehensive test suite
- [ ] Add Docker configuration
- [ ] Add CI/CD pipeline

---

**Made with ❤️ using Django REST Framework**
