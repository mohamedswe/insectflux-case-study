# InsectFlux Public-Safe Architecture Notes

## System shape

InsectFlux is best explained as a marketplace backend with critical reliability concerns around data evolution, checkout/order state, supplier/customer communication, and webhook/payment events.

## Public-safe diagram

```text
[Marketplace Frontend]
    |
    | product browsing, cart, checkout, messaging, reviews
    v
[FastAPI Backend]
    |
    | auth, products/services, orders, messaging, webhook monitoring
    v
[Service Layer]
    |
    | idempotency, notifications, inventory/order rules, compatibility handling
    v
[Data + External Services]
    |
    | Firestore/Firebase, Stripe, Cloudinary, Redis/cache/locks
```

## Reliability themes to mention publicly

- Migration safety: old and new data shapes needed compatibility handling.
- Test safety: tests focused on checkout, inventory, supplier isolation, reviews, auth, currency, Stripe/webhooks.
- Webhook safety: idempotency, deduplication, race-condition prevention.
- Marketplace safety: order and supplier/customer flows needed regression protection.

## Do not publish

- private source code snippets unless explicitly approved,
- `.env` values,
- API keys,
- Stripe/Firebase/Cloudinary credentials,
- real customer/supplier/order data,
- internal deployment URLs,
- teammate-specific code ownership claims not verified.
