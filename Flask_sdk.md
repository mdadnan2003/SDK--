# Flask Backend SDK

> Reusable Flask backend structure for real-world web applications.

---

# 1. Basic Flask App

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def home():

    return "Hello World"


if __name__ == "__main__":
    app.run(debug=True)
```

---

# 2. Recommended Project Structure

```text
project/
│
├── app/
│   ├── __init__.py
│   │
│   ├── config.py
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   └── user.py
│   │
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   ├── users.py
│   │   └── products.py
│   │
│   ├── services/
│   │   └── user_service.py
│   │
│   ├── utils/
│   │   ├── validators.py
│   │   └── helpers.py
│   │
│   └── extensions.py
│
├── migrations/
│
├── tests/
│
├── .env
├── .gitignore
├── requirements.txt
├── run.py
└── README.md
```

---

# 3. Flask App Factory

### app/__init__.py

```python
from flask import Flask

from .config import Config


def create_app():

    app = Flask(__name__)

    app.config.from_object(Config)

    @app.route("/")
    def home():

        return {
            "message": "API is running"
        }

    return app
```

### run.py

```python
from app import create_app


app = create_app()


if __name__ == "__main__":

    app.run(debug=True)
```

---

# 4. Configuration

### app/config.py

```python
import os

from dotenv import load_dotenv


load_dotenv()


class Config:

    SECRET_KEY = os.getenv(
        "SECRET_KEY"
    )

    DATABASE_URL = os.getenv(
        "DATABASE_URL"
    )
```

---

# 5. Environment Variables

### .env

```text
SECRET_KEY=your-secret-key

DATABASE_URL=postgresql://username:password@localhost:5432/mydb
```

### Python

```python
import os

secret_key = os.getenv(
    "SECRET_KEY"
)
```

---

# 6. requirements.txt

```text
Flask
python-dotenv
Flask-SQLAlchemy
Flask-Migrate
Flask-JWT-Extended
Flask-CORS
psycopg
```

---

# 7. Install Flask

```bash
python -m venv venv
```

### Linux / macOS

```bash
source venv/bin/activate
```

### Windows

```bash
venv\Scripts\activate
```

### Install packages

```bash
pip install Flask
```

### requirements

```bash
pip install -r requirements.txt
```

---

# 8. Basic Routes

```python
@app.route("/")
def home():

    return "Home"


@app.route("/about")
def about():

    return "About"


@app.route("/contact")
def contact():

    return "Contact"
```

---

# 9. HTTP Methods

```python
from flask import request


@app.route(
    "/users",
    methods=["GET"]
)
def get_users():

    return {
        "message": "Get users"
    }


@app.route(
    "/users",
    methods=["POST"]
)
def create_user():

    return {
        "message": "Create user"
    }


@app.route(
    "/users/<int:user_id>",
    methods=["PUT"]
)
def update_user(user_id):

    return {
        "message": "Update user",
        "id": user_id
    }


@app.route(
    "/users/<int:user_id>",
    methods=["DELETE"]
)
def delete_user(user_id):

    return {
        "message": "Delete user",
        "id": user_id
    }
```

---

# 10. URL Parameters

```python
@app.route("/users/<int:user_id>")
def get_user(user_id):

    return {
        "user_id": user_id
    }
```

---

# 11. Query Parameters

### URL

```text
/users?page=2&limit=10
```

### Flask

```python
from flask import request


@app.route("/users")
def users():

    page = request.args.get(
        "page",
        default=1,
        type=int
    )

    limit = request.args.get(
        "limit",
        default=10,
        type=int
    )

    return {
        "page": page,
        "limit": limit
    }
```

---

# 12. JSON Request

```python
from flask import request


@app.route(
    "/users",
    methods=["POST"]
)
def create_user():

    data = request.get_json()

    name = data.get("name")

    email = data.get("email")

    return {
        "name": name,
        "email": email
    }
```

---

# 13. JSON Response

```python
@app.route("/api")
def api():

    return {
        "success": True,
        "message": "API working"
    }
```

---

# 14. Response Status Code

```python
from flask import jsonify


