## Table of Contents



## Setup Instructions

### Prerequisites

- Python 3.8+
- PostgreSQL
- [pipenv](https://pipenv.pypa.io/en/latest/) or `pip`
- `git`

### Environment Variables

Create a `.env` file in the project root with the following:

```env
DATABASE_URL=postgresql://username:password@localhost:5432/late_show_db
SECRET_KEY=your_secret_key
FLASK_ENV=development
```

### Install Dependencies

```bash
pipenv install
# or
pip install -r requirements.txt
```

---

## How to Run

1. **Database Migration**

    ```bash
    flask db upgrade
    ```

2. **Seeding the Database**

    ```bash
    flask seed
    ```

3. **Run the Application**

    ```bash
    flask run
    ```

---

## Authentication Flow

- **Register:**  
  `POST /register` with JSON body `{ "username": "...", "password": "..." }`
- **Login:**  
  `POST /login` with JSON body `{ "username": "...", "password": "..." }`
- **Token Usage:**  
  On successful login, a JWT token is returned.  
  Include it in the `Authorization` header as `Bearer <token>` for protected routes.

---

## API Routes

| Method | Endpoint         | Description           | Auth Required |
|--------|------------------|----------------------|---------------|
| POST   | /register        | Register user        | No            |
| POST   | /login           | Login user           | No            |
| GET    | /shows           | List all shows       | Yes           |
| POST   | /shows           | Create a show        | Yes           |
| GET    | /shows/:id       | Get show details     | Yes           |

### Sample Request/Response

**Register**

```http
POST /register
Content-Type: application/json

{
  "username": "alice",
  "password": "password123"
}
```

**Response:**

```json
{
  "message": "User registered successfully."
}
```

**Login**

```http
POST /login
Content-Type: application/json

{
  "username": "alice",
  "password": "password123"
}
```

**Response:**

```json
{
  "access_token": "<JWT_TOKEN>"
}
```

---

## Postman Usage Guide

1. Import the API endpoints into Postman.
2. Set up an environment with your API base URL and JWT token.
3. For protected routes, add an `Authorization` header:  
    `Bearer <your_token>`
4. Use the sample requests above to test endpoints.

---

## GitHub Repository

[https://github.com/your-username/late-show-api](https://github.com/your-username/late-show-api)


