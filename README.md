# InvoiceFlow

Production build of InvoiceFlow. Clone it, add a `.env`, run `npm start`. No install or build step is needed, everything is included.

## Requirements

- Node.js 20 or newer
- PostgreSQL 14 or newer

## Setup

1. Create a database

   ```bash
   createdb invoice_builder
   ```

2. Copy `.env.example` to `.env` and fill it in

   ```
   DATABASE_URL=postgres://postgres:password@localhost:5432/invoice_builder
   SENDGRID_API_KEY=SG.xxxxx
   MAIL_FROM=verified@yourdomain.com
   MAIL_FROM_NAME=InvoiceFlow
   PORT=3000
   ```

   `MAIL_FROM` must be a verified sender in SendGrid. Everything except email works without the SendGrid key.

3. Start the server

   ```bash
   npm start
   ```

   Open http://localhost:3000. Database tables are created automatically on the first request.

## Running in production

Keep it alive with a process manager, for example:

```bash
npm i -g pm2
pm2 start npm --name invoiceflow -- start
```

Put it behind nginx or any reverse proxy for HTTPS.

## Environment variables

| Name | Purpose |
| --- | --- |
| `DATABASE_URL` | PostgreSQL connection string |
| `SENDGRID_API_KEY` | SendGrid API key for sending invoices |
| `MAIL_FROM` | Verified sender address |
| `MAIL_FROM_NAME` | Sender name shown in the email |
| `PORT` | Port to listen on (default 3000) |
