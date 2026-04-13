# FurFriend — Backend API

[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://www.mongodb.com)
[![Jest](https://img.shields.io/badge/Jest-C21325?style=flat-square&logo=jest&logoColor=white)](https://jestjs.io)

REST API backend for **FurFriend** — a social platform for pet lovers. Handles authentication, posts, comments, user profiles, file uploads, and location tracking.

> **Related:** [furfriend-frontend](https://github.com/omer-sch/furfriend-frontend) — React + TypeScript client

---

## Features

- 🔐 **JWT Authentication** — register, login, token refresh via middleware
- 📝 **Posts** — create, read, update, delete with file attachment support
- 💬 **Comments** — full CRUD on post comments
- 👤 **User Profiles** — manage and update user data
- 📍 **Location Tracking** — store and query user locations
- 📁 **File Uploads** — image upload route with multer
- ✅ **Test Coverage** — Jest test suite covering auth, posts, comments, files, and users

---

## API Routes

| Resource | Method | Endpoint | Description |
|----------|--------|----------|-------------|
| Auth | POST | `/auth/register` | Register new user |
| Auth | POST | `/auth/login` | Login + get JWT |
| Auth | POST | `/auth/refresh` | Refresh access token |
| Posts | GET | `/post` | Get all posts |
| Posts | POST | `/post` | Create post |
| Posts | PUT | `/post/:id` | Update post |
| Posts | DELETE | `/post/:id` | Delete post |
| Comments | GET | `/comment/:postId` | Get comments for post |
| Comments | POST | `/comment` | Add comment |
| Comments | DELETE | `/comment/:id` | Delete comment |
| Users | GET | `/user/:id` | Get user profile |
| Users | PUT | `/user/:id` | Update profile |
| Location | POST | `/location` | Save user location |
| Location | GET | `/location` | Get nearby users |
| Files | POST | `/file` | Upload image |

---

## Project Structure

```
src/
├── app.ts                    # Express app setup, middleware, route mounting
├── server.ts                 # HTTP/HTTPS server entry point
├── common/
│   └── auth_middleware.ts    # JWT verify middleware
├── controllers/
│   ├── base_controller.ts    # Generic CRUD base class
│   ├── auth_controller.ts    # Register, login, token refresh
│   ├── post_controller.ts    # Post CRUD
│   ├── comment_controller.ts # Comment CRUD
│   ├── user_controller.ts    # User profile management
│   └── userLocation_controller.ts  # Location queries
├── models/
│   ├── user_model.ts         # User schema (name, email, password, avatar)
│   ├── post_model.ts         # Post schema (content, image, author, likes)
│   ├── comment_model.ts      # Comment schema (text, author, post ref)
│   └── location_model.ts     # Location schema (userId, coordinates)
├── routes/
│   ├── auth_route.ts
│   ├── post_route.ts
│   ├── comment_route.ts
│   ├── user_route.ts
│   ├── location_route.ts
│   └── file_route.ts
└── tests/
    ├── auth.test.ts
    ├── post.test.ts
    ├── comment.test.ts
    ├── user.test.ts
    └── file.test.ts
```

---

## Tech Stack

| | Technology |
|--|-----------|
| Runtime | Node.js |
| Language | TypeScript |
| Framework | Express.js |
| Database | MongoDB + Mongoose |
| Auth | JWT (jsonwebtoken) |
| File Uploads | Multer |
| Testing | Jest + Supertest |

---

## Getting Started

```bash
git clone https://github.com/omer-sch/furfriend_Back.git
cd furfriend_Back
npm install
```

Create a `.env` file:

```env
PORT=3000
MONGO_URI=mongodb://localhost:27017/furfriend
JWT_SECRET=your_secret_here
JWT_REFRESH_SECRET=your_refresh_secret_here
```

```bash
npm run dev      # development
npm run build    # compile TypeScript
npm start        # production
npm test         # run Jest test suite
```

---

## Related

- **Frontend:** [furfriend-frontend](https://github.com/omer-sch/furfriend-frontend) — React + TypeScript + Vite
