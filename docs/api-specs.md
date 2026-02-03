# API Specifications (v1)

Base URL: `/api/v1`

## Auth
### POST /auth/login
Request:
```json
{ "email": "user@example.com", "password": "string" }
```
Response:
```json
{ "accessToken": "jwt", "refreshToken": "jwt", "user": { "id": "uuid", "role": "cashier" } }
```

### POST /auth/refresh
Request:
```json
{ "refreshToken": "jwt" }
```
Response:
```json
{ "accessToken": "jwt" }
```

## Sessions (Parking)
### POST /sessions
Create a parking session (entry event).
Request:
```json
{
  "plateNumber": "ABC1234",
  "entrySource": "kiosk",
  "zoneId": "uuid",
  "vehicleType": "car",
  "entryMethod": "lpr",
  "entrySnapshotUrl": "https://.../image.jpg"
}
```
Response:
```json
{
  "id": "uuid",
  "sessionCode": "PM-2025-000123",
  "entryAt": "2025-01-10T10:02:00Z",
  "status": "active"
}
```

### GET /sessions/{id}
Retrieve session by ID.

### GET /sessions?status=active&siteId=uuid
List sessions with filters.

### POST /sessions/{id}/adjust
Manual adjustment for cashier.
Request:
```json
{ "adjustmentType": "lost_ticket", "notes": "Manual override" }
```

## Payments
### POST /payments/quote
Calculate fees.
Request:
```json
{ "sessionId": "uuid", "at": "2025-01-10T12:30:00Z", "discounts": ["senior"] }
```
Response:
```json
{ "amount": 120, "currency": "PHP", "breakdown": { "durationMinutes": 155, "graceApplied": true } }
```

### POST /payments
Collect payment and mark session paid.
Request:
```json
{ "sessionId": "uuid", "method": "cash", "amount": 120, "currency": "PHP" }
```
Response:
```json
{ "paymentId": "uuid", "receiptNumber": "OR-2025-000221", "exitQr": "base64" }
```

## Exit Validation
### POST /exits/validate
Request:
```json
{ "sessionId": "uuid", "plateNumber": "ABC1234", "method": "qr" }
```
Response:
```json
{ "valid": true, "exitWindowMinutes": 10 }
```

### POST /exits/complete
Record exit.
Request:
```json
{ "sessionId": "uuid", "exitAt": "2025-01-10T12:40:00Z", "barrierOpened": true }
```

## Booking (Mobile)
### POST /bookings
Request:
```json
{
  "siteId": "uuid",
  "entryAt": "2025-01-10T10:30:00Z",
  "durationMinutes": 180,
  "vehicleType": "suv",
  "paymentMethod": "gcash"
}
```
Response:
```json
{ "bookingId": "uuid", "qrPass": "base64", "status": "confirmed" }
```

### GET /bookings/me
List authenticated user bookings.

## Admin
### GET /sites
### POST /sites
### GET /rates?siteId=uuid
### POST /rates
### GET /devices?siteId=uuid
### POST /devices

## Webhooks
### POST /webhooks/payments
External payment confirmation.

## Error Format
```json
{ "error": { "code": "invalid_request", "message": "Human readable message" } }
```
