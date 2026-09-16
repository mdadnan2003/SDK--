# FastAPI Backend SDK

> Reusable FastAPI backend components for real-world applications.

---

# 1. Basic FastAPI App

```python
from fastapi import FastAPI


app = FastAPI()


@app.get("/")
def home():

    return {
        "message": "Hello World"
    }
```

### Run

```bash
uvicorn main:app --reload
```

---

# 2. Recommended Project Structure

```text
project/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── config.py
│   ├── database.py
│   ├── dependencies.py
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   └── user.py
│   │
│   ├── schemas/
│   │   ├── __init__.py
│   │   └── user.py
│   │
│   ├── routers/
│   │   ├── __init__.py
│   │   ├── auth.py
│   │   ├── users.py
│   │   └── products.py
│   │
│   ├── services/
│   │   ├── auth_service.py
│   │   └── user_service.py
│   │
│   └── utils/
│       ├── security.py
│       └── validators.py
│
├── tests/
│
├── .env
├── .gitignore
├── requirements.txt
└── README.md
```

---

# 3. Install FastAPI

```bash
pip install fastapi uvicorn
```

### Common Packages

```bash
pip install sqlalchemy
pip install psycopg
pip install pydantic-settings
pip install python-multipart
pip install pyjwt
pip install pwdlib
pip install pytest httpx
```

---

# 4. requirements.txt

```text
fastapi
uvicorn[standard]
sqlalchemy
psycopg
pydantic-settings
python-multipart
pyjwt
pwdlib
pytest
httpx
```

---

# 5. Basic Route

```python
from fastapi import FastAPI


app = FastAPI()


@app.get("/")
def home():

    return {
        "message": "API is running"
    }
```

---

# 6. HTTP Methods

```python
@app.get("/users")
def get_users():

    return {
        "message": "Get users"
    }


@app.post("/users")
def create_user():

    return {
        "message": "Create user"
    }


@app.put("/users/{user_id}")
def update_user(user_id: int):

    return {
        "message": "Update user",
        "id": user_id
    }


@app.patch("/users/{user_id}")
def patch_user(user_id: int):

    return {
        "message": "Patch user",
        "id": user_id
    }


@app.delete("/users/{user_id}")
def delete_user(user_id: int):

    return {
        "message": "Delete user",
        "id": user_id
    }
```

---

# 7. Path Parameters

```python
@app.get("/users/{user_id}")
def get_user(user_id: int):

    return {
        "user_id": user_id
    }
```

FastAPI automatically validates:

```text
/users/10
```

as:

```python
user_id = 10
```

---

# 8. Query Parameters

### URL

```text
/users?page=1&limit=10
```

### FastAPI

```python
from fastapi import FastAPI


app = FastAPI()


@app.get("/users")
def get_users(
    page: int = 1,
    limit: int = 10
):

    return {
        "page": page,
        "limit": limit
    }
```

---

# 9. Optional Query Parameter

```python
from typing import Optional


@app.get("/users")
def get_users(
    search: Optional[str] = None
):

    return {
        "search": search
    }
```

Modern Python:

```python
def get_users(
    search: str | None = None
):

    return {
        "search": search
    }
```

---

# 10. Request Body

```python
from fastapi import FastAPI


app = FastAPI()


@app.post("/users")
def create_user(data: dict):

    return data
```

---

# 11. Pydantic Schema

```python
from pydantic import BaseModel


class UserCreate(BaseModel):

    name: str

    email: str

    age: int
```

### Route

```python
@app.post("/users")
def create_user(
    user: UserCreate
):

    return user
```

---

# 12. Pydantic Validation

```python
from pydantic import BaseModel


class UserCreate(BaseModel):

    name: str

    email: str

    age: int
```

Request:

```json
{
    "name": "Adnan",
    "email": "adnan@example.com",
    "age": 22
}
```

Invalid request:

```json
{
    "name": "Adnan",
    "email": "wrong",
    "age": "abc"
}
```

FastAPI automatically returns validation errors.

---

# 13. Field Validation

```python
from pydantic import BaseModel, Field


class UserCreate(BaseModel):

    name: str = Field(
        min_length=2,
        max_length=100
    )

    age: int = Field(
        ge=13,
        le=100
    )
```

---

# 14. Email Validation

```bash
pip install email-validator
```

```python
from pydantic import BaseModel, EmailStr


class UserCreate(BaseModel):

    name: str

    email: EmailStr

    password: str
```

---

# 15. Response Model

