# Problem Statement

## 1. Title
LocalServe — Book Trusted Local Service Providers Near You

## 2. Domain
Home Services / Hyperlocal Marketplace

## 3. Who is the user? (2-3 user types, with roles)
- **Customer** — someone who needs a local service done (plumbing, cleaning, appliance repair, etc.) and wants to book a reliable provider without the usual back-and-forth calls.
- **Service Provider** — a local technician or small service business who wants more bookings and a proper way to manage their schedule instead of relying on word of mouth.
- **Admin** — manages the platform: approves new providers, keeps categories clean, and steps in if there's a dispute.

## 4. What problem are we solving? (3-5 sentences, real-life example)
Right now if you need a plumber or an AC repair guy on short notice, you're basically asking around in a family WhatsApp group or calling random numbers off a sticker on the lift wall. There's no way to check if the person is actually free today, no idea if they're any good, and no record of the booking if something goes wrong. Say my washing machine breaks down on a Saturday — I have no easy way to see which nearby technicians are free that afternoon, compare who's reliable, and just book a slot. LocalServe fixes this by letting customers search nearby providers, see their real availability, and book a confirmed slot directly — and it gives providers a proper dashboard to manage their bookings instead of juggling calls.

## 5. Proposed Solution (what the application will do, feature-wise)
- Browse/search providers by service category, location, and rating
- Book an actual open time slot — no calling to "check availability"
- Track booking status end to end: requested → accepted → in progress → completed → reviewed
- Provider side: a dashboard to manage listings, set availability, and see incoming bookings
- Ratings and reviews after every completed booking
- Basic sandbox payment on booking confirmation
- Email/SMS notification when a booking status changes
- Admin panel to approve providers and manage categories
- Later (enhancement phase): recommend providers to customers based on rating + how close they are + past bookings

## 6. Core Entities / Database Tables (list all, minimum 5)
1. **User** — shared login table (email, password hash, role, phone)
2. **ServiceProvider** — linked to a User; business name, bio, verified or not, location
3. **ServiceCategory** — e.g. Plumbing, Cleaning, Electrical
4. **ProviderService** — junction table linking providers to the categories they offer, with pricing
5. **AvailabilitySlot** — a specific date/time slot a provider has opened up, with an is_booked flag
6. **Booking** — links customer, provider, and slot together, with status
7. **Review** — rating + comment tied to a completed booking
8. **Payment** — amount, status, and reference tied to a booking

## 7. User Roles & Permissions (minimum 2 distinct roles, e.g. Admin & User)
- **Customer**: search providers, book/cancel a slot, leave a review, see their own booking history
- **Service Provider**: manage their own listings and availability, accept/complete bookings, see their own reviews and earnings
- **Admin**: approve or suspend providers, manage categories, view all bookings — doesn't book services themselves

## 8. Success Criteria (e.g. 'a user should be able to book an appointment in under 1 minute')
- A customer can find a provider and confirm a booking in under a minute
- No two bookings should ever land on the same slot for the same provider
- A review can only be left after the booking is actually marked completed
- Providers should see new bookings appear without refreshing the page manually

## 9. Out of Scope (clearly list what you will NOT build, to avoid over-commitment)
- Live GPS tracking of the provider on the way
- In-app chat between customer and provider (just notifications for now)
- Multiple currencies / international payments
- A native mobile app — web only, responsive
- Surge pricing or dynamic pricing logic

## 10. Chosen Track: Python (FastAPI)
