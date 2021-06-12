# Schemas

## Message Types

This is a central location where the message schemas will be located. The microservices will respect all of these.

### Order Received Event

Define an event schema representing when an order has been received.

```json
{
  "event_name": "OrderReceived",
  "event_id": "00000000-0000-0000-0000-000000000000"
}
```

### Order Confirmed Event

Define an event schema representing when an order has been confirmed (is not a duplicate order and can be processed).

```json
{
  "event_name": "OrderConfirmed",
  "event_id": "00000000-0000-0000-0000-000000000000"
}
```

### Order Prepared Event

Define an event schema representing when an order has been picked from within a warehouse and packed (ready to be shipped).

```json
{
  "event_name": "OrderPrepared",
  "event_id": "00000000-0000-0000-0000-000000000000"
}
```

### Notification Event

```json
{
  "event_name": "Notification",
  "notification_type": "sms|email|push",
  "notification_data": {}, // schema specific for platform
  "notification_event": "OrderReceived|OrderShipped", // prevent double sending
  "event_id": "00000000-0000-0000-0000-000000000000"
}
```

### Error Event

```json
{
  "event_name": "EventError",
  "event": {}, // full json event
  "error_details": {}, // stacktrace, logging, etc
  "event_id": "00000000-0000-0000-0000-000000000000"
}
```

## Topics

This is where the kafka topics and why they exist are defined. All are prefixed with `app.`.

`order.received | order.confirmed | order.prepared | notification | error`
