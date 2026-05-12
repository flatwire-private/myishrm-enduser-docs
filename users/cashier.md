# Cashier Guide

**Role:** Cashier
**Primary Responsibility:** Record student payments and print Official Receipts (ORs)

---

## Overview

As a Cashier, you are at the cash window taking payments from students and printing ORs. The MyISHRM Cashier portal gives you a focused, distraction-free screen for just this job. You do **not** see receivables, reports, or other accounting screens — those are for the Accounting Officer.

Your daily tasks:
- Record a student payment (Payment of Fees)
- Print the Official Receipt
- Look up a previous OR transaction
- Void a wrong transaction (with reason)

---

## Login

1. Go to [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
2. Enter your cashier credentials
3. You land on the **Cashier Dashboard**

**Test credentials:**
```
Email:    cashier@ishrm.edu.ph
Password: cashiercashier
```

---

## Dashboard

The Cashier Dashboard shows:
- **Today's Collections (Yours)** — total of your recorded payments today
- **Voided (Today)** — count of voided transactions today
- **Quick Actions** — shortcuts to Payment of Fees and OR Transactions
- **Today's Transactions** — list of OR #s you recorded today (newest first)

The voided count is for your awareness; voided transactions appear with a strikethrough.

---

## Recording a Payment (Payment of Fees)

This is your main work surface. Follow these steps:

### Step 1 — Look up the student

1. Click **Payment of Fees** in the sidebar.
2. In the **Student Lookup** field, type the **Student #** (e.g. `2026-1-0106`) or the student's **Name** (last name first works best).
3. Click the matching student from the suggestion list.

The screen now shows the student's name, program, year level, and current academic year.

### Step 2 — Review the Breakdown of Fees

The left panel shows the student's current fee assessment:
- Tuition Fee
- Miscellaneous
- Laboratory
- Other Fees (Insurance, NSTP, Recollection, Retreat, etc.)
- **TOTAL FEES** (assessed amount)
- **AMOUNT PAID** (already paid)
- **BALANCE** (what's still owed)

If you see a balance, the right panel pre-fills that amount in the Payment Input — but you can change it for partial or overpayment.

### Step 3 — Fill the Payment Input

| Field | What to enter |
|---|---|
| **OR Number** | The Official Receipt number from your OR booklet. Must be unique across the whole system. |
| **Date** | Defaults to today. You can backdate within the semester if entering a late OR. |
| **Amount (₱)** | The amount paid. If it exceeds the balance, the system will ask you to confirm overpayment. |
| **Payment Type** | Cash · Check · Bank Transfer · Credit Card · Debit Card · Online |
| **Event Type** | **Required** — what the payment is for: Tuition / Modules / Booklet / DCM / Foundation Week / Retreat / Admission Fee / Other Fees / Miscellaneous. This is how Accounting categorizes payments in reports. |
| **Remarks** | Optional notes (200 chars max). |

### Step 4 — Record + Print

1. Click **Record Payment**.
2. A receipt window pops up showing the OR #, student, amount, event type, your name as cashier.
3. Click **Print Receipt** → opens a printable window. Print, hand the OR to the student.
4. The form clears and refocuses on Student Lookup, ready for the next student.

> **Important:** the school's pre-printed OR booklet is the source of truth for OR numbers. Always type the OR # from the booklet — the system does not generate one for you.

---

## Looking Up a Previous Transaction (OR Transactions)

A student returns with a question about a receipt, or you need to reprint or void.

1. Click **OR Transactions** in the sidebar.
2. Enter the OR # in the **Find by OR Number** field.
3. Click **Find**.

You'll see the transaction details: date, type, event, amount, and a **Voided** badge if it was already voided.

---

## Voiding a Wrong OR Transaction

If you made a mistake (wrong amount, wrong student, wrong OR #):

1. Find the transaction via **OR Transactions**.
2. Click **Void Transaction**.
3. Enter the reason (minimum 5 characters — be specific: *"Wrong amount entered. Should be ₱17,800 not ₱18,800."*).
4. Click **Submit Void**.

**What happens next depends on timing:**

| Scenario | Result |
|---|---|
| You recorded the OR yourself within the last **30 minutes** | Void applies immediately. Student account balance reverses. |
| You recorded it more than 30 minutes ago, OR another cashier recorded it | The system submits a **void request** to the Accounting Manager for approval. The payment stays active until they approve. |

You'll see a confirmation message at the top of the page telling you which path applied.

> **After a void is approved (immediate or after approval):** mark the OR booklet entry as **VOID** by hand. The system can't enforce this; it's part of your physical reconciliation.

---

## Reprinting a Receipt

If a student loses their receipt, look up the OR # in **OR Transactions** and click **Print** (when available on the lookup result). The reprinted receipt is marked **DUPLICATE** so it can't be used to claim double payment.

---

## What You Can NOT Do

By design, the Cashier role does **not** have access to:
- Account Receivables reports (students with outstanding balances)
- Daily Collection report across all cashiers
- Tuition fee configuration
- Approving void requests for other cashiers
- Editing past payments (only void with reason)

If you need these, the Accounting Officer has them.

---

## Common Issues

### "OR number XXXXX already exists"

The OR # you typed is already in the system. Either:
- You typed the wrong number — check the OR booklet again.
- You already recorded this OR — look it up under **OR Transactions** to confirm.

### "Payment exceeds outstanding balance by ₱X. Continue anyway?"

The student is paying more than they currently owe. Confirm with them, then click Continue. The overpayment becomes a credit on their account.

### "A void request for this payment is already pending review"

Someone (you or another cashier) already submitted a void request for this OR. It's waiting for the Accounting Manager. No need to submit again.

### Student wants their OR but I haven't printed it yet

Just record the payment with the OR # from the booklet, then click **Print Receipt** in the popup. The OR booklet entry is your record; the printed receipt is the student's copy.

---

## End of Shift

Before logging off:
1. Reconcile your OR booklet against the **Today's Transactions** list on your dashboard. Every OR you wrote should be in the list (or marked VOIDED with a reason).
2. Hand the OR booklet + cash drawer to the Accounting Officer per the school's standard end-of-day procedure.

---

## Need Help?

- For technical issues (page won't load, can't log in), contact IT Support.
- For permission to do something this guide doesn't cover, ask the Accounting Officer (Ma'am Eza) — she can do it on your behalf if it's legitimately outside the cashier scope.
