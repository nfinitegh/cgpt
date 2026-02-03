# UI/UX Wireframes (Text)

## Kiosk & POS Application

### Entry Module (Kiosk)
```
+--------------------------------------------------+
| Parking Entry                                    |
|--------------------------------------------------|
| [ Camera Preview / LPR ]                         |
|                                                  |
| Plate: [ ABC1234________ ]  (Manual Input)       |
| Vehicle Type: (Car ▾)  Zone/Level: (B2 ▾)        |
|--------------------------------------------------|
| QR Scan  | RFID/NFC  | Ticket Print              |
|--------------------------------------------------|
| Slots Available: 128   Rate: PHP 40/hr           |
|--------------------------------------------------|
| [ Start Session ]                                |
+--------------------------------------------------+
```

### Payment Module (POS)
```
+--------------------------------------------------+
| Payment                                          |
|--------------------------------------------------|
| Session ID: PM-2025-000123                       |
| Plate: ABC1234      Entry: 10:02 AM              |
| Duration: 2h 35m    Rate: PHP 40/hr              |
| Grace: 15m          Total: PHP 120               |
|--------------------------------------------------|
| Discounts: [Senior ▾]  Validations: [Mall ▾]     |
|--------------------------------------------------|
| Pay With:  Cash | QR | Card | Wallet | App       |
|--------------------------------------------------|
| [ Collect Payment ]   [ Print Receipt ]          |
| [ Generate Exit QR ]                             |
+--------------------------------------------------+
```

### Exit Module (Kiosk)
```
+--------------------------------------------------+
| Exit Validation                                  |
|--------------------------------------------------|
| [ QR Scanner ]   [ LPR Preview ]                 |
|                                                  |
| Plate: ABC1234  Paid: Yes  Exit Window: 10m      |
|--------------------------------------------------|
| Status: Valid                                    |
|--------------------------------------------------|
| [ Open Barrier ]                                 |
+--------------------------------------------------+
```

### Cashier Dashboard
```
+--------------------------------------------------+
| Cashier Dashboard (Shift: 08:00-16:00)           |
|--------------------------------------------------|
| Active Sessions | Pending Payments | Lost Ticket |
|--------------------------------------------------|
| #  Plate     Entry      Duration   Amount Due   |
| 1  ABC1234   10:02 AM   2h 35m     PHP 120       |
| 2  XYZ9999   09:15 AM   3h 22m     PHP 160       |
|--------------------------------------------------|
| [ Manual Entry ] [ Manual Exit ] [ Reprint ]     |
| [ X-reading ] [ Z-reading ] [ Reconcile ]        |
+--------------------------------------------------+
```

## Consumer Mobile App

### Home / Discovery
```
+-------------------------------+
| Search Parking                |
| [ Map View ]  [ List View ]   |
|-------------------------------|
| • Mega Mall (120 slots)       |
|   Rate: PHP 40/hr             |
|   [ Book ] [ Directions ]     |
|-------------------------------|
| • Airport T3 (60 slots)       |
|   Rate: PHP 60/hr             |
|   [ Book ] [ Directions ]     |
+-------------------------------+
```

### Booking Flow
```
+-------------------------------+
| Booking Details               |
|-------------------------------|
| Location: Mega Mall           |
| Entry Time: [ 10:30 AM ▾ ]     |
| Duration: [ 3 hours ▾ ]        |
| Vehicle: [ SUV ▾ ]             |
| Payment: [ GCash ▾ ]           |
|-------------------------------|
| [ Confirm & Pay ]              |
+-------------------------------+
```

### Active Session
```
+-------------------------------+
| Active Session                |
|-------------------------------|
| Plate: ABC1234                |
| Slot: B2-014                  |
| Time Remaining: 1h 10m        |
| Exit QR: [ Tap to Enlarge ]   |
|-------------------------------|
| [ Extend Time ]  [ Pay Now ]  |
+-------------------------------+
```
