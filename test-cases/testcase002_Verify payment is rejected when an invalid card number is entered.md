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

