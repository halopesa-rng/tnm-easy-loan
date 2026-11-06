# Ghana Loan Portal (independent application service)

A Ghana-focused loan application portal with a yellow-and-black visual theme inspired by common mobile-money design conventions. This is an independent service and is not affiliated with, endorsed by, or operated by MTN, Telecel, AT or any mobile-money provider. Do not use provider logos or imply provider approval.

## Customer flow
- Enter full name, Ghana mobile number, selected mobile-money network (MTN MoMo, Telecel Cash or AT Money), and requested amount in GHS.
- Application is sent to the assigned Telegram administrator for review.
- After details approval, the customer enters a non-secret application reference number.
- The reference number is reviewed by an administrator; approval completes the application.
- The application never asks for wallet PINs, OTPs, passwords, SMS contents, or security codes. No advance deposit is required to unlock an application.

## Admin controls
- Super Admin: `/addadmin CHAT_ID ADMIN003`, `/revokeadmin CHAT_ID`, `/admins`, `/stats`.
- Admin: `/mylink`, `/pending`, `/stats`, `/myinfo`.
- Telegram review buttons approve/reject application details and approve/reject reference numbers.
- Personal admin links use `?admin=ADMIN003`.

## Environment
Set `DATABASE_URL`, `TELEGRAM_BOT_TOKEN`, `SUPER_ADMIN_CHAT_ID`, and `APP_BASE_URL` (public HTTPS URL). `ADMIN_CHAT_IDS` and `TELEGRAM_WEBHOOK_SECRET` are optional. Build: `npm install`. Start: `npm start`. Health: `/health`.

## Important
Before accepting real loan applications, obtain the required Ghanaian lending and data-protection approvals, publish the lender's legal identity, interest/APR, fees, repayment schedule, privacy notice and complaints process, and connect only authorized payment-provider APIs. This portal does not itself disburse funds or verify wallet balances.
