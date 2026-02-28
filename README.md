# Trade Hub

**Trade Hub** is a full‑stack second‑hand goods marketplace application.  The project consists of a Node/Express/MongoDB backend and a React/Tailwind frontend.  It supports user accounts, listings, messaging, disputes, global policy settings, and administrator tools.

## 🔧 Technologies Used

### Backend
- **Node.js** (v18+)
- **Express** – HTTP server and routing
- **MongoDB & Mongoose** – document database and ODM
- **JWT** (jsonwebtoken) – authentication tokens
- **bcrypt / bcryptjs** – password hashing
- **cors**, **dotenv**, **express-validator** etc. utility libraries
- **Nodemailer** – email notifications
- **Jest**, **Supertest**, **mongodb-memory-server** – unit & integration tests

### Frontend
- **React 18** (Create React App)
- **React Router v7** – client routing
- **Tailwind CSS** & **PostCSS** – utility-based styling
- **@mui/material**, **@nextui-org/react** – component libraries
- **Framer Motion** – animations
- Various helpers (axios, react-dropzone, react-slick, etc.)

### Dev tools & utilities
- **concurrently** – run frontend & backend together
- **nodemon** – auto reload server during development
- **eslint** config bundled with CRA

---

## 📁 Project Structure

```
trade-hub/
├─ backend/           # Express API server and business logic
│  ├─ classes/        # Domain model helper classes
│  ├─ config/         # Environment/config objects
│  ├─ controllers/    # Route handlers
│  ├─ middleware/     # Auth, admin, seller checks
│  ├─ models/         # Mongoose schemas
│  ├─ routes/         # API endpoints
│  ├─ services/       # Business logic
│  ├─ scripts/        # CLI helpers & seeding
│  ├─ tests/          # Jest tests (many disabled)
│  └─ server.js       # App entry point
├─ frontend/          # React single‑page application
│  ├─ public/         # Static assets
│  ├─ src/
│  │  ├─ components/  # UI components
│  │  ├─ pages/       # Route pages
│  │  ├─ services/    # API clients
│  │  └─ styles/      # Tailwind/custom styles
├─ package.json       # root, orchestrates both halves
└─ README.md          # ← you are here
```

---

## 🚀 Getting Started

### Prerequisites

1. **Node.js** and **npm** installed (v16+ recommended).
2. **MongoDB** running locally or accessible via URI.
3. Optionally, a `.env` file at repository root specifying environment variables (see below).

### Environment Variables

You can either set these in a `.env` file (loaded by `dotenv`) or in your shell:

| Variable        | Description                                 | Default / example                          |
|----------------|---------------------------------------------|-------------------------------------------|
| `PORT`         | backend server port                         | `5000`                                    |
| `MONGODB_URI`  | connection string for MongoDB               | `mongodb://localhost:27017/tradehub`      |
| `JWT_SECRET`   | secret for signing JSON web tokens          | `your-secret-key`                         |
| `FRONTEND_URL` | allowed origin in production (CORS)         |                                        |
| `API_BASE_URL` | frontend override for backend API base      | `http://localhost:5000/api`               |
| `REACT_APP_API_URL` | idem for CRA build                    | `http://localhost:5000/api`               |
| **Email config** | (optional) credentials for notifications | see `backend/config/email.js` & `emailjs.js` |

> **Note:** credentials in `config/*.js` are placeholders used for development. Replace them before deploying.

### Install Dependencies

Run from the repository root (project root):

```bash
npm install           # installs concurrently
npm run start         # will bootstrap backend + frontend concurrently
```

Alternately, install each half manually:

```bash
# backend
cd backend && npm install
# frontend
cd ../frontend && npm install
```

### Development

Navigate to the root and use the provided script:

```bash
npm run start
```

This command uses [`concurrently`](https://github.com/open-cli-tools/concurrently) to launch:
- `npm run dev` in `backend` (`nodemon server.js`)
- `npm start` in `frontend` (CRA dev server)

The frontend is served at `http://localhost:3000` by default; it proxies API requests to the backend at port 5000.

### Testing

Backend tests can be executed with:

```bash
cd backend && npm test
```

A lightweight in‑memory MongoDB instance is spun up for the test environment. Many tests are currently disabled and can be enabled for further coverage.

Frontend tests leverage CRA's `react-scripts test`:

```bash
cd frontend && npm test
```

### Scripts & Utilities

- **Seed data**: scripts in `backend/scripts` help populate users/items and manage an admin account.
- **API client**: frontend uses `src/services/api.js` to communicate with backend; adjust base URL via env vars.

### Building for Production

```bash
cd frontend && npm run build   # produces optimized static bundle
# serve the build with any static host or the backend can be configured to serve it
```

Configure CORS/`FRONTEND_URL` accordingly when deploying.

---

## 📌 Features (overview)

- User authentication (JWT, password hashing)
- CRUD operations on item listings
- Inbox/messaging between buyers and sellers
- Dispute submission process
- Admin dashboard with global policy settings,
  user/item management etc.
- Email notifications (Gmail via Nodemailer, EmailJS)


## 📝 License
This project is open-source and available under the terms of the [LICENSE](LICENSE) file.