@app.route("/users")
def users():

    return jsonify({
        "success": True,
        "data": []
    }), 200
```

### Common Status Codes

```text
200 → OK

201 → Created

204 → No Content

400 → Bad Request

401 → Unauthorized

403 → Forbidden

404 → Not Found

409 → Conflict

422 → Validation Error

500 → Server Error
```

---

# 15. Blueprint

### app/routes/users.py

```python
from flask import Blueprint


users_bp = Blueprint(
    "users",
    __name__,
    url_prefix="/api/users"
)


@users_bp.get("/")
def get_users():

    return {
        "users": []
    }
```

---

# 16. Register Blueprint

### app/__init__.py

```python
from flask import Flask

from .routes.users import users_bp


def create_app():

    app = Flask(__name__)

    app.register_blueprint(
        users_bp
    )

    return app
```

---

# 17. Multiple Blueprints

```python
app.register_blueprint(
    auth_bp,
    url_prefix="/api/auth"
)

app.register_blueprint(
    users_bp,
    url_prefix="/api/users"
)

app.register_blueprint(
    products_bp,
    url_prefix="/api/products"
)
```

---

# 18. Extensions

### app/extensions.py

```python
from flask_sqlalchemy import SQLAlchemy

from flask_migrate import Migrate

from flask_jwt_extended import JWTManager

from flask_cors import CORS


db = SQLAlchemy()

migrate = Migrate()

jwt = JWTManager()

cors = CORS()
```

---

# 19. Initialize Extensions

### app/__init__.py

```python
from flask import Flask

from .extensions import (
    db,
    migrate,
    jwt,
    cors
)


def create_app():

    app = Flask(__name__)

    app.config.from_object(
        "app.config.Config"
    )

    db.init_app(app)

    migrate.init_app(
        app,
        db
    )

    jwt.init_app(app)

    cors.init_app(app)

    return app
```

---

# 20. PostgreSQL Configuration

```python
class Config:

    SQLALCHEMY_DATABASE_URI = (
        "postgresql+psycopg://"
        "username:password@"
        "localhost:5432/mydb"
    )

    SQLALCHEMY_TRACK_MODIFICATIONS = False
```

---

# 21. Database Connection Using .env

### .env

```text
DATABASE_URL=postgresql+psycopg://username:password@localhost:5432/mydb
```

### config.py

```python
import os


class Config:

    SQLALCHEMY_DATABASE_URI = os.getenv(
        "DATABASE_URL"
    )

    SQLALCHEMY_TRACK_MODIFICATIONS = False
```

---

# 22. SQLAlchemy Model

### models/user.py

```python
from app.extensions import db


class User(db.Model):

    __tablename__ = "users"

    id = db.Column(
        db.Integer,
        primary_key=True
    )

    name = db.Column(
        db.String(100),
        nullable=False
    )

    email = db.Column(
        db.String(120),
        unique=True,
        nullable=False
    )
```

---

# 23. Model with Created Time

```python
from datetime import datetime


class User(db.Model):

    id = db.Column(
        db.Integer,
        primary_key=True
    )

    name = db.Column(
        db.String(100),
        nullable=False
    )

    created_at = db.Column(
        db.DateTime,
        default=datetime.utcnow
    )
```

---

# 24. Create Database Record

```python
user = User(
    name="Adnan",
    email="adnan@example.com"
)

db.session.add(user)

db.session.commit()
```

---

# 25. Get All Records

```python
users = User.query.all()

for user in users:

    print(user.name)
```

---

# 26. Get One Record

```python
user = db.session.get(
    User,
    user_id
)
```

---

# 27. Find by Column

```python
user = User.query.filter_by(
    email="adnan@example.com"
).first()
```

---

# 28. Filter

```python
users = User.query.filter(
    User.name == "Adnan"
).all()
```

---

# 29. Update Record

```python
user = db.session.get(
    User,
    user_id
)

user.name = "New Name"

db.session.commit()
```

---

# 30. Delete Record

```python
user = db.session.get(
    User,
    user_id
)

db.session.delete(user)

db.session.commit()
```

---

# 31. Complete CRUD API

```python
from flask import Blueprint, request