```python
from pydantic import BaseModel


class UserResponse(BaseModel):

    id: int

    name: str

    email: str


@app.get(
    "/users/{user_id}",
    response_model=UserResponse
)
def get_user(user_id: int):

    return {
        "id": user_id,
        "name": "Adnan",
        "email": "adnan@example.com"
    }
```

---

# 16. Create / Read Schemas

```python
from pydantic import BaseModel, EmailStr


class UserCreate(BaseModel):

    name: str

    email: EmailStr

    password: str


class UserResponse(BaseModel):

    id: int

    name: str

    email: EmailStr
```

Never return the password in the response schema.

---

# 17. Status Codes

```python
from fastapi import status


@app.post(
    "/users",
    status_code=status.HTTP_201_CREATED
)
def create_user():

    return {
        "message": "User created"
    }
```

Common:

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

# 18. HTTPException

```python
from fastapi import HTTPException


@app.get("/users/{user_id}")
def get_user(user_id: int):

    if user_id != 1:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    return {
        "id": 1,
        "name": "Adnan"
    }
```

---

# 19. APIRouter

### routers/users.py

```python
from fastapi import APIRouter


router = APIRouter(
    prefix="/users",
    tags=["Users"]
)


@router.get("/")
def get_users():

    return {
        "users": []
    }
```

---

# 20. Register Router

### main.py

```python
from fastapi import FastAPI

from app.routers.users import router as users_router


app = FastAPI()


app.include_router(
    users_router,
    prefix="/api/v1"
)
```

Endpoint:

```text
GET /api/v1/users/
```

---

# 21. Multiple Routers

```python
app.include_router(
    auth_router,
    prefix="/api/v1/auth",
    tags=["Auth"]
)

app.include_router(
    users_router,
    prefix="/api/v1/users",
    tags=["Users"]
)

app.include_router(
    products_router,
    prefix="/api/v1/products",
    tags=["Products"]
)
```

---

# 22. API Versioning

```text
/api/v1/users
/api/v1/products
/api/v1/orders
```

Example:

```python
app.include_router(
    users_router,
    prefix="/api/v1/users"
)
```

---

# 23. Configuration with .env

### .env

```text
DATABASE_URL=postgresql+psycopg://username:password@localhost:5432/mydb

SECRET_KEY=change-this-secret
```

### config.py

```python
from pydantic_settings import BaseSettings


class Settings(BaseSettings):

    database_url: str

    secret_key: str

    class Config:

        env_file = ".env"


settings = Settings()
```

---

# 24. Better Settings Configuration

```python
from pydantic_settings import (
    BaseSettings,
    SettingsConfigDict
)


class Settings(BaseSettings):

    database_url: str

    secret_key: str

    model_config = SettingsConfigDict(
        env_file=".env"
    )


settings = Settings()
```

---

# 25. PostgreSQL Connection

```python
from sqlalchemy import create_engine

from app.config import settings


engine = create_engine(
    settings.database_url
)
```

---

# 26. SQLAlchemy Base

```python
from sqlalchemy.orm import (
    DeclarativeBase
)


class Base(DeclarativeBase):

    pass
```

---

# 27. Database Session

```python
from sqlalchemy.orm import (
    sessionmaker
)


SessionLocal = sessionmaker(
    bind=engine,
    autoflush=False,
    autocommit=False
)
```

---

# 28. Database Dependency

```python
def get_db():

    db = SessionLocal()

    try:

        yield db

    finally:

        db.close()
```

---

# 29. Using Database Dependency

```python
from fastapi import Depends

from sqlalchemy.orm import Session


@app.get("/users")
def get_users(
    db: Session = Depends(get_db)
):

    users = db.query(User).all()

    return users
```

---

# 30. SQLAlchemy Model

```python
from sqlalchemy import (
    String,
    Integer
)

from sqlalchemy.orm import (
    Mapped,
    mapped_column
)


class User(Base):

    __tablename__ = "users"

    id: Mapped[int] = mapped_column(
        Integer,
        primary_key=True
    )

    name: Mapped[str] = mapped_column(
        String(100)
    )

    email: Mapped[str] = mapped_column(
        String(120),
        unique=True
    )
```

---

# 31. Password Model

```python
class User(Base):

    __tablename__ = "users"

    id: Mapped[int] = mapped_column(
        primary_key=True
    )

    name: Mapped[str]

    email: Mapped[str] = mapped_column(
        unique=True,
        index=True
    )

    password_hash: Mapped[str]
```

---

# 32. Create Database Tables

```python
from app.database import engine

from app.models.user import User


Base.metadata.create_all(
    bind=engine
)
```

For production projects, prefer migrations instead of relying on `create_all()` for schema evolution.

---

# 33. Alembic

Install:

```bash
pip install alembic
```

