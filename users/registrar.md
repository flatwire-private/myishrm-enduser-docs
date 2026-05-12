# Registrar Guide

**Role:** Registrar
**Primary Responsibility:** Manage student records, enrollments, and official documents

---

## Overview

As a Registrar, you can:
- Convert approved applicants to students
- Manage student enrollments
- Process document requests
- Set grading deadlines
- Generate official documents (TOR, etc.)
- Close the semester through the Semester Closure workflow

---

## Login

1. Go to [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
2. Enter your registrar credentials
3. You'll see the Registrar Dashboard

---

## Dashboard Overview

Your dashboard shows:
- **Total Students** - Active student count
- **Pending Enrollments** - Enrollments awaiting approval
- **Document Requests** - Pending document requests
- **Grading Deadlines** - Current grading period settings

---

## Key Tasks

### Convert Applicants to Students

**When to Convert:**
- Applicant is approved by Admission
- Payment is verified by Accounting

**Steps:**
1. Click **"Applicants"** in the menu
2. Filter by "Ready for Conversion" (approved + payment verified)
3. Click on an applicant
4. Review applicant details and payment status
5. Click **"Convert to Student"**
6. Set:
   - Year Level (1st, 2nd, 3rd, or 4th year)
   - Initial Password (min 12 characters)
7. Click **"Convert"**

**Result:**
- Student ID is generated (e.g., 2026-00001)
- Student account is created
- Applicant status changes to "Enrolled"

---

### Manage Enrollments

**View All Enrollments:**
1. Click **"Enrollments"** in the menu
2. Filter by status: Pending, Approved, Rejected
3. Search by student name or ID

**Approve Enrollment:**
1. Click on a pending enrollment
2. Review student info and selected subjects
3. Click **"Approve"**

**Reject Enrollment:**
1. Click on a pending enrollment
2. Click **"Reject"**
3. Enter rejection reason (required)
4. Click **"Confirm Reject"**

---

### Create New Enrollment

**For Existing Students:**
1. Click **"Enrollments"** → **"New Enrollment"**
2. Search for student by name or ID
3. Select available course sections
4. Review total units (max 24 units/semester)
5. Click **"Create Enrollment"**

---

### Set Grading Deadlines

**Steps:**
1. Go to **Dashboard** → **Grading Deadlines** tab
2. Set dates for each period:
   - **Prelims**: Start date and deadline
   - **Midterm**: Start date and deadline
   - **Finals**: Start date and deadline
3. Click **"Save"**

**Note:** Faculty will see deadline warnings based on these dates.

---

### Process Document Requests

**Document Types:**
- Transcript of Records (TOR)
- Certificate of Enrollment (COE)
- Certificate of Grades (COG)
- Certificate of Graduation
- Good Moral Certificate

**Steps:**
1. Click **"Documents"** in the menu
2. View pending requests
3. Click on a request to review
4. Process based on status:
   - **Set Fee**: Click "Process" and set document fee
   - **Mark Ready**: After preparing, click "Ready for Pickup"
   - **Release**: When student picks up, click "Release"

**Generate TOR:**
1. Click on a TOR request
2. Click **"Generate TOR"**
3. Review the generated transcript
4. Print for the student

---

### Manage Students

**View Students:**
1. Click **"Students"** in the menu
2. Filter by: Status, Year Level
3. Search by name, ID, or email

**Edit Student:**
1. Click on a student
2. Click **"Edit"**
3. Update information:
   - Year Level
   - Section
   - Status (Active, Inactive, Graduated)
   - Guardian info
   - Medical conditions
4. Click **"Save"**

---

### View a Student's Academic History (with semester drill-down)

On a student's detail page, the **Academic History** tab shows one row per semester they've enrolled — year level, semester, **Academic Year**, units, standing.

**New: rows are clickable.** Click any semester row to expand an inline accordion showing the exact subjects enrolled in that semester:

| Code | Title | Units | Grade | Status |
|---|---|---|---|---|

Each expanded view also shows a footer with:
- Subject count and units earned (only subjects with grade ≤ 3.0 count)
- Semester GWA (weighted by units, only graded subjects counted)

Multiple semesters can be open at once — useful when comparing a student's standing across terms.

---

### View a Student's Permanent Record / Transcript

On a student's detail page, the **Grades Transcript** tab shows the official Permanent Record. Each **Year Level** has its own block (e.g. "1st Year · AY 2024-2025") containing the FIRST and SECOND Semester tables side by side.

**Academic Year is shown:**
- On the year-level header (e.g. "1st Year · AY 2024-2025" or, when the year stretched across two AYs, "1st Year · AY 2024-2025 — 2025-2026").
- On each semester sub-header (e.g. "FIRST Semester  AY 2024-2025").

**The Permanent Record is immutable.** When a student enrolls in a subject, the system captures the subject's code, title, and units at that moment as a permanent **snapshot** on the enrollment record. If the Curriculum Committee later renames a subject or changes its units, the student's historical transcript does **not** silently change. What they enrolled in is what their record shows.

> **Why this matters:** if a subject is renamed from "Mathematics in the Modern World" to "Discrete Math for Hospitality" later, a graduate's transcript still says "Mathematics in the Modern World" (the title that existed when they took it). This is correct behavior for an official record.

---

### Semester Closure

The Semester Closure workflow finalizes the academic semester — it consolidates clearance statuses from all departments before records are locked.

**When to use:** At the end of each semester, after all grades have been submitted and verified.

**Steps:**
1. Click **"Semester Closure"** in the menu
2. Select the academic year and semester to close
3. Review the clearance summary:
   - Students fully cleared (all departments)
   - Students with pending clearances
   - Students with conditional clearances
4. Coordinate with Dean and Accounting to resolve any outstanding clearances
5. Once all clearances are resolved, confirm the semester closure

**Clearance Types reviewed during closure:**
- Faculty clearance
- Accounting (financial) clearance
- Library clearance
- Dean's office clearance
- Registrar clearance
- Student Affairs clearance
- Property clearance

See [Clearances](features/clearances.md) for full details on the clearance system.

---

## Common Questions

**Q: Can I convert an applicant who hasn't paid?**
A: No. Payment must be verified by Accounting first.

**Q: How do I change a student's year level?**
A: Go to Students → Click student → Edit → Change year level.

**Q: What if a faculty misses the grading deadline?**
A: You can extend deadlines or manually allow late submissions.

**Q: How long does TOR generation take?**
A: TOR is generated instantly. Processing time is for review.

---

## Need Help?

- [Common Issues](common-issues.md)
- [Contact Support](contact-support.md)
