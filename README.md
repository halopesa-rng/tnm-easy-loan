# Tea Farm Management System

Role-based Node.js + Express + PostgreSQL farm management application.

## Role dashboards and permissions

- **Administrator:** full access, including creating staff accounts, assigning roles, linking staff accounts to plucker/worker records, and activating/deactivating accounts.
- **Director:** farm-wide dashboard, production, pluckers/workers, payroll, plots, deliveries, expenses and reports.
- **Manager:** operational dashboard and access to daily farm operations, staff records, picking, payroll, plots, deliveries, expenses and reports.
- **Plucker:** personal dashboard showing their own monthly picking, estimated earnings and picking history.
- **Worker:** personal dashboard showing their own picking and earnings when their account is linked to a worker record.

## Farm features
- Dashboard with current-month picking, factory deliveries, expenses, payments, active staff and plots
- Plucker and worker register with activate/deactivate
- Daily picking entries by date, worker, plot, kilograms and rate per kg
- Monthly plucker payroll and payment recording
- Farm plot register
- Factory delivery and receipt records
- Expense tracking by category
- Six-month operational reports and CSV export
- PostgreSQL persistence and PostgreSQL-backed sessions
- Password hashing and role-based route permissions
- Render Blueprint deployment

## First login and staff setup

1. Deploy using the Render Blueprint or the manual settings below.
2. Set `ADMIN_PASSWORD` to a strong password. `ADMIN_USERNAME` defaults to `admin`.
3. The first startup creates the Administrator account if it does not already exist.
4. Sign in as Administrator and open **User accounts**.
5. Add Director and Manager accounts.
6. Open **Pluckers & workers** and register each plucker/worker.
7. Return to **User accounts**, create a Plucker or Worker login and link it to that person's worker record.
8. Share each person's username and temporary password securely. They should sign in and use their own dashboard.

If a username already exists, create a different username. Existing farm records are retained; the upgrade adds the user-account table and does not delete existing worker, picking, payroll, plot, delivery or expense data.

## Deploy on Render

1. Upload this project to a GitHub repository.
2. In Render choose **New + → Blueprint** and connect the repository.
3. Render provisions the web service and PostgreSQL database from `render.yaml`.
4. Set `ADMIN_PASSWORD` to a strong unique password.
5. Open the generated service URL.

Build command: `npm install`  
Start command: `npm start`

Required environment variables: `DATABASE_URL`, `SESSION_SECRET`, `ADMIN_PASSWORD`. The Blueprint generates `SESSION_SECRET` and connects the managed database.

## Local run

Install Node.js 20+ and PostgreSQL. Copy `.env.example` to `.env`, configure values, then run `npm install` and `npm start`. Open `http://localhost:3000`.

## Notes

Currency is displayed in Kenyan shillings (KSh). This system records farm operations and does not automatically connect to a factory, bank, payroll provider or mobile-money service. Back up PostgreSQL regularly. Never commit `.env` or share passwords.