Initialize:

```bash
alembic init alembic
```

Create migration:

```bash
alembic revision --autogenerate -m "create users table"
```

Apply:

```bash
alembic upgrade head
```

Rollback:

```bash
alembic downgrade -1
```

---

# 34. Create Record

```python
user = User(
    name="Adnan",
    email="adnan@example.com",
    password_hash="hashed-password"
)

db.add(user)

db.commit()

db.refresh(user)
```

---

# 35. Get All Records

```python
from sqlalchemy import select


stmt = select(User)

users = db.scalars(
    stmt
).all()
```

---

# 36. Get One Record

```python
user = db.get(
    User,
    user_id
)
```

---

# 37. Find by Email

```python
stmt = select(User).where(
    User.email == email
)

user = db.scalar(stmt)
```

---

# 38. Update Record

```python
user = db.get(
    User,
    user_id
)

if not user:

    raise HTTPException(
        status_code=404,
        detail="User not found"
    )

user.name = "New Name"

db.commit()

db.refresh(user)
```

---

# 39. Delete Record

```python
user = db.get(
    User,
    user_id
)

if not user:

    raise HTTPException(
        status_code=404,
        detail="User not found"
    )

db.delete(user)

db.commit()
```

---

# 40. Complete CRUD API

```python
from fastapi import (
    APIRouter,
    Depends,
    HTTPException
)

from sqlalchemy import select

from sqlalchemy.orm import Session


router = APIRouter()


@router.get("/users")
def get_users(
    db: Session = Depends(get_db)
):

    users = db.scalars(
        select(User)
    ).all()

    return users


@router.post("/users")
def create_user(
    user_data: UserCreate,
    db: Session = Depends(get_db)
):

    existing_user = db.scalar(
        select(User).where(
            User.email == user_data.email
        )
    )

    if existing_user:

        raise HTTPException(
            status_code=409,
            detail="Email already exists"
        )

    user = User(
        name=user_data.name,
        email=user_data.email,
        password_hash="hashed-password"
    )

    db.add(user)

    db.commit()

    db.refresh(user)

    return user


@router.get("/users/{user_id}")
def get_user(
    user_id: int,
    db: Session = Depends(get_db)
):

    user = db.get(
        User,
        user_id
    )

    if not user:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    return user


@router.delete("/users/{user_id}")
def delete_user(
    user_id: int,
    db: Session = Depends(get_db)
):

    user = db.get(
        User,
        user_id
    )

    if not user:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    db.delete(user)

    db.commit()

    return {
        "message": "User deleted"
    }
```

---

# 41. Password Hashing

```bash
pip install pwdlib
```

```python
from pwdlib import PasswordHash


password_hash = PasswordHash.recommended()
```

### Hash

```python
hashed_password =
    password_hash.hash(
        password
    )
```

### Verify

```python
valid =
    password_hash.verify(
        password,
        hashed_password
    )
```

---

# 42. Register API

```python
@router.post(
    "/register",
    status_code=201
)
def register(
    data: UserCreate,
    db: Session = Depends(get_db)
):

    existing_user = db.scalar(
        select(User).where(
            User.email == data.email
        )
    )

    if existing_user:

        raise HTTPException(
            status_code=409,
            detail="Email already exists"
        )

    user = User(

        name=data.name,

        email=data.email,

        password_hash=
            password_hash.hash(
                data.password
            )

    )

    db.add(user)

    db.commit()

    db.refresh(user)

    return {
        "message":
            "Registration successful",
        "id":
            user.id
    }
```

---

# 43. JWT Authentication

Install:

```bash
pip install pyjwt
```

### Create Token

```python
import jwt

from datetime import (
    datetime,
    timedelta
)


def create_access_token(
    user_id: int,
    secret_key: str
):

    payload = {

        "sub": str(user_id),

        "exp":
            datetime.utcnow()
            + timedelta(
                minutes=30
            )

    }

    return jwt.encode(
        payload,
        secret_key,
        algorithm="HS256"
    )
```

---

# 44. Login API

```python
@router.post("/login")
def login(
    data: LoginRequest,
    db: Session = Depends(get_db)
):

    user = db.scalar(
        select(User).where(
            User.email == data.email
        )
    )

    if not user:

        raise HTTPException(
            status_code=401,
            detail="Invalid credentials"
        )

    if not password_hash.verify(
        data.password,
        user.password_hash
    ):

        raise HTTPException(
            status_code=401,
            detail="Invalid credentials"
        )

    token = create_access_token(
        user.id,
        settings.secret_key
    )

    return {
        "access_token": token,
        "token_type": "bearer"
    }
```

---

