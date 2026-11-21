# Security notes

- Never commit `.env.local` or any secret keys.
- The Supabase anon key is designed for client use only when RLS is correctly configured.
- Never expose the Supabase service-role key to browser code.
- Bookings and documents have RLS enabled with no public read policy.
- Public booking creation is restricted to a validation function.
- Add abuse prevention/rate limits before public launch.
- Add admin authentication and explicit admin-only policies before exposing admin data.
- Keep identity documents in a private bucket and provide short-lived signed URLs only to authorized staff.
- Do not store payment card details.
- Verify payment gateway webhooks on the server before marking payments as paid.
