# Magicline API Reference Skill

This skill helps Claude understand and work with the Magicline API ecosystem, which consists of three main APIs for fitness studio management.

## Overview

Magicline provides a comprehensive suite of APIs for managing fitness studios, including customer management, memberships, appointments, classes, financial operations, and device integrations.

## API Ecosystem

### 1. Magicline API (OpenAPI)
**Base URL (Demo):** `https://open-api-demo.open-api.magicline.com`
**Version:** 1.11.0
**Authentication:** API Key via `X-API-KEY` header

The main API for comprehensive studio management operations.

#### Core Functional Areas

**Customers**
- Customer CRUD operations (`/v1/customers`)
- Search customers by criteria
- Get customer by ID, card number, or other identifiers
- Manage customer contracts, benefits, and measurements
- Access mediums (cards, PINs, barcodes, wallet passes)
- Customer documents and profile images
- Access restrictions management
- Cross-studio customer operations (`/v1/cross-studio/customers`)

**Memberships**
- Get membership offers (`/v1/memberships/membership-offers`)
- Sign up new memberships (`/v1/memberships/signup`)
- Add memberships to existing customers
- Preview membership operations
- Switch memberships between offers
- Contract cancelation and amendments
- Idle periods management
- Additional modules (purchase, cancel, validate)

**Classes & Bookings**
- Get active classes (`/v1/classes`)
- Get class slots and availability
- Book class slots (`/v1/classes/booking/book`)
- Validate bookability
- Cancel bookings
- Get booking history per customer

**Appointments**
- Get bookable appointments (`/v1/appointments/bookable`)
- Get appointment slots
- Book appointments (`/v1/appointments/booking/book`)
- Validate appointment availability
- Delete appointments

**Trial Offers**
- Get trial offer configurations
- Create lead customers
- Book trial sessions (classes and appointments)
- Validate trial offer bookings
- Confirm trial bookings

**Finance & Payments**
- Customer account balance data
- Transaction history (past and upcoming)
- Book customer payments
- Update payment instruments
- Debt collection operations
- Tax advisor exports

**Studios**
- Get studio information (`/v1/studios/information`)
- Studio utilization (current capacity)
- Studio tags management
- Confirm contract activation

**Self-Service Operations**
- Customer self-service amendments:
  - Contact data
  - Address data
  - Master data
  - Payment data
- Membership self-service:
  - Contract cancelations
  - Idle periods (create, update, withdraw)
  - Additional modules purchase

**Communication**
- Create communication threads
- Get/update communication preferences
- Manage customer communications

**Employees**
- Get employees list
- Get employee by ID

**Devices**
- Get devices for a studio
- Activate devices

**Leads**
- Get lead configuration
- Validate lead data
- Create leads

**Checkin Vouchers**
- Redeem checkin vouchers

### 2. Magicline Connect API
**Base URL (Demo):** `https://connectdemo.api.magicline.com`
**Version:** 1.0.0

API for integrating Magicline into third-party websites and applications.

#### Core Functional Areas

**Contracts**
- List rate bundles (membership offers)
- Create customer and contract
- Get active contracts
- Cancel contracts (automatic or manual request)
- Get studio information

**Trial Sessions**
- Get bookable trial session slots
- Book trial sessions
- Get mandatory field configuration

**Credit Card Tokenization**
- Initiate tokenization (v2)
- Load payment methods (v2)
- Complete tokenization
- Get tokenization state

**Bank Account**
- Validate IBAN and lookup BIC
- Validate account holder name

**Studios**
- List all studios with filters
- Get studio details
- Get studio information
- Get communication settings
- Get utilization (public)
- Get SEPA agreement text
- Get legal information

**Contract Vouchers**
- Validate contract voucher
- Redeem contract voucher (Rate type only)

**Campaigns**
- List all active campaigns

**Referrals**
- List referrals by studio ID

**Leads**
- Create leads
- Get lead customer by UUID

**Promotions**
- Confirm customer participation

**Other Utilities**
- Get countries list (i18n)
- Get province information (Italy)
- Validate tax ID
- Generate pre-signed URL for image upload
- Get tenant information
- Check active features
- Get preview information

### 3. Device API
**Base URL (Demo):** `https://open-api-demo.devices.magicline.com`
**Authentication:** Bearer token (received from device activation)

API for device integrations (card readers, vending machines, time-based devices).

#### Device Types

**Access Control (Generic Card Reader)**
- Model: `GENERIC_CARD_READER`
- Check customer authorization
- Support for dry-run operations

**Vending Machines (Generic Vending)**
- Model: `GENERIC_VENDING_READER`
- Customer identification
- Product sales with dry-run support
- Top up consumption credit (revalue)

**Time-based Devices**
- Get available time intervals with prices
- Customer identification
- Benefit usage with dry-run support

## Common Patterns

### Authentication
All APIs use header-based authentication:
- **OpenAPI & Connect API:** `X-API-KEY: <your-api-key>`
- **Device API:** `Authorization: Bearer <token>`

### Error Responses
Standard error response structure across all APIs:
```json
{
  "errorMessage": "Resolved message in the context-specific default locale",
  "errorCode": "Key for translation files",
  "traceId": "Datadog trace id",
  "reference": "parent.child",
  "args": [],
  "typedArgs": []
}
```

