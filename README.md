# 💰 Financial Logic Vulnerabilities

This repository contains real-world business logic vulnerabilities discovered during security testing of a travel booking platform.

These issues highlight how improper validation in financial workflows can lead to serious exploitation and monetary loss.

---

## 📂 Vulnerabilities Included

### 1️⃣ Price Tampering (Payment Manipulation)
📄 File: `price-tampering-payment-bypass.md`

A critical vulnerability where the application trusts client-side price values during payment processing.

💥 Impact:
- Pay arbitrary amounts (e.g., 1 AED)
- Direct financial loss
- High fraud risk

---

### 2️⃣ Payment Duration Mismatch
📄 File: `payment-duration-mismatch.md`

A business logic flaw allowing users to extend booking duration without increasing the price.

💥 Impact:
- Longer bookings for same price
- Revenue loss
- Broken pricing logic

---

## ⚠️ Common Root Causes

- Trusting client-side input
- Missing server-side validation
- Weak business logic enforcement

---

## 🛡️ Key Takeaways

- Never trust client-side values
- Always calculate sensitive data (price, duration) on the server
- Validate relationships between parameters (e.g., duration vs price)

---

## 📌 Notes

- All sensitive data (domains, tokens, IDs) have been sanitized
- This repository is for educational and security research purposes only

---

## 👨‍💻 Author

Hadi Metlej  
Cyber Security / Bug Bounty Researcher
