# CheckMailPro - Block Fake/Temp emails

A tool designed to detect temporary or disposable email addresses and block them, effectively preventing spammers and fake account signups

# Secure Email Validation API Documentation

## Overview

The Secure Email Validation API enables you to verify whether an email address is disposable or valid through a simple POST request.

**Base URL**

```arduino
https://api.checkmailpro.com/
```

## Authentication

To access the API, include your `access_key` and `secret_key` in the request body. Ensure these keys are kept confidential to prevent unauthorized access.

## Endpoint: Secure Validator

### URL

```sql
/api/v1/check/secure_validator/
```

### Method

`POST`

### Headers

- `Content-Type: application/json`: Indicates that the request body is in JSON format.

### Request Body Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | String | Yes | The email address to validate. |
| `access_key` | String | Yes | Your unique access key for authentication. |
| `secret_key` | String | Yes | Your unique secret key for secure access. |

### Example Request

```bash
curl -X 'POST' 'https://api.checkmailpro.com/api/v1/check/secure_validator/' 
-H 'accept: application/json' 
-H 'X-Access-Key: your_access_key' 
-H 'X-Secret-Key: your_secret_key' 
-H 'Content-Type: application/json' 
-d '{
"email": "user@example.com"
}'

```

Response

The API returns a JSON object with the validation result.

### Successful Response

```json
{
   "Result": {
    "input": "user@example.com",
    "is_disposable": true,
    "public_domain": false,
    "mx": false
}
 }
```

### Error Response

```json
{
    "error": "Invalid API keys"
}

```

### Response Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| `status` | String | Indicates whether the request was successful or not. |
| `email` | String | The email address that was validated. |
| `is_disposable` | Boolean | Indicates if the email is disposable (`true` or `false`). |
| `MX Records` | Boolean | Provides additional information about the result. |

---

## Rate Limiting

To ensure fair usage, the API enforces rate limits:

- **Free Plan**: 1,000 requests per month.
- **Pro Plan**: 350,000 requests per month.

Exceeding these limits will result in a `429 Too Many Requests` response.

---

## Error Codes

The API may return the following HTTP status codes:

- `200 OK`: The request was successful.
- `400 Bad Request`: The request was malformed or missing required parameters.
- `401 Unauthorized`: Authentication failed due to invalid `access_key` or `secret_key`.
- `429 Too Many Requests`: Rate limit exceeded.
- `500 Internal Server Error`: An unexpected error occurred on the server.

---

## Notes

- Ensure your `access_key` and `secret_key` are kept confidential.
- Use the appropriate HTTP status codes to handle responses effectively.
- For bulk email validations or higher rate limits, consider upgrading to a higher plan.

---

## Contact

For support or inquiries, please contact [support@checkmailpro.com.](https://www.notion.so/CheckMailPro-Block-Fake-Temp-emails-163e6df249b5808a8c3af90a47b3b4e9?pvs=21)

**How users can generate their keys on the website:**

1. Visit checkmailpro.com and log in.
2. Select a plan based on your requirements.
3. An API key will be automatically generated under the "My APIs" tab – Access Key and Secret Key.
4. Replace `access_key` and `secret_key` in Postman with your generated keys.
