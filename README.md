# Tea Farm Management System

Responsive Node.js + Express + PostgreSQL farm dashboard.

## Features
- Administrator login
- Dashboard with current-month tea picked, deliveries, expenses, payments, workers and plots
- Worker register with activate/deactivate
- Farm plot register
- Tea picking records by date, worker, plot, kilograms and rate per kg
- Tea factory delivery records, receipt number and payments recorded
- Expense tracking by category
- Six-month operational reports and harvest CSV export
- PostgreSQL data persistence and PostgreSQL-backed sessions
- Render Blueprint (`render.yaml`)

## Deploy on Render
1. Upload this project to a GitHub repository.
2. In Render select **New + → Blueprint**, then connect the repository.
3. Render provisions the web service and PostgreSQL database from `render.yaml`.
4. In the service environment settings, set `ADMIN_PASSWORD` to a strong unique password. Keep or change `ADMIN_USERNAME` (default `admin`).
5. Deploy and open the generated service URL.

Build command: `npm install`
Start command: `npm start`

Required environment variables: `DATABASE_URL`, `SESSION_SECRET`, `ADMIN_PASSWORD`.
`render.yaml` generates `SESSION_SECRET` and connects the managed database.

## Local run
Install Node.js 20+ and PostgreSQL. Copy `.env.example` to `.env`, configure values, then run `npm install` and `npm start`. Open `http://localhost:3000`.

## Notes
Currency is displayed in Kenyan shillings (KSh). This system stores farm records; it does not automatically connect to factory, bank, payroll or mobile-money systems. Back up the PostgreSQL database regularly. Never commit `.env` or share admin credentials.


## Daily pluckers and monthly pay
- Register each tea plucker under **Pluckers**.
- Record each day's kilograms under **Daily picking**, selecting the plucker and entering the rate per kilogram for that day's work.
- Open **Monthly pay**, choose a month, and view each plucker's total kilograms and wages due.
- After paying, record the payment date, method (cash or M-Pesa), and optional reference. A second payment record for the same plucker and month is prevented.
- Wages are calculated as daily kilograms × the rate saved on that picking record.
