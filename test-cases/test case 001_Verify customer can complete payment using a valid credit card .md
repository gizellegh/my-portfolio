

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
