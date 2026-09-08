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


