# Database Schema (PostgreSQL)

## Core Entities

### sites
- id (uuid, pk)
- name
- address
- timezone
- status
- created_at

### zones
- id (uuid, pk)
- site_id (fk -> sites)
- name
- level
- capacity

### devices
- id (uuid, pk)
- site_id (fk -> sites)
- device_type (kiosk, pos, barrier, lpr, rfid)
- identifier
- status
- last_seen_at

### users
- id (uuid, pk)
- email
- phone
- password_hash
- role (admin, manager, cashier, customer)
- status
- created_at

### vehicles
- id (uuid, pk)
- user_id (fk -> users, nullable)
- plate_number
- vehicle_type

### sessions
- id (uuid, pk)
- session_code (unique)
- site_id (fk -> sites)
- zone_id (fk -> zones)
- vehicle_id (fk -> vehicles)
- entry_at
- exit_at (nullable)
- status (active, paid, exited, void)
- entry_method (lpr, qr, rfid, manual)
- entry_snapshot_url (nullable)
- created_by (fk -> users)

### rates
- id (uuid, pk)
- site_id (fk -> sites)
- vehicle_type
- rate_type (flat, hourly, overnight)
- grace_minutes
- amount
- effective_from
- effective_to

### payments
- id (uuid, pk)
- session_id (fk -> sessions)
- method (cash, qr, card, wallet, app)
- amount
- currency
- status (pending, paid, failed)
- receipt_number
- paid_at

### validations
- id (uuid, pk)
- session_id (fk -> sessions)
- validation_type (mall, hotel, office)
- discount_amount
- notes

### bookings
- id (uuid, pk)
- user_id (fk -> users)
- site_id (fk -> sites)
- vehicle_id (fk -> vehicles)
- entry_at
- duration_minutes
- status (reserved, active, completed, cancelled)
- qr_pass
- created_at

### audit_logs
- id (uuid, pk)
- actor_id (fk -> users)
- action
- entity_type
- entity_id
- metadata (jsonb)
- created_at

## Relationships
- sites 1..n zones
- sites 1..n devices
- users 1..n vehicles
- vehicles 1..n sessions
- sessions 1..n payments
- sessions 0..n validations
- users 1..n bookings