from app.extensions import db

from app.models.user import User


users_bp = Blueprint(
    "users",
    __name__
)


@users_bp.get("/users")
def get_users():

    users = User.query.all()

    return {
        "users": [
            {
                "id": user.id,
                "name": user.name,
                "email": user.email
            }

            for user in users
        ]
    }


@users_bp.post("/users")
def create_user():

    data = request.get_json()

    user = User(
        name=data["name"],
        email=data["email"]
    )

    db.session.add(user)

    db.session.commit()

    return {
        "message": "User created",
        "id": user.id
    }, 201


@users_bp.put("/users/<int:user_id>")
def update_user(user_id):

    user = db.session.get(
        User,
        user_id
    )

    if not user:

        return {
            "message": "User not found"
        }, 404

    data = request.get_json()

    user.name = data.get(
        "name",
        user.name
    )

    user.email = data.get(
        "email",
        user.email
    )

    db.session.commit()

    return {
        "message": "User updated"
    }


@users_bp.delete(
    "/users/<int:user_id>"
)
def delete_user(user_id):

    user = db.session.get(
        User,
        user_id
    )

    if not user:

        return {
            "message": "User not found"
        }, 404

    db.session.delete(user)

    db.session.commit()

    return {
        "message": "User deleted"
    }
```

---

# 32. Database Relationships

### One-to-Many

```python
class User(db.Model):

    id = db.Column(
        db.Integer,
        primary_key=True
    )

    posts = db.relationship(
        "Post",
        backref="user",
        lazy=True
    )


class Post(db.Model):

    id = db.Column(
        db.Integer,
        primary_key=True
    )

    user_id = db.Column(
        db.Integer,
        db.ForeignKey("user.id"),
        nullable=False
    )
```

---

# 33. Flask-Migrate

### Initialize

```bash
flask db init
```

### Create Migration

```bash
flask db migrate -m "create users table"
```

### Apply Migration

```bash
flask db upgrade
```

### Rollback

```bash
flask db downgrade
```

---

# 34. Password Hashing

```python
from werkzeug.security import (
    generate_password_hash,
    check_password_hash
)
```

### Hash

```python
password_hash =
    generate_password_hash(
        password
    )
```

### Verify

```python
is_valid =
    check_password_hash(
        password_hash,
        password
    )
```

---

# 35. Register API

```python
@auth_bp.post("/register")
def register():

    data = request.get_json()

    name = data.get("name")

    email = data.get("email")

    password = data.get("password")

    if not name or not email or not password:

        return {
            "message": "All fields are required"
        }, 400

    existing_user =
        User.query.filter_by(
            email=email
        ).first()

    if existing_user:

        return {
            "message": "Email already exists"
        }, 409

    user = User(
        name=name,
        email=email,
        password_hash=
            generate_password_hash(password)
    )

    db.session.add(user)

    db.session.commit()

    return {
        "message": "Registration successful"
    }, 201
```

---

# 36. JWT Authentication

### Configuration

```python
class Config:

    JWT_SECRET_KEY = os.getenv(
        "JWT_SECRET_KEY"
    )
```

### Login

```python
from flask_jwt_extended import (
    create_access_token
)


@auth_bp.post("/login")
def login():

    data = request.get_json()

    user = User.query.filter_by(
        email=data.get("email")
    ).first()

    if not user:

        return {
            "message": "Invalid credentials"
        }, 401

    if not check_password_hash(
        user.password_hash,
        data.get("password")
    ):

        return {
            "message": "Invalid credentials"
        }, 401

    token = create_access_token(
        identity=str(user.id)
    )

    return {
        "access_token": token
    }
```

---

# 37. Protected Route

```python
from flask_jwt_extended import (
    jwt_required,
    get_jwt_identity
)


@app.get("/profile")
@jwt_required()
def profile():

    user_id =
        get_jwt_identity()

    user = db.session.get(
        User,
        user_id
    )

    return {
        "id": user.id,
        "name": user.name,
        "email": user.email
    }
