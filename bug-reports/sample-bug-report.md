# Sample Bug Report

## BUG-001 – Customer Can Be Charged Twice When Clicking Pay Now Multiple Times

| **Field**   | **Details**                                                                   |
| ----------- | ----------------------------------------------------------------------------- |
| Bug ID      | BUG-001                                                                       |
| Title       | Customer can be charged twice when clicking the Pay Now button multiple times |
| Severity    | Critical                                                                      |
| Priority    | High                                                                          |
| Module      | Checkout / Payment                                                            |
| Environment | Web – Chrome                                                                  |
| Status      | Open                                                                          |
| Type        | Functional / Payment                                                          |

### Description

When a customer clicks the **Pay Now** button multiple times while the payment transaction is still processing, the system processes multiple payment requests. This can result in the customer being charged more than once for the same order.

### Preconditions

* Customer has a valid product in the cart.
* Customer is on the checkout page.
* Customer has entered valid payment details.
* Payment gateway is available.

### Steps to Reproduce

1. Add a product to the shopping cart.
2. Proceed to checkout.
3. Select Credit Card as the payment method.
4. Enter valid payment details.
5. Click **Pay Now**.
6. Immediately click **Pay Now** again before the first transaction finishes.
7. Check the payment transactions and order history.

### Expected Result

The system should process only **one payment transaction** for the order.

The **Pay Now** button should be disabled or otherwise prevent additional payment requests while the transaction is being processed.

Only one order and one successful payment transaction should be created.

### Actual Result

Multiple payment requests are processed when the customer clicks **Pay Now** multiple times.

The customer may be charged twice for the same order, resulting in duplicate payment transactions.

### Impact

This may result in:

* Customer being charged multiple times.
* Duplicate payment transactions.
* Duplicate orders or inconsistent order status.
* Customer complaints and refund requests.
* Potential financial loss and reputational impact.

### Recommendation

Implement duplicate-submission protection by disabling the **Pay Now** button after the initial submission and ensuring that the backend handles duplicate payment requests using transaction validation or idempotency controls.
