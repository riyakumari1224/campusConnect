# CampusConnect

CampusConnect is a campus community platform for discovering student societies, keeping up with campus events and announcements, and managing club recruitment and applications. The repository contains a web app, a companion mobile app, and a REST API.

## Features

- Browse approved societies, their teams, events, and open recruitments.
- View campus events, announcements, and FAQs.
- Student registration and sign-in, recruitment applications, and application status tracking.
- Club dashboards for managing society profiles, teams, events, recruitments, announcements, and applications.
- Admin tools for reviewing club registrations and publishing campus-wide announcements.
- Role-based authentication for students, clubs, and admins.

## Project structure

```text
backend/      Express 5 API, TypeScript, MongoDB
webFrontend/  Next.js web application
frontend/     Expo / React Native mobile application
```

## Tech stack

- **Web:** Next.js 14, React 18, TypeScript
- **Mobile:** Expo, React Native, Expo Router, TypeScript
- **API:** Node.js 20+, Express 5, TypeScript, MongoDB with Mongoose

## Prerequisites

- Node.js 20 or later and npm
- MongoDB, running locally or available through a connection URI
- Expo Go or an Android/iOS development environment to run the mobile app

## Getting started

Run each app or service in its own terminal. Install dependencies separately in each project directory.

### 1. Start the API

```bash
cd backend
npm install
```

Create `backend/.env` from the example:

```bash
cp .env.example .env
```

On Windows PowerShell, use `Copy-Item .env.example .env`.

Set at least `MONGODB_URI` to your MongoDB connection string. The example uses a local database at `mongodb://127.0.0.1:27017/campus_connect`. Then start the API:

```bash
npm run dev
```

The API listens on port `4000` by default. Check `http://localhost:4000/health/live` for liveness and `http://localhost:4000/health/ready` for readiness, including the database connection.

### 2. Start the web app

```bash
cd webFrontend
npm install
```

Create `webFrontend/.env.local` and set the API URL:

```env
NEXT_PUBLIC_API_URL=http://localhost:4000
```

Run the development server:

```bash
npm run dev
```

Open `http://localhost:3000`.

### 3. Start the mobile app

```bash
cd frontend
npm install
```

Create `frontend/.env` with the API URL:

```env
EXPO_PUBLIC_API_URL=http://localhost:4000
```

Then start Expo:

```bash
npm start
```

Use the Expo CLI prompts to open the app on a device or simulator. When testing on a physical device, use your computer's LAN IP address instead of `localhost` for the API URL.

## Environment configuration

Examples are provided in `backend/.env.example`, `webFrontend/.env.example`, and `frontend/.env.example`. Do not commit `.env` files or put private credentials in either frontend.

The backend supports optional integrations and settings:

- `GOOGLE_CLIENT_ID` enables Google sign-in for existing student accounts.
- `ADMIN_ID` and `ADMIN_PASSWORD` configure admin login; set both together.
- `SMTP_URL`, `SMTP_FROM`, and `PASSWORD_RESET_URL` configure password-reset email delivery.
- `CORS_ORIGINS` accepts a comma-separated list of allowed origins.
- `JWT_SECRET` must be a strong secret of at least 32 characters in production.

For production, configure secrets through your hosting provider, use HTTPS, and set the frontend API URLs to your deployed API. See [backend/README.md](./backend/README.md) for detailed API, authentication, and environment documentation.

## Useful commands

| Project | Command | Description |
| --- | --- | --- |
| `backend` | `npm run dev` | Run API in development watch mode |
| `backend` | `npm run typecheck` | Type-check the API |
| `backend` | `npm run build` | Compile the API to `dist/` |
| `backend` | `npm start` | Run the compiled API |
| `webFrontend` | `npm run dev` | Run the web app in development |
| `webFrontend` | `npm run build` | Build the web app |
| `webFrontend` | `npm start` | Run the production web build |
| `frontend` | `npm start` | Start Expo |
| `frontend` | `npm run android` | Start Expo for Android |
| `frontend` | `npm run ios` | Start Expo for iOS |
| `frontend` | `npm run web` | Start the mobile app's web target |

## API documentation

The API route reference and example requests are documented in [backend/README.md](./backend/README.md). The API includes health checks, authentication, public discovery, student applications, club management, and admin routes.

## License

The mobile app directory includes a [LICENSE](./frontend/LICENSE). Check the license terms before redistributing or reusing project materials.
