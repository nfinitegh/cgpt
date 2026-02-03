# Source Code Structure

```
parking-platform/
├── apps/
│   ├── kiosk-pos-android/         # Android app for kiosks & POS
│   │   ├── app/
│   │   ├── shared-ui/
│   │   └── hardware-connectors/
│   ├── mobile-app/                # Flutter/React Native consumer app
│   │   ├── lib/
│   │   ├── assets/
│   │   └── test/
│   └── admin-dashboard/           # Web admin dashboard
│       ├── src/
│       └── public/
├── services/
│   ├── api-gateway/               # API gateway + auth
│   ├── parking-service/           # sessions, entry/exit
│   ├── billing-service/           # rates, payments, discounts
│   ├── booking-service/           # mobile reservations
│   ├── device-service/            # device health, commands
│   └── reporting-service/         # analytics
├── infra/
│   ├── terraform/                 # cloud infra
│   ├── helm/                      # Kubernetes charts
│   └── scripts/
├── shared/
│   ├── sdk/                       # mobile/kiosk SDKs
│   ├── protobuf/                  # event schemas
│   └── ui-kit/
└── docs/
```

## Cross-Cutting Concerns
- Observability: OpenTelemetry + centralized logging.
- Security: JWT + RBAC + device certificates.
- Offline: local queue + sync service.
- Hardware: adapters per vendor (LPR, barrier, RFID).