Common HTTP status codes:
- `400` - Bad Request (validation errors)
- `401` - Unauthorized (authentication failed)
- `403` - Forbidden (insufficient permissions)
- `404` - Not Found
- `409` - Conflict (business logic conflict)
- `429` - Too Many Requests (rate limiting)
- `500` - Internal Server Error

### Data Formats
- **Dates:** ISO-8601 format (e.g., `2026-02-01`)
- **Date-times:** ISO-8601 with timezone (e.g., `2022-06-15T23:59:59.999+02:00[Europe/Berlin]`)
- **Languages:** Language code with optional country code (e.g., `de`, `de-DE`)
- **Phone numbers:** International format (e.g., `+49 30901820`)

### Common Enumerations
- **Gender:** `MALE`, `FEMALE`, `UNISEX`
- **Customer Status:** `MEMBER`, `PROSPECT`, `FORMER_MEMBER`
- **Access Medium Types:** `CARD_NUMBER`, `PIN`, `BARCODE`, `WALLET_PASS`
- **Communication Channels:** `LETTER`, `EMAIL`, `TEXT_MESSAGE`, `PHONE`, `FAX`, `CONVERSATION`, `CHAT`, `OTHER`
- **Message Categories:** `CONTRACT`, `GENERAL`, `APPOINTMENT`, `NEWSLETTER`, `LOYALTY_PROGRAM`

### Preview-then-Execute Pattern
Many operations support a preview mode:
1. Call preview endpoint (e.g., `/v1/memberships/signup/preview`)
2. Show user the impact/costs
3. Execute actual operation (e.g., `/v1/memberships/signup`)

### Dry-Run Pattern (Device API)
Device operations support dry-run:
1. Call with `dryRun: true` to validate
2. If successful, perform physical action (dispense product, enable access)
3. Call again with `dryRun: false` to commit transaction

## Reference Documentation Location

All detailed API documentation is located in:
```
/Users/luca/Projects/magiclineTools/skill/references/magicline/apis/magicline/
├── openapi/
│   └── openapi/
│       ├── appointments/
│       ├── classes/
│       ├── customers/
│       ├── customers-account/
│       ├── customers-communication/
│       ├── customers-self-service/
│       ├── devices/
│       ├── employees/
│       ├── finance/
│       ├── leads/
│       ├── memberships/
│       ├── membership-self-service/
│       ├── studios/
│       ├── trial-offers/
│       └── ...
├── connectapi/
│   └── connectapi/
│       ├── contracts/
│       ├── creditcard-tokenization/
│       ├── studios/
│       ├── trialsessions/
│       └── ...
└── deviceapi/
    └── deviceapi/
        ├── access/
        ├── vending/
        └── time/
```

## Usage Guidelines

### When working with Magicline API:

1. **Identify the right API:**
   - Use **OpenAPI** for comprehensive studio management and operations
   - Use **Connect API** for public-facing integrations (websites, apps)
   - Use **Device API** for hardware integrations

2. **Check authentication requirements:**
   - Ensure proper API key or bearer token is available
   - Check required scopes for the endpoint

3. **Reference detailed documentation:**
   - Navigate to the appropriate endpoint file in the references folder
   - Review request/response field specifications
   - Check for required vs optional parameters

4. **Follow common patterns:**
   - Use preview endpoints before executing financial transactions
   - Use dry-run mode for device operations
   - Handle pagination for list operations
   - Implement proper error handling for all status codes

5. **Consider data validation:**
   - Validate dates in ISO-8601 format
   - Ensure phone numbers are in international format
   - Check country-specific requirements (e.g., taxId for Spain/Italy)
   - Validate against enumerations where applicable

6. **Cross-studio operations:**
   - Use cross-studio endpoints when operating across multiple locations
   - Ensure partner integration is activated for cross-studio features

## Quick Reference: Key Endpoints

### Most Common Operations

**Get Customer Information**
```
GET /v1/customers/{customerId}
GET /v1/customers/by?email={email}
POST /v1/customers/search
```

**Create New Membership**
```
POST /v1/memberships/signup/preview (preview first)
POST /v1/memberships/signup (execute)
```

**Book a Class**
```
GET /v1/classes (list classes)
GET /v1/classes/{classId}/slots (get available slots)
POST /v1/classes/booking/validate (validate)
POST /v1/classes/booking/book (book)
```

**Manage Customer Contracts**
```
GET /v1/customers/{customerId}/contracts
POST /v1/memberships/{customerId}/self-service/ordinary-contract-cancelation
```

**Check Studio Utilization**
```
GET /v1/studios/utilization
GET /v1/studios/information
```

## Notes

- API documentation files are comprehensive and include all field definitions
- Demo environments are available for testing
- All date/time values should be timezone-aware
- Rate limiting applies (indicated by 429 responses)
- Some operations require specific country configurations (Italy, Spain, etc.)

## Developer Resources

- Full OpenAPI specifications available at:
  - https://redocly.sportalliance.com/_spec/apis/magicline/openapi/openapi.yaml
  - https://redocly.sportalliance.com/_spec/apis/magicline/connectapi/connectapi.yaml
  - https://redocly.sportalliance.com/_spec/apis/magicline/deviceapi/deviceapi.yaml