# 45. OAuth2 Bearer Token

```python
from fastapi.security import (
    OAuth2PasswordBearer
)


oauth2_scheme =
    OAuth2PasswordBearer(
        tokenUrl="/api/v1/auth/login"
    )
```

---

# 46. Get Current User

```python
from fastapi import Depends


def get_current_user(
    token: str = Depends(
        oauth2_scheme
    )
):

    payload =
        jwt.decode(
            token,
            settings.secret_key,
            algorithms=["HS256"]
        )

    user_id =
        payload.get("sub")

    if not user_id:

        raise HTTPException(
            status_code=401,
            detail="Invalid token"
        )

    return int(user_id)
```

---

# 47. Protected Route

```python
@router.get("/profile")
def profile(
    user_id: int = Depends(
        get_current_user
    )
):

    return {
        "user_id": user_id
    }
```

---

# 48. Authentication Flow

```text
Register
   │
   ▼
Hash Password
   │
   ▼
PostgreSQL
   │
   ▼
Login
   │
   ▼
Verify Password
   │
   ▼
Create JWT
   │
   ▼
Frontend
   │
   ▼
Authorization: Bearer TOKEN
   │
   ▼
Protected API
```

---

# 49. CORS

```python
from fastapi.middleware.cors import (
    CORSMiddleware
)


app.add_middleware(
    CORSMiddleware,

    allow_origins=[
        "http://localhost:3000"
    ],

    allow_credentials=True,

    allow_methods=["*"],

    allow_headers=["*"]
)
```

Avoid using `allow_origins=["*"]` with credentials in production.

---

# 50. Middleware

```python
from fastapi import Request


@app.middleware("http")
async def log_requests(
    request: Request,
    call_next
):

    response =
        await call_next(request)

    return response
```

---

# 51. Custom Header

```python
from fastapi import Header


@app.get("/profile")
def profile(
    user_agent: str | None =
        Header(default=None)
):

    return {
        "user_agent": user_agent
    }
```

---

# 52. File Upload

```python
from fastapi import (
    UploadFile,
    File
)


@app.post("/upload")
async def upload_file(
    file: UploadFile = File(...)
):

    contents =
        await file.read()

    return {
        "filename": file.filename,

        "content_type":
            file.content_type,

        "size":
            len(contents)
    }
```

---

# 53. Save Uploaded File

```python
from pathlib import Path


UPLOAD_DIR =
    Path("uploads")

UPLOAD_DIR.mkdir(
    exist_ok=True
)


@app.post("/upload")
async def upload_file(
    file: UploadFile = File(...)
):

    file_path =
        UPLOAD_DIR / file.filename

    with open(
        file_path,
        "wb"
    ) as buffer:

        buffer.write(
            await file.read()
        )

    return {
        "message": "File uploaded"
    }
```

---

# 54. Secure File Upload

```python
from pathlib import Path
from uuid import uuid4


ALLOWED_TYPES = {
    "image/png",
    "image/jpeg",
    "application/pdf"
}


@app.post("/upload")
async def upload_file(
    file: UploadFile = File(...)
):

    if file.content_type not in ALLOWED_TYPES:

        raise HTTPException(
            status_code=400,
            detail="Invalid file type"
        )

    extension =
        Path(
            file.filename
        ).suffix.lower()

    filename =
        f"{uuid4()}{extension}"

    file_path =
        UPLOAD_DIR / filename

    with open(
        file_path,
        "wb"
    ) as buffer:

        while chunk :=
            await file.read(1024 * 1024):

            buffer.write(chunk)

    return {
        "filename": filename
    }
```

---

# 55. Multiple File Upload

```python
from typing import Annotated


@app.post("/uploads")
async def upload_files(
    files: Annotated[
        list[UploadFile],
        File(...)
    ]
):

    return {
        "files": [
            file.filename
            for file in files
        ]
    }
```

---

# 56. Form Data

Install:

```bash
pip install python-multipart
```

```python
from fastapi import Form


@app.post("/login")
def login(
    username: str = Form(...),
    password: str = Form(...)
):

    return {
        "username": username
    }
```

---

# 57. Background Tasks

```python
from fastapi import (
    BackgroundTasks
)


def send_email(email: str):

    print(
        f"Sending email to {email}"
    )


@app.post("/register")
def register(
    email: str,
    background_tasks:
        BackgroundTasks
):

    background_tasks.add_task(
        send_email,
        email
    )

    return {
        "message":
            "Registration successful"
    }
```

---

# 58. Pagination

