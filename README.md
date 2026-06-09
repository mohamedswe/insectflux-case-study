# InsectFlux Case Study

> Backend reliability, database migrations, testing infrastructure, and webhook-driven messaging for an agri-food marketplace.

**Role:** Backend / Reliability Engineer, one of three engineers  
**Status:** Public-safe case study. Source code is private/team-owned.  
**Primary ownership areas:** database migrations, forward/backward compatibility, testing suite, webhook messaging/payment reliability, backend hardening.

## Overview

InsectFlux is a marketplace platform for the insect-farming and agri-food ecosystem. The product connected suppliers and customers through marketplace workflows involving listings, checkout, messaging, reviews, payments, and supplier/customer interactions.

I worked on the project as one of three engineers. My main contributions were in the backend systems that made the product safer to evolve and closer to production-ready:

- database migrations and compatibility paths,
- backend and frontend test infrastructure,
- webhook-driven messaging/payment reliability,
- idempotency/race-condition prevention,
- production-readiness hardening around critical marketplace flows.

This case study intentionally focuses on my verified ownership areas and avoids claiming teammates' work.


## Screenshots


### Homepage hero

![InsectFlux homepage hero](assets/homepage-hero.png)

### Marketplace products view

![InsectFlux marketplace products](assets/marketplace-products.png)

### How it works section

![InsectFlux how it works section](assets/homepage-how-it-works.png)

## Why this project matters

Most student/new-grad projects are simple CRUD apps. InsectFlux forced more mature engineering problems:

- evolving a live marketplace data model without breaking existing behavior,
- testing money/order/inventory flows,
- preventing duplicate webhook processing,
- handling supplier/customer messaging state,
- protecting checkout and inventory behavior,
- making a multi-engineer codebase safer to change.

## Technical Highlights

### 1. Database migrations with forward/backward compatibility

The app's marketplace model evolved over time, which meant older and newer data shapes needed to coexist safely.

My work focused on migration and compatibility logic so the system could evolve without brittle one-shot changes.

Evidence areas from the private codebase:

- service migration script,
- multi-currency schema plan,
- compatibility-aware model logic,
- old/new marketplace record handling.

Key engineering concern:

> Changing a schema is easy. Changing a schema without breaking existing users, old records, frontend assumptions, and payment/order flows is the real engineering problem.

### 2. Testing suite for high-risk marketplace flows

I built out tests around the highest-risk areas of the app: places where bugs could affect money, orders, inventory, supplier isolation, or user trust.

Test coverage areas included:

- checkout inventory validation,
- insufficient stock and out-of-stock cases,
- multi-supplier order splitting,
- supplier dashboard isolation,
- review flow consistency,
- Stripe/webhook behavior,
- auth API behavior,
- currency conversion and supplier payout currency,
- cart and product frontend behavior.

Representative private test files:

```text
insectflux-backend/tests/test_cart_service_inventory.py
insectflux-backend/tests/test_multi_supplier_orders.py
insectflux-backend/tests/test_reviews_e2e.py
insectflux-backend/tests/test_review_integration.py
insectflux-backend/tests/test_webhook_race_condition_fix.py
insectflux-backend/tests/integration/test_auth_api.py
insectflux-backend/tests/integration/test_currency_conversion_api.py
insectflux-backend/tests/unit/test_auth_service.py
insectflux-backend/tests/unit/test_product_service.py
insectflux-backend/tests/unit/test_stripe_checkout_currency.py
```

### 3. Webhook-driven messaging and payment reliability

Marketplace systems can fail in subtle ways when payment events, webhook retries, inventory updates, and user messaging all interact.

I worked on backend reliability around webhook processing and messaging-related flows, including:

- webhook event deduplication,
- payment session idempotency,
- distributed lock / race-condition prevention patterns,
- webhook monitoring endpoints,
- supplier/customer messaging flow support,
- message read/sent/delivered/failed states,
- unread counts and conversation APIs.

Representative private files:

```text
insectflux-backend/app/api/messages.py
insectflux-backend/app/models/message.py
insectflux-backend/app/schemas/message.py
insectflux-backend/app/services/notification_service.py
insectflux-backend/app/api/webhook_monitoring.py
insectflux-backend/app/services/webhook_idempotency_service.py
insectflux-backend/docs/WEBHOOK_RACE_CONDITION_FIX.md
insectflux-backend/tests/test_webhook_race_condition_fix.py
```

### 4. Backend hardening and production readiness

Beyond features, I worked on making critical backend flows safer to maintain and deploy.

Hardening themes:

- auth and validation paths,
- checkout/order reliability,
- supplier/customer isolation,
- payment/session handling,
- testable service logic,
- Docker/deployment-readiness,
- logging/monitoring-oriented design.

## Architecture Snapshot

```text
Frontend Marketplace UI
  |-- product/service browsing
  |-- cart and checkout
  |-- supplier/customer messaging
  |-- reviews
  v
FastAPI Backend
  |-- auth/user APIs
  |-- product/service APIs
  |-- order/checkout APIs
  |-- messaging APIs + websocket support
  |-- webhook monitoring APIs
  v
Services Layer
  |-- payment/webhook idempotency
  |-- notification service
  |-- inventory/order logic
  |-- migration/compatibility handling
  v
Data + External Services
  |-- Firebase/Firestore
  |-- Stripe
  |-- Cloudinary/media
  |-- Redis/locking/cache where configured
```

## What I learned

This project taught me that production engineering is mostly about protecting transitions and edge cases:

- schemas change,
- events retry,
- users double-click,
- payments race,
- inventory can oversell,
- old data survives longer than expected,
- tests matter most where the business can break.

It pushed me from "building features" toward thinking like a backend systems engineer.

## Interview summary

If asked to explain this project quickly:

> I was one of three engineers on InsectFlux, a marketplace platform. My strongest ownership areas were database migrations with forward/backward compatibility, the testing suite, webhook-driven messaging/payment reliability, and backend hardening. The most technical work involved making evolving marketplace data models safe, testing high-risk checkout/order/supplier flows, and preventing duplicate webhook/race-condition failures.

## Privacy / safety note

The source code and production data are private/team-owned. This case study avoids exposing secrets, customer/supplier data, private deployment details, or teammate-owned implementation details.
