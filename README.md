# Pocket

Pocket is a personal task and time-tracking app. Create daily task blocks, log time against targets, keep notes for each task, and review your progress through weekly, monthly, and yearly statistics.

## Features

- **Daily task blocks** with time tracking and targets
- **Quick time adjustments** in 30-minute steps
- **Notes** for each task
- **Statistics** with weekly, monthly, and yearly views and charts
- **Email verification** on registration, with a link sent to your inbox
- **JWT authentication** with protected routes

## Repositories

| Part | Stack | Path |
|---|---|---|
| Backend | Python 3.13, FastAPI, SQLAlchemy (async), fastapi-mail, Jinja2 | [`backend/`](https://github.com/life-in-pocket/frontend) |
| Frontend | React, TypeScript, Vite, React Router, Tailwind CSS v4 | [`frontend/`](https://github.com/life-in-pocket/backend) |

Each part has its own README with setup instructions.

## Quick Start

### 1. Backend

```bash
cd backend
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env             # fill in your values
uvicorn app.main:app --reload
```

The API runs at `http://localhost:8000`. Interactive docs are at `http://localhost:8000/docs`.

### 2. Frontend

```bash
cd frontend
npm install
npm run dev
```

The app runs at `http://localhost:5173`.

## Configuration

The backend reads its settings from `backend/.env`. The most important variables are:

| Variable | Purpose |
|---|---|
| `DATABASE_URL` | Database connection string |
| `SECRET_KEY` | Signs JWT tokens |
| `FRONTEND_URL` | Base URL used in email links |
| `MAIL_SERVER`, `MAIL_PORT` | SMTP server and port |
| `MAIL_USERNAME`, `MAIL_PASSWORD` | SMTP credentials |
| `MAIL_FROM`, `MAIL_FROM_NAME` | Sender address and name |

For local email testing, use a [Mailtrap](https://mailtrap.io) sandbox so messages never reach real inboxes.

## How Email Verification Works

1. A user registers, and a verification email is sent.
2. The link opens the frontend `/verify-email` page, which sends the token to the API.
3. The API verifies the token, marks the account as confirmed, and sends a welcome email.
4. Users can log in only after verifying their email.

## Contributing

1. Fork the repository and create a feature branch.
2. Keep changes focused, and describe what changed and why.
3. Never commit `.env` files or credentials.
