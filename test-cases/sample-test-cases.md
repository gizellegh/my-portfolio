

## Test Case 001 – Successful Payment with Valid Card

| **Field**     | **Details**                                                    |
| ------------- | -------------------------------------------------------------- |
| Test Case ID  | TC-001                                                         |
| Title         | Verify customer can complete payment using a valid credit card |
| Priority      | High                                                           |
| Preconditions | Customer has products in the cart and is ready to checkout     |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Enter a valid card number.
4. Enter a valid cardholder name.
5. Enter a valid expiry date.
6. Enter a valid CVV.
7. Click **Pay Now**.

### Expected Result

Payment should be successfully processed. The customer should be redirected to the order confirmation page, and the order status should be updated to **Paid/Confirmed**.

### Test Data

Card Number: `4111 1111 1111 1111`
Cardholder Name: `Test User`
Expiry Date: `12/30`
CVV: `123`

---

## Test Case 002 – Payment with Invalid Card Number

| **Field**     | **Details**                                                       |
| ------------- | ----------------------------------------------------------------- |
| Test Case ID  | TC-002                                                            |
| Title         | Verify payment is rejected when an invalid card number is entered |
| Priority      | High                                                              |
| Preconditions | Customer has products in the cart and is ready to checkout        |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Enter an invalid card number.
4. Enter a valid cardholder name.
5. Enter a valid expiry date.
6. Enter a valid CVV.
7. Click **Pay Now**.

### Expected Result

The payment should not be processed. The system should display an appropriate validation or error message indicating that the card number is invalid.

### Test Data

Card Number: `1234 5678 9012 3456`
Cardholder Name: `Test User`
Expiry Date: `12/30`
CVV: `123`

---

## Test Case 003 – Payment with Expired Card

| **Field**     | **Details**                                                |
| ------------- | ---------------------------------------------------------- |
| Test Case ID  | TC-003                                                     |
| Title         | Verify payment is rejected when an expired card is used    |
| Priority      | High                                                       |
| Preconditions | Customer has products in the cart and is ready to checkout |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Enter a valid card number.
4. Enter a valid cardholder name.
5. Enter an expired expiry date.
6. Enter a valid CVV.
7. Click **Pay Now**.

### Expected Result

The payment should be declined, and the customer should receive an appropriate error message indicating that the card has expired.

### Test Data

Card Number: `4111 1111 1111 1111`
Cardholder Name: `Test User`
Expiry Date: `01/22`
CVV: `123`

---

## Test Case 004 – Payment with Invalid CVV

| **Field**     | **Details**                                                 |
| ------------- | ----------------------------------------------------------- |
| Test Case ID  | TC-004                                                      |
| Title         | Verify payment is rejected when an incorrect CVV is entered |
| Priority      | High                                                        |
| Preconditions | Customer has products in the cart and is ready to checkout  |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Enter a valid card number.
4. Enter a valid cardholder name.
5. Enter a valid expiry date.
6. Enter an incorrect CVV.
7. Click **Pay Now**.

### Expected Result

The payment should not be completed. The system should display an appropriate error message for the invalid CVV.

### Test Data

Card Number: `4111 1111 1111 1111`
Cardholder Name: `Test User`
Expiry Date: `12/30`
CVV: `999`

---

## Test Case 005 – Payment with Missing Required Fields

| **Field**     | **Details**                                                          |
| ------------- | -------------------------------------------------------------------- |
| Test Case ID  | TC-005                                                               |
| Title         | Verify payment cannot proceed when required payment fields are empty |
| Priority      | Medium                                                               |
| Preconditions | Customer has products in the cart and is ready to checkout           |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Leave the card number field empty.
4. Leave the cardholder name field empty.
5. Leave the expiry date field empty.
6. Leave the CVV field empty.
7. Click **Pay Now**.

### Expected Result

Payment should not be processed. Required-field validation messages should be displayed for the missing payment information.

### Test Data

Card Number: `Blank`
Cardholder Name: `Blank`
Expiry Date: `Blank`
CVV: `Blank`

---

## Test Case 006 – Payment with Insufficient Balance

| **Field**     | **Details**                                                                       |
| ------------- | --------------------------------------------------------------------------------- |
| Test Case ID  | TC-006                                                                            |
| Title         | Verify payment is declined when the card has insufficient funds                   |
| Priority      | High                                                                              |
| Preconditions | Customer has products in the cart and the card has insufficient available balance |

### Steps

1. Open the checkout page.
2. Select Credit Card as the payment method.
3. Enter valid payment details.
4. Click **Pay Now**.

### Expected Result

The payment should be declined. The customer should receive an appropriate payment failure message, and the order should not be marked as paid.

### Test Data

Card Number: `Valid test card with insufficient funds`
Cardholder Name: `Test User`
Expiry Date: `12/30`
CVV: `123`

---

## Test Case 007 – Prevent Duplicate Payment

| **Field**     | **Details**                                                                 |
| ------------- | --------------------------------------------------------------------------- |
| Test Case ID  | TC-007                                                                      |
| Title         | Verify customer is not charged twice when Pay Now is clicked multiple times |
| Priority      | Critical                                                                    |
| Preconditions | Customer has a valid order and valid payment details                        |

### Steps

1. Open the checkout page.
2. Enter valid payment details.
3. Click **Pay Now**.
4. Immediately click **Pay Now** again while the first transaction is processing.
5. Check the payment transaction and order history.

### Expected Result

Only one payment transaction should be processed. The customer should not be charged twice, and only one order should be created.

### Test Data

Card Number: `Valid test card`
Cardholder Name: `Test User`
Expiry Date: `12/30`
CVV: `123`

---

## Test Case 008 – Payment Gateway Timeout

| **Field**     | **Details**                                                                |
| ------------- | -------------------------------------------------------------------------- |
| Test Case ID  | TC-008                                                                     |
| Title         | Verify system handles payment gateway timeout properly                     |
| Priority      | High                                                                       |
| Preconditions | Customer has a valid order and payment gateway is unavailable or times out |

### Steps

1. Open the checkout page.
2. Enter valid payment details.
3. Click **Pay Now**.
4. Simulate or wait for a payment gateway timeout.

### Expected Result

The customer should receive an appropriate error or timeout message. The order should not incorrectly be marked as paid, and the customer should have an option to retry the payment when applicable.

### Test Data

Payment Method: `Credit Card`
Gateway Status: `Timeout`
