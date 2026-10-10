# Juno Advising — HackNC frontend

React + Vite financial dashboard prototype for the Juno Advising AI Financial Copilot.

## Run locally

Requires Node.js 20+.

```bash
npm install
npm run dev
```

Open the local URL shown by Vite (normally http://localhost:5173).

## Features
- Dashboard with account balance, income, expenses, safe-to-spend
- 30-day balance forecast chart
- Interactive purchase affordability simulator and safety cushion
- Recent transactions, bills, spending categories
- AI Copilot chat page (calls POST /api/chat, shows demo fallback if unavailable)
- Responsive sidebar navigation

## Connect to Express

Vite proxies `/api` to `http://localhost:3001` (see `vite.config.js`).

Implement `POST /api/chat` returning `{ "reply": "..." }`.

Currently, the financial widgets read `DEMO` from `src/App.jsx`. Replace that object with data from your backend using `GET /api/dashboard`, and replace the local forecast and affordability logic with your backend's `GET /api/forecast` and `POST /api/simulate` results. Keep money math and risk calculations on the backend; don't let Gemini invent them.

**Important:** All banking values are sample data. There is no real Nessie, Gemini, Photon, or Tiger Data connection in this frontend. Do not put API keys in Vite `VITE_` variables or browser code. Keep keys in the Express server.

## Team handoff

- Frontend: UI and fetch calls
- Backend: Nessie data normalization and endpoints
- Forecasting/database: forecast logic, alerts, Tiger Data
- AI/messaging: Gemini and Photon Spectrum integration