```python
from sqlalchemy import (
    select
)


@router.get("/users")
def get_users(
    page: int = 1,
    limit: int = 10,
    db: Session =
        Depends(get_db)
):

    offset =
        (page - 1) * limit

    users =
        db.scalars(
            select(User)
            .offset(offset)
            .limit(limit)
        ).all()

    return {
        "page": page,

        "limit": limit,

        "data": users
    }
```

---

# 59. Search

```python
@router.get("/users")
def search_users(
    search: str | None = None,
    db: Session =
        Depends(get_db)
):

    stmt = select(User)

    if search:

        stmt = stmt.where(
            User.name.ilike(
                f"%{search}%"
            )
        )

    users =
        db.scalars(stmt).all()

    return users
```

---

# 60. Sorting

```python
from sqlalchemy import select


stmt = select(User).order_by(
    User.name.asc()
)

users =
    db.scalars(stmt).all()
```

Descending:

```python
stmt = select(User).order_by(
    User.name.desc()
)
```

---

# 61. Dependency Injection

```python
from fastapi import Depends


def get_message():

    return "Hello"


@app.get("/")
def home(
    message: str =
        Depends(get_message)
):

    return {
        "message": message
    }
```

---

# 62. Common Database Dependency

```python
def get_db():

    db = SessionLocal()

    try:

        yield db

    finally:

        db.close()
```

Use:

```python
db: Session =
    Depends(get_db)
```

---

# 63. Role-Based Authorization

```python
def require_admin(
    user_id: int =
        Depends(get_current_user),
    db: Session =
        Depends(get_db)
):

    user = db.get(
        User,
        user_id
    )

    if not user:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    if user.role != "admin":

        raise HTTPException(
            status_code=403,
            detail="Admin access required"
        )

    return user
```

### Protected Admin Route

```python
@router.delete("/users/{user_id}")
def delete_user(
    user_id: int,
    admin = Depends(
        require_admin
    ),
    db: Session =
        Depends(get_db)
):

    user = db.get(
        User,
        user_id
    )

    if not user:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    db.delete(user)

    db.commit()

    return {
        "message": "User deleted"
    }
```

---

# 64. Response Wrapper

```python
def success_response(
    data=None,
    message="Success"
):

    return {
        "success": True,
        "message": message,
        "data": data
    }
```

Usage:

```python
return success_response(
    data=users,
    message="Users fetched"
)
```

---

# 65. Error Response

```python
def error_response(
    message: str,
    status_code: int
):

    raise HTTPException(
        status_code=status_code,
        detail=message
    )
```

Usage:

```python
error_response(
    "User not found",
    404
)
```

---

# 66. Global Exception Handler

```python
from fastapi import (
    Request
)

from fastapi.responses import (
    JSONResponse
)


@app.exception_handler(
    Exception
)
async def global_exception_handler(
    request: Request,
    exc: Exception
):

    return JSONResponse(
        status_code=500,

        content={
            "success": False,
            "message":
                "Internal server error"
        }
    )
```

Do not expose sensitive exception details to clients.

---

# 67. Logging

```python
import logging


logger =
    logging.getLogger(__name__)


logger.info(
    "Application started"
)

logger.error(
    "Something went wrong"
)
```

---

# 68. Health Check

```python
@app.get("/health")
def health():

    return {
        "status": "healthy"
    }
```

---

# 69. Database Health Check

```python
from sqlalchemy import text


@app.get("/health/db")
def database_health(
    db: Session =
        Depends(get_db)
):

    try:

        db.execute(
            text("SELECT 1")
        )

        return {
            "database": "healthy"
        }

    except Exception:

        raise HTTPException(
            status_code=503,
            detail="Database unavailable"
        )
```

---

# 70. Async Route

```python
@app.get("/async")
async def async_route():

    return {
        "message":
            "Async endpoint"
    }
```

---

# 71. Async HTTP Request

```python
import httpx


@app.get("/external")
async def external_api():

    async with httpx.AsyncClient() as client:

        response =
            await client.get(
                "https://example.com"
            )

    return {
        "status":
            response.status_code
    }
```

---

# 72. Async Database

For applications that use async database access, SQLAlchemy provides an async API.

```python
from sqlalchemy.ext.asyncio import (
    create_async_engine,
    AsyncSession
)


engine =
    create_async_engine(
        settings.database_url
    )
```

Use an async-compatible PostgreSQL driver/configuration when choosing the async database URL.

---

# 73. Async SQLAlchemy Query

```python
from sqlalchemy import select


async def get_users(
    session: AsyncSession
):

    result =
        await session.execute(
            select(User)
        )

    return result.scalars().all()
```

---

# 74. WebSocket

