# API Testing – E-commerce Payment API

As part of my QA experience, I have worked with API testing to validate backend services and ensure that data is correctly processed between the application and its services.

For this sample project, I am using an **e-commerce payment API** to demonstrate how I would validate payment requests and responses. The scenarios include positive and negative test cases covering successful transactions, invalid payment details, missing fields, unauthorized requests, duplicate transactions, and response validation.

The objective is to ensure that the API handles valid and invalid requests correctly, returns the appropriate HTTP status codes and response messages, and maintains data integrity throughout the payment process.

# Sample API Test Cases

## API Test Case 001 – Successful Payment

| **Field**     | **Details**                                                       |
| ------------- | ----------------------------------------------------------------- |
| Test Case ID  | API-TC-001                                                        |
| Title         | Verify payment API successfully processes a valid payment request |
| Method        | POST                                                              |
| Endpoint      | `/api/payments`                                                   |
| Priority      | Critical                                                          |
| Preconditions | Valid order and payment test data are available                   |

### Request

```json
{
  "orderId": "ORD-10001",
  "amount": 1500.00,
  "currency": "PHP",
  "paymentMethod": "CARD"
}
```

### Steps

1. Open Postman.
2. Select the `POST` method.
3. Enter the payment endpoint.
4. Add the required authentication headers.
5. Add a valid payment request body.
6. Send the request.

### Expected Result

* API should return **HTTP 200 OK** or the expected successful status code.
* Payment status should be returned as `SUCCESS`.
* A unique transaction ID should be generated.
* The response should contain the correct order ID and payment amount.

---

## API Test Case 002 – Missing Required Field

| **Field**     | **Details**                                                  |
| ------------- | ------------------------------------------------------------ |
| Test Case ID  | API-TC-002                                                   |
| Title         | Verify payment API rejects a request with a missing order ID |
| Method        | POST                                                         |
| Endpoint      | `/api/payments`                                              |
| Priority      | High                                                         |
| Preconditions | API is available                                             |

### Request

```json
{
  "amount": 1500.00,
  "currency": "PHP",
  "paymentMethod": "CARD"
}
```

### Steps

1. Open Postman.
2. Select the `POST` method.
3. Enter the payment endpoint.
4. Add the required headers.
5. Send the request without the `orderId` field.

### Expected Result

API should reject the request and return an appropriate **4xx validation error**.

The response should clearly indicate that `orderId` is required.

---

## API Test Case 003 – Invalid Payment Amount

| **Field**     | **Details**                                          |
| ------------- | ---------------------------------------------------- |
| Test Case ID  | API-TC-003                                           |
| Title         | Verify payment API rejects an invalid payment amount |
| Method        | POST                                                 |
| Endpoint      | `/api/payments`                                      |
| Priority      | High                                                 |
| Preconditions | API is available                                     |

### Request

```json
{
  "orderId": "ORD-10001",
  "amount": -100.00,
  "currency": "PHP",
  "paymentMethod": "CARD"
}
```

### Expected Result

API should reject the request with an appropriate **4xx status code**.

The payment transaction should not be created, and the response should indicate that the payment amount is invalid.

---

## API Test Case 004 – Unauthorized Payment Request

| **Field**     | **Details**                                                      |
| ------------- | ---------------------------------------------------------------- |
| Test Case ID  | API-TC-004                                                       |
| Title         | Verify payment API rejects requests without valid authentication |
| Method        | POST                                                             |
| Endpoint      | `/api/payments`                                                  |
| Priority      | Critical                                                         |
| Preconditions | API requires authentication                                      |

### Steps

1. Open Postman.
2. Select the `POST` method.
3. Enter the payment endpoint.
4. Remove or modify the authentication token.
5. Send a valid payment request.

### Expected Result

API should reject the request with **HTTP 401 Unauthorized** or the expected authentication error.

No payment transaction should be created.

---

## API Test Case 005 – Duplicate Payment Request

| **Field**     | **Details**                                                               |
| ------------- | ------------------------------------------------------------------------- |
| Test Case ID  | API-TC-005                                                                |
| Title         | Verify API prevents duplicate payment processing for the same transaction |
| Method        | POST                                                                      |
| Endpoint      | `/api/payments`                                                           |
| Priority      | Critical                                                                  |
| Preconditions | A valid payment request has already been processed                        |

### Steps

1. Send a valid payment request.
2. Capture the transaction or idempotency reference.
3. Send the same payment request again.
4. Compare the API responses and transaction records.

### Expected Result

The API should prevent duplicate payment processing.

The customer should not be charged twice, and the API should return the existing transaction or an appropriate duplicate-request response.

---

# API Response Validation

For each API test, I would also validate:

* HTTP status code
* Response time
* Response body
* Required response fields
* Data types
* Payment status
* Transaction ID
* Order ID
* Payment amount
* Error messages
* Authentication/authorization behavior
* Duplicate transaction handling
