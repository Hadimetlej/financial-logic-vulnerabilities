# Payment Duration Mismatch Vulnerability

## 🧾 Description

A business logic vulnerability was discovered in the booking system where users can manipulate the booking duration (dates) without affecting the final payment amount.

The application fails to properly validate the relationship between:
- Booking duration (start & end dates)
- Total price calculation

This allows an attacker to book longer trips while paying for a shorter duration.

---

## 🎯 Impact

- Financial loss for the company
- Users can extend bookings without paying the correct amount
- Integrity of booking system is compromised

---

## 🛠️ Steps to Reproduce

1. Create a normal booking through the application
2. Intercept the request using Burp Suite
3. Modify booking dates (check_in / check_out)
4. Keep the same price
5. Forward the request

---

## 🧪 Proof of Concept

Modified request example:

{
  "check_in": "2026-01-20",
  "check_out": "2026-01-26",
  "price": "9737.50"
}

Result:
- Booking duration increased
- Price remains unchanged

---

## 🔍 Root Cause

The backend does not validate the relationship between booking duration and price.

---

## 🛡️ Recommendation

- Recalculate price on server-side
- Do not trust client-side input
- Validate booking duration vs price

---

## ⚠️ Severity

High