```python
from fastapi import (
    WebSocket
)


@app.websocket("/ws")
async def websocket_endpoint(
    websocket: WebSocket
):

    await websocket.accept()

    while True:

        data =
            await websocket.receive_text()

        await websocket.send_text(
            f"Message: {data}"
        )
```

---

# 75. WebSocket Flow

```text
Client
  │
  │ WebSocket Connection
  ▼
FastAPI
  │
  │ accept()
  ▼
Connection Open
  │
  ├── receive_text()
  │
  ├── process
  │
  └── send_text()
  │
  ▼
Client
```

---

# 76. API Documentation

FastAPI automatically provides:

```text
/docs
```

Swagger UI.

And:

```text
/redoc
```

ReDoc.

Open:

```text
http://localhost:8000/docs
```

---

# 77. Tags

```python
router = APIRouter(
    prefix="/users",
    tags=["Users"]
)
```

---

# 78. Route Documentation

```python
@router.get(
    "/",
    summary="Get all users",
    description="Returns all registered users."
)
def get_users():

    return []
```

---

# 79. Custom OpenAPI Metadata

```python
app = FastAPI(

    title="My API",

    description=
        "Backend API for my application",

    version="1.0.0"
)
```

---

# 80. Request Example Schema

```python
from pydantic import BaseModel


class LoginRequest(BaseModel):

    email: str

    password: str
```

---

# 81. Environment-Based Configuration

```python
class Settings(BaseSettings):

    environment: str = "development"

    debug: bool = False

    database_url: str

    secret_key: str

    model_config =
        SettingsConfigDict(
            env_file=".env"
        )
```

---

# 82. Testing

Install:

```bash
pip install pytest httpx
```

### Test

```python
from fastapi.testclient import (
    TestClient
)

from app.main import app


client =
    TestClient(app)


def test_home():

    response =
        client.get("/")

    assert response.status_code == 200
```

---

# 83. Test POST API

```python
def test_create_user():

    response =
        client.post(
            "/api/v1/users",
            json={
                "name": "Adnan",
                "email":
                    "adnan@example.com",
                "password":
                    "password123"
            }
        )

    assert response.status_code == 201
```

---

# 84. Test Authentication

```python
def test_login():

    response =
        client.post(
            "/api/v1/auth/login",
            json={
                "email":
                    "adnan@example.com",
                "password":
                    "password123"
            }
        )

    assert response.status_code == 200

    data = response.json()

    assert "access_token" in data
```

---

# 85. Protected API Test

```python
def test_profile():

    login =
        client.post(
            "/api/v1/auth/login",
            json={
                "email":
                    "adnan@example.com",
                "password":
                    "password123"
            }
        )

    token =
        login.json()["access_token"]

    response =
        client.get(
            "/api/v1/auth/profile",
            headers={
                "Authorization":
                    f"Bearer {token}"
            }
        )

    assert response.status_code == 200
```

---

# 86. Static Files

```python
from fastapi.staticfiles import (
    StaticFiles
)


app.mount(
    "/static",
    StaticFiles(
        directory="static"
    ),
    name="static"
)
```

---

# 87. Serve HTML

```python
from fastapi.responses import (
    HTMLResponse
)


@app.get(
    "/",
    response_class=HTMLResponse
)
def home():

    return """
    <h1>
        Hello World
    </h1>
    """
```

---

# 88. JSON Response

```python
from fastapi.responses import (
    JSONResponse
)


@app.get("/data")
def data():

    return JSONResponse(
        content={
            "success": True
        }
    )
```

---

# 89. Redirect

```python
from fastapi.responses import (
    RedirectResponse
)


@app.get("/old")
def old():

    return RedirectResponse(
        "/new"
    )
```

---

# 90. Cookie

```python
from fastapi import Response


@app.get("/set-cookie")
def set_cookie(
    response: Response
):

    response.set_cookie(
        key="session",
        value="abc123",
        httponly=True
    )

    return {
        "message": "Cookie set"
    }
```

---

# 91. Read Cookie

```python
from fastapi import Cookie


@app.get("/cookie")
def get_cookie(
    session: str | None =
        Cookie(default=None)
):

    return {
        "session": session
    }
```

---

# 92. Header Authentication Concept

```text
Authorization:
Bearer <JWT>
```

FastAPI:

```python
token: str =
    Depends(oauth2_scheme)
```

---

# 93. Database Relationships

```python
from sqlalchemy.orm import (
    relationship
)


class User(Base):

    __tablename__ = "users"

    id: Mapped[int] =
        mapped_column(
            primary_key=True
        )

    posts = relationship(
        "Post",
        back_populates="user"
    )


class Post(Base):

    __tablename__ = "posts"

    id: Mapped[int] =
        mapped_column(
            primary_key=True
        )

    user_id: Mapped[int] =
        mapped_column(
            ForeignKey("users.id")
        )

    user = relationship(
        "User",
        back_populates="posts"
    )
```

