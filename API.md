# Backend interface

## Supabase RPC: `create_public_booking`

Parameters:
- `p_customer_name` text
- `p_email` text
- `p_phone` text
- `p_seat_number` integer (1–50)
- `p_booking_date` date
- `p_duration_type` hourly | daily | monthly
- `p_start_time` time (hourly only)
- `p_end_time` time (hourly only)
- `p_payment_method` online | pay_at_office

Returns JSON with `booking_id`, `booking_code`, and `status`.

The database function validates input and inserts the booking. A PostgreSQL exclusion constraint prevents overlapping confirmed bookings on the same seat.
