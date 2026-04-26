<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->


# About this project

## Product Overview

This project is a marketplace platform similar to Airbnb, but for renting garages and parking spaces.

Users can:
- List their garage or parking space
- Set availability via a calendar
- Accept or reject booking requests

Renters can:
- Discover nearby garages
- Select a date range
- Send booking requests

Hosts receive a notification (SMS/email) and can approve or reject the request.

---

## Core Problem

Parking in urban areas is difficult and inefficient:
- Many unused private garages exist
- No centralized platform for short-term rentals
- Current solutions (OLX, Facebook) lack structure, trust, and booking capabilities

This platform solves:
- Discovery (finding available garages)
- Booking (calendar-based reservations)
- Coordination (host approval flow)

---

## Core Features (MVP)

- User authentication
- Garage listing creation
- Calendar-based availability
- Booking requests (not instant booking)
- Host approval / rejection
- SMS + email notifications
- Basic map view

---

## Booking Flow

1. User selects garage and date range
2. User submits booking request
3. Host receives notification (SMS + email)
4. Host approves or rejects request
5. If approved → booking is confirmed
6. If no response → request expires

---

## Key Constraint

No instant booking in MVP.

Reason:
- Prevent double booking (external channels like OLX)
- Ensure host confirmation

---

## Tech Stack

### Frontend
- Next.js (React framework)
- Hosted on Vercel

### Backend
- Supabase (Backend-as-a-Service)

Includes:
- PostgreSQL database
- Authentication (Google / email)
- Storage (garage images)
- Auto-generated APIs

### Database
PostgreSQL (managed by Supabase)

Core tables:
- users
- garages
- bookings
- booking_requests

### Notifications
- Twilio (SMS)
- Email (fallback)

### Maps
- Mapbox (preferred) or Google Maps

### Payments (future)
- Stripe (marketplace payments)

---

## Architecture
Client (browser)
↓
Next.js (Vercel)
↓
Supabase (DB + Auth + Storage)
↓
Twilio (SMS notifications)


---

## Cost Strategy

All services are chosen with:
- Free tiers
- Pay-as-you-go pricing

Goal:
- Near-zero cost when no users
- Scales automatically with usage

---

## Access Strategy (MVP)

No smart lock integration.

Instead:
- Hosts provide access instructions manually
- Examples:
  - Lockbox code
  - Garage PIN
  - Key location

Instructions are shown only after booking confirmation.

---

## Future Improvements

- Instant booking (for trusted hosts)
- Calendar sync (Google Calendar / iCal)
- Smart lock integrations
- Ratings & reviews
- Mobile app (iOS/Android)
- Dynamic pricing

---

## Goal of MVP

Validate:
- Do users list garages?
- Do users request bookings?
- Do users like the app enough to go beyond MVP?

Not optimized for:
- Scale
- Performance
- Complex automation

---

## Guiding Principle

Move fast, validate demand, then scale architecture.

Avoid over-engineering in early stages.