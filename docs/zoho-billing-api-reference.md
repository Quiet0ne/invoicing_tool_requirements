# Zoho Billing API Reference Documentation

## Table of Contents
1. [Authentication](#authentication)
2. [Base URLs](#base-urls)
3. [Invoices](#invoices)
4. [Customers](#customers)
5. [Payments](#payments)
6. [Error Handling](#error-handling)
7. [Rate Limits](#rate-limits)

## Authentication

### OAuth 2.0 Authentication
- Client ID and Client Secret required
- Access Token generation process
- Token refresh mechanism
- Scopes and permissions

### API Token Authentication
- API token generation
- Token inclusion in requests
- Security best practices

## Base URLs

```
Production: https://www.zoho.com/billing/api/v1
Sandbox: https://sandbox.zoho.com/billing/api/v1
```

## Invoices

### Create Invoice
- Endpoint: `POST /invoices`
- Required fields:
  - customer_id
  - line_items
  - date
  - payment_terms
- Optional fields:
  - custom_fields
  - notes
  - terms
  - payment_options

### Retrieve Invoice
- Endpoint: `GET /invoices/{invoice_id}`
- Available fields:
  - invoice_number
  - reference_number
  - customer_details
  - line_items
  - total
  - balance
  - status

### Update Invoice
- Endpoint: `PUT /invoices/{invoice_id}`
- Modifiable fields:
  - line_items
  - notes
  - terms
  - custom_fields

### List Invoices
- Endpoint: `GET /invoices`
- Filter parameters:
  - date_range
  - status
  - customer_id
  - amount_range

## Customers

### Customer Operations
- Create customer: `POST /customers`
- Update customer: `PUT /customers/{customer_id}`
- List customers: `GET /customers`
- Delete customer: `DELETE /customers/{customer_id}`

### Customer Fields
- Required:
  - display_name
  - email
- Optional:
  - billing_address
  - shipping_address
  - custom_fields
  - payment_terms
  - currency_code

## Payments

### Record Payment
- Endpoint: `POST /invoices/{invoice_id}/payments`
- Required fields:
  - amount
  - payment_mode
  - date
- Optional fields:
  - reference_number
  - notes

### Payment Methods
- Online payment gateways
  - PayPal
  - Stripe
  - Authorize.net
- Offline payment methods
  - Bank transfer
  - Cash
  - Check

## Error Handling

### HTTP Status Codes
- 200: Success
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 429: Too Many Requests
- 500: Internal Server Error

### Error Response Format
```json
{
  "code": "ERROR_CODE",
  "message": "Error description",
  "details": {
    "field_name": "Specific error details"
  }
}
```

## Rate Limits

### API Limits
- Requests per minute: 100
- Requests per hour: 1000
- Burst limit: 25 requests per second

### Best Practices
- Implement exponential backoff
- Handle rate limit errors
- Monitor usage
- Cache responses when possible

## Webhooks

### Available Events
- invoice.created
- invoice.updated
- payment.received
- customer.created
- customer.updated

### Webhook Setup
- Endpoint configuration
- Security verification
- Retry mechanisms
- Response handling

## Testing

### Sandbox Environment
- Test credentials
- Test data
- Limitations
- Differences from production

### Test Cards
- Test card numbers
- Test scenarios
- Validation rules
- Error simulation