---

# 94. Transaction Handling

```python
try:

    user = User(
        name="Adnan"
    )

    db.add(user)

    db.commit()

except Exception:

    db.rollback()

    raise
```

---

# 95. Service Layer

### services/user_service.py

```python
from sqlalchemy import select


def get_user(
    db,
    user_id
):

    return db.scalar(
        select(User).where(
            User.id == user_id
        )
    )
```

### Router

```python
@router.get(
    "/users/{user_id}"
)
def get_user(
    user_id: int,
    db: Session =
        Depends(get_db)
):

    user =
        user_service.get_user(
            db,
            user_id
        )

    if not user:

        raise HTTPException(
            status_code=404,
            detail="User not found"
        )

    return user
```

---

# 96. Repository Layer

```python
class UserRepository:

    def get_by_id(
        self,
        db,
        user_id
    ):

        return db.get(
            User,
            user_id
        )


    def get_by_email(
        self,
        db,
        email
    ):

        return db.scalar(
            select(User).where(
                User.email == email
            )
        )
```

---

# 97. Recommended Architecture

```text
Router
   │
   ▼
Schema Validation
   │
   ▼
Service
   │
   ▼
Repository
   │
   ▼
SQLAlchemy
   │
   ▼
PostgreSQL
```

---

# 98. Full FastAPI Architecture

```text
                         CLIENT
                            │
                            ▼
                    HTML + CSS + JS
                            │
                            │ HTTP/JSON
                            ▼
                     ┌─────────────┐
                     │   FastAPI   │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │   Router    │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │  Pydantic   │
                     │   Schema    │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │   Service   │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │ Repository  │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │ SQLAlchemy  │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │ PostgreSQL  │
                     └─────────────┘
```

---

# 99. FastAPI + Frontend Flow

```text
Browser
   │
   │ fetch()
   ▼
FastAPI Endpoint
   │
   ▼
Pydantic Validation
   │
   ▼
Service Logic
   │
   ▼
Database
   │
   ▼
JSON Response
   │
   ▼
JavaScript
   │
   ▼
DOM Update
```

---

# 100. JavaScript Fetch Example

```javascript
async function getUsers() {

    const response =
        await fetch(
            "http://localhost:8000/api/v1/users"
        );

    const data =
        await response.json();

    console.log(data);

}
```

---

# 101. FastAPI Response

```python
@router.get("/users")
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

# 102. FastAPI + PostgreSQL Flow

```text
Frontend
    │
    ▼
FastAPI
    │
    ▼
Router
    │
    ▼
Pydantic
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

# 103. Complete Full-Stack Project Structure

```text
my-project/
│
├── backend/
│   │
│   ├── app/
│   │   ├── main.py
│   │   ├── config.py
│   │   ├── database.py
│   │   ├── dependencies.py
│   │   │
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   └── product.py
│   │   │
│   │   ├── schemas/
│   │   │   ├── user.py
│   │   │   └── product.py
│   │   │
│   │   ├── routers/
│   │   │   ├── auth.py
│   │   │   ├── users.py
│   │   │   └── products.py
│   │   │
│   │   ├── services/
│   │   │   ├── auth_service.py
│   │   │   └── user_service.py
│   │   │
│   │   └── utils/
│   │       ├── security.py
│   │       └── validators.py
│   │
│   ├── alembic/
│   ├── tests/
│   ├── .env
│   ├── requirements.txt
│   └── README.md
│
└── frontend/
    │
    ├── index.html
    │
    ├── pages/
    │
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

# 104. Development Order

```text
1. Create Virtual Environment
        ↓
2. Install FastAPI
        ↓
3. Create App
        ↓
4. Create Config
        ↓
5. Setup PostgreSQL
        ↓
6. Setup SQLAlchemy
        ↓
7. Create Models
        ↓
8. Create Pydantic Schemas
        ↓
9. Setup Alembic
        ↓
10. Create Routers
        ↓
11. Create CRUD
        ↓
12. Add Service Layer
        ↓
13. Add Authentication
        ↓
14. Add CORS
        ↓
15. Connect Frontend
        ↓
16. Testing
        ↓
17. Deployment
```

---

# 105. Run Development Server

```bash
uvicorn app.main:app --reload
```

Specific host:

```bash
uvicorn app.main:app \
    --host 0.0.0.0 \
    --port 8000
