# Accounting Reports

**Who can access:** Accounting Officer, Admin, Super Admin (not Cashier)
**Where:** Accounting Portal → **Reports** in the sidebar

---

## Overview

The Reports section gives Accounting four standard reports modeled on the school's previous SIS:

| Report | What it answers |
|---|---|
| **Payment Summary** | "Who paid today (or in this date range)?" |
| **Account Receivables per Student** | "How much does each student still owe, broken down by fee category?" |
| **Daily Collection (per College)** | "How much did we collect each day, grouped by college?" |
| **Payment Summary Details** | "Per student, what did the payment categorize as — Tuition vs Modules vs Misc?" |

Every report supports **CSV export** and **Print** (browser print, opens in a clean A4 layout).

---

## Reports Hub

From the Accounting sidebar, click **Reports** to land at `/accounting/reports`. You'll see four cards — one per report. Click any card to open it.

---

## 1. Payment Summary

**Path:** Reports → Payment Summary
**URL:** `/accounting/reports/payments`

A list of payments in a date range. Columns:

| OR # | Date | Student | Type | Event | Cashier | Amount |
|---|---|---|---|---|---|---|

**Filters:**
- **From / To** — date range. Defaults to today.
- **Today** button — quick "just today".
- **Last 7 days** button — quick week view.
- **Show voided** checkbox — by default, voided OR transactions are hidden. Toggle to see them (strikethrough rows + VOIDED badge).

**Totals strip** at top: date range, payment count, total ₱ amount.

**Click-through from the dashboard:** the **Today's Collections** stat card on the Accounting Dashboard now links here with `?date=today` already applied. So "Who paid today?" is one click from the dashboard.

**Export CSV** — downloads `payment-summary-2026-05-12-to-2026-05-12.csv` (or your selected range) with the same columns. Opens in Excel.

**Print** — `Ctrl+P` / opens a printable view.

---

## 2. Account Receivables per Student

**Path:** Reports → Account Receivables per Student
**URL:** `/accounting/reports/receivables/students`

Per-student fee breakdown showing what each student has been assessed and what they've paid. **Grouped by Department → Program** with subtotals.

**Columns:**
- Student name + Student #
- **Tuition · Misc · Lab · NSTP · Insurance · Reco · Retreat · Others** (the standard ISHRM fee buckets)
- **Total** (sum of all fees)
- **Paid** (verified payments so far)
- **Balance** (still owed)
- Status (PAID / PARTIAL / PENDING / OVERDUE)

**Filters:**
- **Search** by student name or student #.
- **Status filter** — All / Paid / Partial / Pending / Overdue.

**Totals strip** at top: total students, total assessment, total paid, total balance.

This is the modern equivalent of the old SIS "Financial Accounts per Student" report (Reference Image #1 in the original feedback PDF). Use it to chase unpaid balances and to brief the school office on the receivables position.

---

## 3. Daily Collection (per College)

**Path:** Reports → Daily Collection (per College)
**URL:** `/accounting/reports/collections/by-college`

A pivot table: **rows are dates, columns are colleges**, cells show ₱ collected that day per college.

**Filters:**
- Date range (defaults to today; **Today** and **Last 30 days** quick buttons).

**Outputs:**
- Each cell shows ₱ amount, or `—` if there were no payments that day for that college.
- Per-date totals on the right (one row total per date).
- Per-college totals at the bottom.
- Grand total at the bottom-right.

This matches the old SIS "Daily Collection (per College)" layout (Reference Image #4 in the feedback PDF).

---

## 4. Payment Summary Details

**Path:** Reports → Payment Summary Details
**URL:** `/accounting/reports/payments/details`

Per-student rollup of payments by **fee category**:

| Student Name | Tuition / Other Fees | Modules / Booklet | Misc | Total |
|---|---|---|---|---|

**Filters:**
- Date range (defaults to today).

**How rollup works:**
- Every payment has an **Event Type** (Tuition / DCM / Foundation Week / Retreat / Modules / Booklet / Other / Admission Fee / Miscellaneous). Cashiers fill this when recording.
- Event types are grouped into 3 categories: `Tuition / Other Fees`, `Modules / Booklet`, `Misc`.
- This report sums each student's payments per category.

**Grand totals** row at the bottom summarizes across all students.

Matches the old SIS "Payment Summary Details" layout (Reference Image #4 second screenshot).

---

## Export, Print, and Currency

All reports use the same conventions:

- **Currency** — `₱X,XXX.XX` (Philippine Peso, comma thousands, two decimals).
- **Dates** — Asia/Manila timezone server-side. Display matches Manila time regardless of where you are.
- **CSV** — downloads with a `.csv` extension; filename includes the report name and date range.
- **Print** — uses the browser print dialog. The on-screen filter bar and Action buttons are automatically hidden in print.

---

## Voided Transactions

By default, **voided payments are excluded from all totals**. This keeps your daily/monthly/semester totals truthful — you don't want a wrong-OR-then-voided transaction to inflate the collection report.

To see voided transactions:
- **Payment Summary** — tick the **Show voided** filter.
- The voided rows render with strikethrough and a red `VOIDED` badge.
- Their amount is excluded from the totals strip.

---

## Permission

| Role | Sees Reports? |
|---|---|
| Accounting Officer | ✅ |
| Admin / Super Admin | ✅ |
| Cashier | ❌ — Cashier only sees their own daily totals on the Cashier dashboard |
| Registrar / Dean / Admission / Faculty / Student | ❌ |

---

## What's Coming

The old SIS had additional reports we have NOT built yet:

- Account Receivables per Program
- Account Receivables per Department
- Account Receivables per College
- Miscellaneous Fees (per College)
- Laboratory Fees (per College)
- Students with Discount
- Refund Information

These will roll out as needed. The four reports above were the ones explicitly red-boxed in the feedback PDF.
