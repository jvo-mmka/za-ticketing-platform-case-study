# Zã Ticketing Platform

Zã is an event ticketing platform I have been building as an independent software project.

I started the project because I wanted to understand how a real ticketing system works beyond just selling a ticket. Over time, it grew into a much larger system with reserved seating, general admission tickets, payments, ticket scanning, organizer tools, real-time updates and event management.

The actual source code for the project is private, but this repository gives an overview of what I built, the technologies I used and some of the technical problems I had to solve.

## What the platform can do

Some of the main features include:

- Event creation and management
- General admission and reserved-seat ticketing
- Interactive venue seat maps
- Real-time seat holding and release
- Online payments using Paystack
- Digital ticket generation
- Ticket scanning and verification
- Organizer dashboards
- Staff roles and permissions
- Refund handling
- Event analytics
- Notifications
- Event community features
- Support for large venues with thousands of seats

## Tech stack

**Backend**
- Python
- Django
- Django REST Framework
- PostgreSQL
- Redis
- Django Channels / WebSockets

**Frontend**
- Vue.js
- JavaScript
- Pinia
- Vue Router

**Other**
- Paystack
- Railway
- REST APIs
- JWT authentication
- Git

## One of the harder parts

One of the more difficult parts of the project was reserved seating.

When two people are looking at the same event, the system needs to make sure they cannot both buy the same seat.

I implemented temporary seat holds using Redis together with database state, so a selected seat becomes unavailable to other users for a limited period while the customer completes their purchase.

If the hold expires or the user releases the seat, it becomes available again.

I also had to make sure this continued to work correctly when users moved between pages, refreshed the browser or selected seats across different parts of a venue.

## Large venue performance

I also worked on supporting very large seat maps.

During testing, I used a venue with more than 20,000 seats. The first versions became slow when zooming, dragging and selecting sections, so I had to reduce unnecessary work during interaction and improve how the frontend handled the seat map.

That was one of the parts of the project that taught me the most about frontend performance.

## Payments

The platform uses Paystack for payment processing.

I implemented payment initialization, callbacks, webhook handling, payment confirmation, refunds and reconciliation logic.

I also built the order flow around the payment system so that tickets are only fulfilled after a payment has been successfully confirmed.

## What I learned from building it

This project has helped me learn much more than I would have learned from small tutorial projects.

I have worked with:

- API design
- authentication and permissions
- database modelling
- concurrent seat reservations
- third-party payment APIs
- real-time communication
- background processing
- frontend performance
- deployment
- debugging production issues

There are still parts of the platform I am improving, but it is currently the largest software project I have built.

## Live project

A deployed version of the platform is available here:

https://ticket-frontend-production-486f.up.railway.app/

## Source code

The production source code is kept in a private repository because the project is still under active development and contains implementation details I do not want to expose publicly.

I am happy to discuss the architecture, technical decisions and challenges I encountered during the project.