```

---

# 38. Logout

For JWT APIs, logout is commonly handled by token expiry/revocation rather than server-side session destruction.

```python
@app.post("/logout")
@jwt_required()
def logout():

    return {
        "message": "Logged out"
    }
```

---

# 39. CORS

```python
from flask_cors import CORS

CORS(app)
```

### Specific Frontend

```python
CORS(
    app,
    origins=[
        "http://localhost:3000"
    ]
)
```

---

# 40. File Upload

### HTML

```html
<form
    method="POST"
    enctype="multipart/form-data"
>

    <input
        type="file"
        name="file"
    >

    <button type="submit">
        Upload
    </button>

</form>
```

### Flask

```python
from flask import request

import os


UPLOAD_FOLDER = "uploads"

os.makedirs(
    UPLOAD_FOLDER,
    exist_ok=True
)


@app.post("/upload")
def upload():

    file = request.files.get(
        "file"
    )

    if not file:

        return {
            "message": "No file"
        }, 400

    file.save(
        os.path.join(
            UPLOAD_FOLDER,
            file.filename
        )
    )

    return {
        "message": "File uploaded"
    }
```

---

# 41. Secure File Name

```python
from werkzeug.utils import secure_filename


filename =
    secure_filename(
        file.filename
    )

file.save(
    os.path.join(
        UPLOAD_FOLDER,
        filename
    )
)
```

---

# 42. File Type Validation

```python
ALLOWED_EXTENSIONS = {
    "png",
    "jpg",
    "jpeg",
    "pdf"
}


def allowed_file(filename):

    return (
        "." in filename
        and filename.rsplit(
            ".",
            1
        )[1].lower()
        in ALLOWED_EXTENSIONS
    )
```

---

# 43. Error Handler

```python
@app.errorhandler(404)
def not_found(error):

    return {
        "success": False,
        "message": "Resource not found"
    }, 404
```

---

# 44. Global Error Handler

```python
@app.errorhandler(Exception)
def handle_error(error):

    return {
        "success": False,
        "message": "Internal server error"
    }, 500
```

> Production apps should log the actual exception server-side instead of returning sensitive error details to clients.

---

# 45. Custom API Error

```python
def error_response(
    message,
    status_code
):

    return {
        "success": False,
        "message": message
    }, status_code
```

### Usage

```python
return error_response(
    "User not found",
    404
)
```

---

# 46. Standard API Response

```python
def success_response(
    data=None,
    message="Success",
    status_code=200
):

    return {
        "success": True,
        "message": message,
        "data": data
    }, status_code
```

---

# 47. Pagination

```python
@users_bp.get("/users")
def get_users():

    page = request.args.get(
        "page",
        1,
        type=int
    )

    limit = request.args.get(
        "limit",
        10,
        type=int
    )

    pagination =
        db.paginate(
            User.select(),
            page=page,
            per_page=limit
        )

    return {
        "data": [
            {
                "id": user.id,
                "name": user.name
            }

            for user in pagination.items
        ],

        "page": pagination.page,

        "pages": pagination.pages,

        "total": pagination.total
    }
```

---

# 48. Search API

```python
@users_bp.get("/users/search")
def search_users():

    query =
        request.args.get(
            "q",
            ""
        )

    users =
        User.query.filter(
            User.name.ilike(
                f"%{query}%"
            )
        ).all()

    return {
        "users": [
            {
                "id": user.id,
                "name": user.name
            }

            for user in users
        ]
    }
```

---

# 49. Sorting

```python
users = User.query.order_by(
    User.name.asc()
).all()
```

### Descending

```python
users = User.query.order_by(
    User.name.desc()
).all()
```

---

# 50. Service Layer

### services/user_service.py

```python
from app.extensions import db

from app.models.user import User


def create_user(
    name,
    email
):

    user = User(
        name=name,
        email=email
    )

    db.session.add(user)

    db.session.commit()

    return user
```

### Route

```python
@users_bp.post("/")
def create():

    data = request.get_json()

    user = create_user(
        data["name"],
        data["email"]
    )

    return {
        "id": user.id
    }, 201
```

---

# 51. Validation Helper

### utils/validators.py

```python
def validate_required(
    data,
    fields
):

    errors = {}

    for field in fields:

        if not data.get(field):

            errors[field] =
                f"{field} is required"

    return errors
