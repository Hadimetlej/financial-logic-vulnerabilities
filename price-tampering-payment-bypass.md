# 💸 Price Tampering Leading to Financial Loss (Payment Manipulation)

## 📌 Overview
During a security assessment of a booking/payment flow, I identified a critical business logic vulnerability that allowed manipulation of transaction prices.

By intercepting a payment request and modifying the `price` parameter, it was possible to complete a valid transaction for a significantly reduced amount.

---

## 🧪 Vulnerability Type
- Business Logic Flaw
- Price Manipulation
- Lack of Server-Side Validation

---

## ⚙️ Affected Component
- Booking / Payment Flow
- Endpoint: `/booking/process_payment`

---

## 🔍 Technical Details

The application sends a POST request during checkout containing a JSON body similar to:

```json
{
  "items": [
    {
      "price": 113.65,
      "type": "transportation"
    }
  ]
}
```

The server trusts the client-supplied price without validation.

---

## 🚨 Exploitation Steps

1. Intercept the payment request using Burp Suite
2. Locate the JSON parameter:
   items[].price
3. Modify the value to:
   "price": 1
4. Forward the request
5. Complete payment via gateway

---

## 💥 Impact

- Direct financial loss
- Ability to pay arbitrary amounts (e.g., 1 AED)
- High fraud risk
- Potential automation for mass exploitation

---

## 🔐 Root Cause

- No server-side validation of price
- Trusting client input
- Lack of integrity checks

---

## 🛡️ Recommended Fix

- Validate price server-side using trusted data source
- Ignore client-supplied price values
- Implement signed requests or server-calculated totals
- Add transaction verification before payment processing

---

## 🧠 Lessons Learned

- Never trust client-side values
- Business logic vulnerabilities can be more critical than technical ones
- Payment flows require strict validation and integrity checks

---

## 🏁 Conclusion

This vulnerability demonstrates how improper validation in financial workflows can lead to real monetary loss and exploitation at scale.
