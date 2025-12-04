
# Social Pulse

**Social Pulse** is my full-stack social media platform built on the MERN stack. It delivers the core experiences I wanted from a modern community: create posts with captions and images, react to what friends share, discover new people to follow, and keep profiles up to date.

---

## Feature Highlights

- Email/password onboarding with JWT-authenticated sessions
- Personalized timeline that aggregates posts from followed users
- Rich post composer with image uploads, captions, and live preview
- Instant like/unlike interactions and optimistic UI feedback
- Follow suggestions plus follower/following counts on profile cards
- Profile editing (name, bio, relationship status, workplace, etc.)
- Responsive layout optimized for desktop-sized breakpoints

---

## Tech Stack

| Layer     | Tools |
|-----------|-------|
| Frontend  | React 18, Redux Toolkit, React Router, Material UI Icons, custom CSS modules |
| Backend   | Node.js 20, Express 4, Mongoose 7, Multer, Bcrypt, JSON Web Tokens |
| Database  | MongoDB Community 7.x (local or Atlas) |
| Tooling   | Nodemon, npm scripts, dotenv |

---

## Architecture Overview

- `client/`: React app bootstrapped with CRA. State is centralized in `store/ReduxStore.js` with async actions living under `src/actions`.
- `Server/`: Express API exposing auth, user, post, and upload routes. Controllers encapsulate business logic, while Mongoose models reside in `Server/Models`.
- Static assets (profile and cover defaults) live under `Server/public/images`, and are exposed via `GET /images/:filename`.

```
client (React)
   ↕ REST via axios (http://localhost:4000)
Server (Express + MongoDB)
   ↳ Auth/User/Post/Upload routes
```

---

## Getting Started

### Prerequisites
- Node.js ≥ 18
- npm (ships with Node)
- MongoDB running locally (`brew services start mongodb/brew/mongodb-community@7.0`) or a MongoDB Atlas URI

### Environment Variables

Create `Server/.env`:
```
PORT=4000
MONGO_DB=mongodb://127.0.0.1:27017/socialmedia
JWT_KEY=change-me
```

Create `client/.env`:
```
REACT_APP_PUBLIC_FOLDER=http://localhost:4000/images/
```

### Install & Run

```bash
# Backend
cd Server
npm install
npm start   # runs nodemon on http://localhost:4000

# Frontend (in new terminal)
cd client
npm install
npm start   # CRA dev server on http://localhost:3000
```

Visit `http://localhost:3000`, register an account, and start sharing posts. The React dev server proxies API calls to the backend automatically.

---

## Useful Scripts

| Location | Command | Description |
|----------|---------|-------------|
| `Server` | `npm start` | Starts nodemon with hot reload |
| `client` | `npm start` | CRA dev server with fast refresh |
| `client` | `npm test` | React Testing Library suite (placeholder) |

---

## Folder Structure

```
├── README.md
├── Server
│   ├── Controllers
│   ├── Middleware
│   ├── Models
│   ├── Routes
│   └── public/images
└── client
    ├── src
    │   ├── Components
    │   ├── Pages
    │   ├── actions / reducers / store
    │   └── api (axios wrappers)
    └── public
```

---

## Roadmap

- [ ] Push notifications for new followers & likes
- [ ] Real-time comments via WebSockets
- [ ] Dark mode theme toggle
- [ ] Deployment scripts (Render / Vercel / Railway)

---

## Screenshots

Add your own captures under `docs/screenshots` and reference them here, e.g.

```
![Homepage](docs/screenshots/home.png)
![Profile](docs/screenshots/profile.png)
```

---

## License

This project is released under the MIT License. Feel free to fork, extend, and ship your own social platform on top of it. If you build something cool, let me know! 😄
    