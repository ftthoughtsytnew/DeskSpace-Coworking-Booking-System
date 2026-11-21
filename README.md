# DeskSpace Coworking Booking System

A Next.js starter project for a 50-seat open coworking space in Delhi NCR.

## Included
- Responsive customer-facing landing page.
- Seat selection interface for 50 seats.
- Hourly, daily and monthly booking options.
- Customer details and payment preference form.
- Supabase PostgreSQL schema and controlled booking RPC.
- Database-level prevention of overlapping bookings for the same seat.
- Admin dashboard starter page.
- Environment variable template.

## Important status
This repository is a **starter MVP**, not a fully production-ready commercial booking platform. Supabase must be configured before real bookings work. The admin dashboard is a visual starter and does not yet authenticate administrators or manage records. Online payment is only a preference field; no payment gateway is integrated. Document upload is intentionally not enabled until private storage and admin access controls are configured.

## Requirements
- Node.js 20.9+
- npm
- A Supabase project

## Run locally
```bash
npm install
cp .env.example .env.local
npm run dev
```
On Windows PowerShell, copy the environment template with:
```powershell
Copy-Item .env.example .env.local
```
Then fill in the Supabase project URL and anon key in `.env.local`.

Open http://localhost:3000.

## Configure Supabase
1. Create a project at https://supabase.com.
2. Open SQL Editor.
3. Run the contents of `supabase/schema.sql`.
4. In Project Settings > API, copy the Project URL and anon/public key.
5. Add them to `.env.local`.
6. Restart the Next.js development server.

The SQL seeds 50 seats and creates a database function for guest bookings. It uses an exclusion constraint to prevent overlapping confirmed bookings for the same seat.

## Before public launch
Complete and test all of the following:
- Admin authentication and role-based access control.
- Admin-only booking, customer, document and pricing management.
- Secure private document bucket and strict storage policies.
- Payment gateway integration with server-side signature/webhook verification.
- Email/WhatsApp notifications.
- Anti-spam/rate limiting and CAPTCHA or verified phone/email.
- Cancellation, refund, check-in and no-show workflows.
- Legal review of privacy policy, terms and document retention.
- Backups, monitoring and recovery testing.

Do not collect Aadhaar/PAN by default. Collect only information genuinely required for the service and explain the purpose and retention period.

## GitHub upload
Extract this ZIP. Upload the **contents** of the extracted folder to your GitHub repository, not just the ZIP file, so GitHub displays `package.json`, `src/`, `supabase/` and `README.md` at the repository root.

Never commit `.env.local`, service-role keys, passwords or customer documents.
