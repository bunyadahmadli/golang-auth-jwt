# golang-auth-jwt

User registration and login with JWT authentication — a Go (Fiber) REST API backed by PostgreSQL, with a Vue 3 + TypeScript client.

## Features

- Register and log in with email and password.
- Passwords hashed with bcrypt.
- JWT issued on login and stored in an HTTP-only cookie.
- Get the current user and log out.
- User roles (`SystemAdmin`, `BasicUser`).

## Tech stack

| Layer | Technology |
|---|---|
| API | Go, [Fiber](https://gofiber.io/), [jwt-go](https://github.com/dgrijalva/jwt-go), bcrypt |
| Database | PostgreSQL, [GORM](https://gorm.io/) (auto-migration) |
| Client | Vue 3, TypeScript, Vue Router, Vuex |

## API

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/register` | Create a user |
| `POST` | `/api/login` | Log in, sets the JWT cookie |
| `GET` | `/api/user` | Current user (requires the JWT cookie) |
| `POST` | `/api/logout` | Clear the JWT cookie |

## Run locally

**API** (port 3000)

1. Start PostgreSQL and update the connection string in `database/connection.go`.
2. Enable the `database.ConnectDb()` call in `main.go`.
3. Run:

```bash
go run .
```

**Client**

```bash
cd client
npm install
npm run serve
```

## Notes

This is a learning project. Before using it in production:

- Read the JWT signing key and database credentials from environment variables instead of the source code.
- Replace `dgrijalva/jwt-go`, which is no longer maintained, with [`golang-jwt/jwt`](https://github.com/golang-jwt/jwt).
- Restrict CORS to known origins.

## License

[MIT](LICENSE)