```

### Usage

```python
errors = validate_required(
    data,
    [
        "name",
        "email",
        "password"
    ]
)

if errors:

    return {
        "errors": errors
    }, 400
```

---

# 52. Login Flow

```text
Frontend
   │
   ▼
POST /api/auth/login
   │
   ▼
Flask
   │
   ▼
Validate Email/Password
   │
   ▼
PostgreSQL
   │
   ▼
Check Password Hash
   │
   ▼
Create JWT
   │
   ▼
Return Token
   │
   ▼
Frontend
```

---

# 53. CRUD Flow

```text
Frontend
   │
   ▼
HTTP Request
   │
   ▼
Flask Route
   │
   ▼
Validation
   │
   ▼
Service Layer
   │
   ▼
SQLAlchemy
   │
   ▼
PostgreSQL
   │
   ▼
Response
   │
   ▼
Frontend
```

---

# 54. Flask + HTML + CSS + JS

```text
                WEBSITE
                   │
       ┌───────────┼───────────┐
       │           │           │
      HTML        CSS          JS
       │           │           │
       └───────────┼───────────┘
                   │
                Browser
                   │
                fetch()
                   │
                   ▼
                Flask
                   │
              Route / API
                   │
                   ▼
               Service
                   │
                   ▼
              SQLAlchemy
                   │
                   ▼
              PostgreSQL
```

---

# 55. Frontend Fetch Example

### JavaScript

```javascript
async function getUsers() {

    const response =
        await fetch(
            "http://localhost:5000/api/users"
        );

    const data =
        await response.json();

    console.log(data);

}
```

---

# 56. Flask API Response

```python
@app.get("/api/users")
def users():

    return {
        "success": True,

        "data": [
            {
                "id": 1,
                "name": "Adnan"
            },
            {
                "id": 2,
                "name": "Rahul"
            }
        ]
    }
```

---

# 57. Environment-Based Config

```python
import os


class Config:

    DEBUG = False

    SECRET_KEY = os.getenv(
        "SECRET_KEY"
    )

    SQLALCHEMY_DATABASE_URI =
        os.getenv(
            "DATABASE_URL"
        )


class DevelopmentConfig(Config):

    DEBUG = True


class ProductionConfig(Config):

    DEBUG = False
```

---

# 58. Logging

```python
import logging


logging.basicConfig(
    level=logging.INFO
)


app.logger.info(
    "Application started"
)

app.logger.error(
    "Something went wrong"
)
```

---

# 59. Health Check

```python
@app.get("/health")
def health():

    return {
        "status": "healthy"
    }
```

---

# 60. API Versioning

```text
/api/v1/users
/api/v1/products
/api/v1/orders
```

### Flask

```python
users_bp = Blueprint(
    "users",
    __name__,
    url_prefix="/api/v1/users"
)
```

---

# 61. Testing

### Install

```bash
pip install pytest
```

### Test

```python
def test_home(client):

    response =
        client.get("/")

    assert response.status_code == 200
```

---

# 62. Flask Test Client

```python
response = client.post(
    "/api/users",
    json={
        "name": "Adnan",
        "email": "adnan@example.com"
    }
)

assert response.status_code == 201
```

---

# 63. Production Run

Development:

```bash
flask run --debug
```

Production deployment should use a production WSGI server rather than Flask's development server.

Example:

```bash
gunicorn "app:create_app()"
```

---

# 64. Security Checklist

```text
□ SECRET_KEY environment variable me rakho

□ Database password code me hardcode mat karo

□ Password ko hash karke store karo

□ Input validation karo

□ SQL injection se bachne ke liye
  parameterized queries / ORM use karo

□ File upload validate karo

□ secure_filename() use karo

□ CORS ko specific origins tak restrict karo

□ Production me DEBUG=False rakho

□ Sensitive errors client ko mat bhejo

□ HTTPS use karo

□ Authentication properly implement karo

□ Authorization / role checks lagao

□ JWT/session expiry ka dhyan rakho

