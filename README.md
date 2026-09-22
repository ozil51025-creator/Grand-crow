# Grand Crown Platform

Grand Crown is a Node.js platform with a customer site and a mobile-responsive administrator panel.

## Local URLs
- Customer: http://localhost:3000/
- Admin: http://localhost:3000/admin

## Admin login
Default local credentials:
- Username: `admin`
- Password: `change-me-now`

For deployment, set `ADMIN_USER` and `ADMIN_PASS` environment variables and change the default credentials.

## Admin interface
The admin navigation follows the supplied Chipz/Doritos Admin reference layout: Dashboard, Analytics, Users, Deposits, Withdrawals, Products, Gift Codes, Messages, Transactions, Referrals, Settings, Countries, Admins and Activity Log. The dashboard uses a responsive two-column overview-card layout.

## PesaJet checkout payments
Grand Crown now provides a **Pay with PesaJet** button using this checkout link: https://pay.pesajet.com/pay/d9c18ef87c. Customers select a product, open checkout, then return and submit their phone number and PesaJet transaction/reference ID. The payment remains pending until an administrator verifies it and approves the purchase.

**Important:** This is a hosted-checkout link redirect, not a completed API/webhook integration. The app does not independently verify PesaJet payments or automatically activate purchases. Confirm the amount shown at checkout matches the selected product; for automatic confirmation and per-order amounts, configure PesaJet API credentials and a verified webhook with PesaJet.

## Withdrawal rules
- Minimum withdrawal: UGX 7,000
- Withdrawal fee: 12%
- At least one approved product purchase is required before withdrawal is allowed.
- Withdrawal requests remain pending until an administrator manually marks them paid or rejects them.

## Referral rules
- Every registered user receives a unique referral code.
- Three levels: 25% / 2% / 1%.
- Commissions are created only when the referred user's purchase is manually approved.
- Duplicate commission creation is prevented per purchase and level.

## Earnings
Approved purchases have independent earning schedules. The server credits one daily earning after each completed 24-hour period, up to the product validity period, and prevents duplicate daily credits.

## Support
- Customer support: `@Doritos1225`
- Telegram group: https://t.me/+zNDnaz_xKfdiMTlk

## Production notes
This package uses JSON storage for local/testing purposes. Before production real-money use, move to persistent database storage, use secure authentication/session storage, HTTPS, rate limiting, audit logging, backups, and appropriate payment/legal compliance.