```

---

# 106. Production

Do not use `--reload` in production.

Example:

```bash
uvicorn app.main:app \
    --host 0.0.0.0 \
    --port 8000
```

For larger deployments, FastAPI can be served through a production ASGI deployment setup.

---

# 107. Security Checklist

```text
□ SECRET_KEY .env me rakho

□ Database password hardcode mat karo

□ Password hash karke store karo

□ JWT expiry rakho

□ Input validation karo

□ Pydantic schemas use karo

□ File uploads validate karo

□ File names safely generate karo

□ CORS restrict karo

□ HTTPS use karo

□ Production me debug/reload disable karo

□ Sensitive errors client ko mat bhejo

□ Authentication + Authorization separate rakho

□ Admin routes protect karo

□ Database transactions properly handle karo

□ Dependencies updated rakho

□ Secrets GitHub par commit mat karo
```

---

# 108. FastAPI Mental Model

```text
FastAPI
   │
   ├── Router
   │      ↓
   │   Request
   │      ↓
   │   Pydantic
   │      ↓
   │   Validation
   │      ↓
   │   Service
   │      ↓
   │   Database
   │      ↓
   │   Response
   │
   ├── Dependency
   │      ↓
   │   Shared Logic
   │
   ├── Model
   │      ↓
   │   Database Structure
   │
   ├── Schema
   │      ↓
   │   Request/Response Structure
   │
   └── Config
          ↓
       Settings
```

---

# 109. Golden Rule

```text
Request
   ↓
Router
   ↓
Pydantic Validation
   ↓
Dependency
   ↓
Service
   ↓
Repository
   ↓
SQLAlchemy
   ↓
PostgreSQL
   ↓
Response Schema
   ↓
JSON Response
```

---

# 110. Final FastAPI SDK Checklist

```text
FASTAPI CORE
□ FastAPI
□ Uvicorn
□ Routes
□ HTTP Methods
□ Path Parameters
□ Query Parameters
□ Request Body
□ Response
□ Status Codes
□ HTTPException

PYDANTIC
□ BaseModel
□ Field
□ EmailStr
□ Request Schema
□ Response Schema
□ Validation

ARCHITECTURE
□ APIRouter
□ App Factory
□ Config
□ Dependencies
□ Services
□ Repository
□ Utils

DATABASE
□ PostgreSQL
□ SQLAlchemy
□ Models
□ Sessions
□ CRUD
□ Relationships
□ Transactions
□ Alembic
□ Migrations

AUTH
□ Register
□ Login
□ Password Hashing
□ JWT
□ OAuth2 Bearer
□ Protected Routes
□ Current User
□ Roles
□ Authorization

API
□ REST API
□ GET
□ POST
□ PUT
□ PATCH
□ DELETE
□ Pagination
□ Search
□ Sorting
□ API Versioning
□ Error Handling

FILES
□ UploadFile
□ File()
□ Multiple Upload
□ File Validation
□ Secure Filename
□ Static Files

ADVANCED
□ Dependency Injection
□ Middleware
□ Background Tasks
□ Async/Await
□ Async Database
□ WebSocket
□ Cookies
□ Headers

FRONTEND
□ CORS
□ fetch()
□ JSON
□ Authentication Header
□ File Upload

DOCUMENTATION
□ Swagger
□ ReDoc
□ OpenAPI
□ Tags

TESTING
□ pytest
□ TestClient
□ API Tests
□ Authentication Tests

PRODUCTION
□ Environment Variables
□ Logging
□ HTTPS
□ Production ASGI Server
□ No --reload
□ Database Migrations
□ Security
```

---

# 111. Flask vs FastAPI Mental Model

```text
FLASK                         FASTAPI

@app.route()          →       @app.get()
request.get_json()    →       Pydantic Model
Blueprint             →       APIRouter
Flask-SQLAlchemy      →       SQLAlchemy
Flask-CORS            →       CORSMiddleware
Flask-JWT             →       OAuth2 + JWT
Jinja Templates       →       JSON API / Templates
Manual Validation     →       Pydantic Validation
Manual Docs           →       Automatic OpenAPI
WSGI                  →       ASGI
```

---

# 112. FastAPI Best Practice Architecture

```text
                    FastAPI Application
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          Routers        Dependencies    Middleware
             │              │              │
             ▼              ▼              ▼
          Schemas       Authentication    CORS
             │
             ▼
          Services
             │
             ▼
        Repositories
             │
             ▼
         SQLAlchemy
             │
             ▼
         PostgreSQL
```

> Small projects me Router → SQLAlchemy directly bhi chal sakta hai. Project bada hone par Service + Repository layers maintainability ke liye useful hote hain.