□ Dependencies updated rakho
```

---

# 65. Final Flask SDK Checklist

```text
FLASK CORE
□ Flask App
□ Routes
□ HTTP Methods
□ URL Parameters
□ Query Parameters
□ JSON Request
□ JSON Response
□ Status Codes
□ Error Handlers

ARCHITECTURE
□ App Factory
□ Blueprints
□ Config
□ Environment Variables
□ Services
□ Utils
□ Extensions

DATABASE
□ PostgreSQL
□ SQLAlchemy
□ Models
□ CRUD
□ Relationships
□ Filtering
□ Searching
□ Sorting
□ Pagination
□ Flask-Migrate

AUTH
□ Register
□ Login
□ Password Hashing
□ JWT
□ Protected Routes
□ Logout
□ Authorization

API
□ REST API
□ GET
□ POST
□ PUT
□ PATCH
□ DELETE
□ API Versioning
□ Standard Responses
□ Error Responses

FRONTEND CONNECTION
□ CORS
□ fetch()
□ JSON
□ Form Submission
□ File Upload

FILES
□ File Upload
□ File Validation
□ secure_filename()
□ Image Upload

PRODUCTION
□ Environment Variables
□ Logging
□ Error Handling
□ HTTPS
□ WSGI Server
□ DEBUG=False

TESTING
□ pytest
□ Test Client
□ API Tests
```

---

# 66. Complete Backend Architecture

```text
                        CLIENT
                          │
                          ▼
                   HTML + CSS + JS
                          │
                          │ HTTP / JSON
                          ▼
                    ┌───────────┐
                    │   Flask   │
                    │    API    │
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │  Routes   │
                    │ Blueprint │
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │ Validation│
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │  Service  │
                    │   Layer   │
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │ SQLAlchemy │
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │ PostgreSQL │
                    └───────────┘
```

---

# 67. Full-Stack Project Structure

```text
my-project/
│
├── backend/
│   │
│   ├── app/
│   │   ├── __init__.py
│   │   ├── config.py
│   │   ├── extensions.py
│   │   │
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   └── product.py
│   │   │
│   │   ├── routes/
│   │   │   ├── auth.py
│   │   │   ├── users.py
│   │   │   └── products.py
│   │   │
│   │   ├── services/
│   │   │   ├── auth_service.py
│   │   │   └── user_service.py
│   │   │
│   │   └── utils/
│   │       ├── validators.py
│   │       └── helpers.py
│   │
│   ├── migrations/
│   ├── tests/
│   ├── .env
│   ├── requirements.txt
│   └── run.py
│
└── frontend/
    │
    ├── index.html
    ├── pages/
    ├── css/
    │   ├── style.css
    │   └── components.css
    │
    └── js/
        ├── main.js
        ├── api.js
        ├── ui.js
        └── utils.js
```

---

# 68. Development Order

```text
1. Project Setup
       ↓
2. Flask App
       ↓
3. Configuration
       ↓
4. PostgreSQL
       ↓
5. SQLAlchemy Models
       ↓
6. Migrations
       ↓
7. Routes / Blueprints
       ↓
8. CRUD APIs
       ↓
9. Validation
       ↓
10. Authentication
       ↓
11. CORS
       ↓
12. Frontend fetch()
       ↓
13. Testing
       ↓
14. Deployment
```

---

# 69. Flask Mental Model

```text
Flask
 │
 ├── Route
 │      ↓
 │   Request
 │      ↓
 │   Validation
 │      ↓
 │   Business Logic
 │      ↓
 │   Database
 │      ↓
 │   Response
 │
 ├── Model
 │      ↓
 │   Database Structure
 │
 ├── Blueprint
 │      ↓
 │   Routes ko organize karta hai
 │
 ├── Service
 │      ↓
 │   Business Logic
 │
 └── Config
        ↓
     Settings
```

---

# 70. Golden Rule

```text
Route
  ↓
Validation
  ↓
Service
  ↓
Database
  ↓
Response
```

> Large Flask applications me route ke andar poora business logic bharne ke bajay routes, services, models aur utilities ko separate rakhna maintainability ke liye useful hota hai.
