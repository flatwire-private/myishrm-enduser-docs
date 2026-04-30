# MyISHRM Student Information System - Complete User Guide

**International School of Hospitality and Restaurant Management**
**Version 2.0** | Last Updated: November 20, 2025

---

## Table of Contents

1. [System Overview](#system-overview)
2. [Getting Started - Superadmin](#getting-started---superadmin)
3. [Staff Account Management](#staff-account-management)
4. [Academic Setup Workflow](#academic-setup-workflow)
5. [Applicant Admission & Payment Workflow](#applicant-admission--payment-workflow)
6. [Role-Specific Guides](#role-specific-guides)
7. [Support & Troubleshooting](#support--troubleshooting)

---

## System Overview

### What is MyISHRM?

MyISHRM is a comprehensive Student Information System (SIS) that manages the complete academic lifecycle of ISHRM, from applicant admission to student graduation.

**Key Modules:**
- 🎓 **Admission & Enrollment** - Application processing with payment verification
- 📚 **Academic Management** - Colleges, courses, subjects, and curriculum
- 👨‍🏫 **Faculty & Course Assignment** - Dean-managed course sections
- 💰 **Payments & Accounting** - Fee collection and verification
- 📊 **Grades & Records** - Student performance tracking
- 🔐 **User & Role Management** - Staff and student account control

### System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         MyISHRM Portal                           │
│                   https://myishrm.flatwire.io                    │
└─────────────────────────────────────────────────────────────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
              ┌─────▼──────┐          ┌──────▼──────┐
              │  Frontend  │          │   Backend   │
              │  (Next.js) │◄────────►│  (FastAPI)  │
              │  Port 3001 │          │  Port 8001  │
              └────────────┘          └──────┬──────┘
                                             │
                                      ┌──────▼───────┐
                                      │   Supabase   │
                                      │  PostgreSQL  │
                                      │   + Storage  │
                                      └──────────────┘
```

### User Roles Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│ 👑 ADMIN (Superadmin) - Full System Access                      │
│    ├─→ Create all staff accounts                                 │
│    ├─→ System configuration                                      │
│    └─→ Override all permissions                                  │
└─────────────────────────────────────────────────────────────────┘
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
┌───────▼────────┐ ┌─────▼──────┐ ┌───────▼────────┐
│ 🎓 DEAN        │ │ 📋 REGISTRAR│ │ 💰 ACCOUNTING  │
│  (Academic)    │ │  (Records)  │ │  (Financial)   │
└────────────────┘ └─────────────┘ └────────────────┘
        │                 │                 │
        ▼                 ▼                 ▼
  Manage Courses    Enrollment Mgmt   Payment Verify
  Assign Faculty    Student Records   Financial Reports
        │                 │                 │
        └─────────────────┼─────────────────┘
                          │
                ┌─────────┴─────────┐
                │                   │
         ┌──────▼───────┐   ┌──────▼──────┐
         │ 🎫 ADMISSION │   │ 👨‍🏫 FACULTY  │
         │  (Applicants)│   │  (Teaching) │
         └──────────────┘   └─────────────┘
                │                   │
                ▼                   ▼
         Review & Approve    Submit Grades
         Generate Invoices   Manage Classes
                │                   │
                └───────────────────┘
                          │
                    ┌─────▼──────┐
                    │ 🎓 STUDENT │
                    │  (Learner) │
                    └────────────┘
                          │
                          ▼
                  View Grades/Enroll
                  Pay Fees/Records
```

---

## Getting Started - Superadmin

### 1. Initial System Access

**Super Admin Account (created during bootstrap):**
- **Email**: `superadmin@ishrm.edu.ph`
- **Password**: `ISHRMAdmin2025!`
- Created by `scripts/create_superadmin.py`. Full unrestricted system access.

**Test Admin Account (for training):**
- **Email**: `admin@ishrm.edu.ph`
- **Password**: `adminadmin`
- Standard admin role — most administrative tasks. Use this for day-to-day staff training.

**First Login Steps:**
1. Navigate to: `https://myishrm.flatwire.io` (or your configured domain)
2. Enter the Super Admin credentials above
3. **IMPORTANT**: Change the default password immediately after first login
4. Enable MFA (Multi-Factor Authentication) if available

> **Note:** If `admin@ishrm.edu.ph` cannot log in, the auth record may be missing (the account exists in user records but Supabase Auth has no password). Use the Super Admin account, then re-create the admin via the user management screen, or re-run the seed-data step from the Super Admin dashboard.

### 2. Admin Dashboard Overview

Upon login, the admin sees:

```
┌─────────────────────────────────────────────────────────────┐
│                    ADMIN DASHBOARD                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  📊 System Statistics                                        │
│  ├─→ Total Users: 150                                        │
│  ├─→ Active Students: 120                                    │
│  ├─→ Faculty Members: 20                                     │
│  └─→ Staff Accounts: 10                                      │
│                                                              │
│  ⚙️  Quick Actions                                           │
│  ├─→ [Create Staff Account]                                  │
│  ├─→ [Manage Colleges]                                       │
│  ├─→ [Academic Year Setup]                                   │
│  └─→ [System Configuration]                                  │
│                                                              │
│  🔧 Administration Menu                                      │
│  ├─→ User Management                                         │
│  ├─→ College Management                                      │
│  ├─→ Program Management                                      │
│  ├─→ Academic Year & Semester                                │
│  ├─→ System Logs & Audit Trail                              │
│  └─→ Settings & Configuration                                │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### 3. Initial System Setup Checklist

Before the system can be used, admin must:

- [ ] **Change default admin password**
- [ ] **Create academic year and semester**
- [ ] **Create colleges** (e.g., College of Hospitality)
- [ ] **Create staff accounts** (Registrar, Dean, Admission, Accounting)
- [ ] **Verify Supabase email settings** (for notifications)
- [ ] **Test login for each role**

---

## Staff Account Management

### Creating Staff Accounts

**Navigation:** Admin Dashboard → User Management → Create Staff Account

### 1. Create Registrar Account

**Why First?** Registrar manages student records and enrollments.

**Steps:**
1. Click **"Create Staff Account"**
2. Fill in details:
   ```
   First Name: Maria
   Last Name: Santos
   Email: registrar@ishrm.edu.ph
   Role: Registrar
   Password: (auto-generated or manual)
   ```
3. Click **"Create Account"**
4. ✅ Registrar account created
5. Share credentials with staff member (via secure channel)

**Registrar Capabilities:**
- ✅ Manage student enrollments
- ✅ Convert applicants to students
- ✅ Issue student IDs
- ✅ Process document requests
- ✅ View all student records
- ✅ Generate reports

### 2. Create Dean Accounts

**Why Important?** Deans manage their college's courses and faculty assignments.

**Steps:**
1. Click **"Create Staff Account"**
2. Fill in details:
   ```
   First Name: John
   Last Name: Dela Cruz
   Email: dean.hospitality@ishrm.edu.ph
   Role: Dean
   College: College of Hospitality and Tourism (select from dropdown)
   Password: (auto-generated)
   ```
3. Click **"Create Account"**
4. ✅ Dean account created and linked to college

**Dean Capabilities:**
- ✅ Create and edit courses in their college
- ✅ Assign faculty to courses
- ✅ Set class schedules and sections
- ✅ Manage course offerings per semester
- ✅ View college statistics
- ✅ Monitor faculty performance

**Create Deans for Each College:**
- ✅ College of Hospitality and Tourism
- ✅ College of Business and Entrepreneurship
- ✅ Senior High School Tech-Voc Track

### 3. Create Admission Officer Account

**Why Important?** Processes new applicant applications and generates invoices.

**Steps:**
1. Click **"Create Staff Account"**
2. Fill in details:
   ```
   First Name: Anna
   Last Name: Reyes
   Email: admission@ishrm.edu.ph
   Role: Admission
   Password: (auto-generated)
   ```
3. Click **"Create Account"**
4. ✅ Admission officer account created

**Admission Officer Capabilities:**
- ✅ View all applicant applications
- ✅ Review application documents
- ✅ Approve applications and generate invoices
- ✅ Monitor applicant payment status
- ❌ Cannot convert to student (Registrar's role)

### 4. Create Accounting Staff Account

**Why Important?** Verifies payment proofs before student conversion.

**Steps:**
1. Click **"Create Staff Account"**
2. Fill in details:
   ```
   First Name: Carlos
   Last Name: Ramos
   Email: accounting@ishrm.edu.ph
   Role: Accounting
   Password: (auto-generated)
   ```
3. Click **"Create Account"**
4. ✅ Accounting staff account created

**Accounting Capabilities:**
- ✅ View all payment proofs
- ✅ Verify payment receipts
- ✅ Approve or reject payments
- ✅ Generate financial reports
- ✅ Track student account balances

### 5. Create Faculty Accounts

**When?** After colleges and courses are set up.

**Steps:**
1. Click **"Create Staff Account"**
2. Fill in details:
   ```
   First Name: Prof. Lisa
   Last Name: Garcia
   Email: faculty.garcia@ishrm.edu.ph
   Role: Faculty
   Department: College of Hospitality and Tourism
   Password: (auto-generated)
   ```
3. Click **"Create Account"**
4. ✅ Faculty account created
5. **Next:** Dean will assign this faculty to courses

**Faculty Capabilities:**
- ✅ View assigned classes
- ✅ Submit student grades
- ✅ View class rosters
- ✅ Mark attendance
- ❌ Cannot assign themselves to courses (Dean's role)

---

## Academic Setup Workflow

### Phase 1: College Management

**Who:** Admin (Superadmin)

**Navigation:** Admin Dashboard → College Management → Create College

**Steps:**

1. **Create College: Hospitality and Tourism**
   ```
   College Name: College of Hospitality and Tourism
   Code: CHT
   Dean: dean.hospitality@ishrm.edu.ph (select from dropdown)
   Status: Active
   ```
   Click **"Create College"**

2. **Create College: Business and Entrepreneurship**
   ```
   College Name: College of Business and Entrepreneurship
   Code: CBE
   Dean: dean.business@ishrm.edu.ph
   Status: Active
   ```

3. **Create College: Senior High School**
   ```
   College Name: Senior High School Tech-Voc
   Code: SHS
   Dean: dean.shs@ishrm.edu.ph
   Status: Active
   ```

✅ **Result:** Three colleges created with assigned deans

---

### Phase 2: Program/Course Creation (By Dean)

**Who:** Dean (of each college)

**Important Terminology:**
- **Course** = Academic program/degree (e.g., BS Hospitality Management)
- **Subject** = Individual class/module within a course (e.g., "Introduction to Hospitality")
- **Section** = Specific class schedule/group (e.g., "HM 101 - Section A")

**Navigation:** Dean Dashboard → Course Management → Create Course

**Example: Dean of Hospitality Creates BS Hospitality Management**

1. Login as Dean (`dean.hospitality@ishrm.edu.ph`)
2. Go to **"Course Management"**
3. Click **"Create New Course"**
4. Fill in course details:
   ```
   Course Code: BSHM
   Course Name: BS Hospitality Management
   Description: Four-year bachelor's degree in hospitality management
   Duration: 4 years (8 semesters)
   Total Units: 180 units
   College: College of Hospitality and Tourism (auto-selected)
   Status: Active
   ```
5. Click **"Create Course"**
6. ✅ Course created successfully

**Repeat for Other Courses:**
- ✅ BS Tourism Management (BSTM)
- ✅ BS Culinary Management (BSCM)
- ✅ BSBA in Human Resource Management (BSBA-HRM)

---

### Phase 3: Subject Creation & Curriculum Setup (By Dean)

**Who:** Dean

**Navigation:** Dean Dashboard → Course Management → [Select Course] → Subjects → Add Subject

**Example: Adding Subjects to BS Hospitality Management**

#### First Year, First Semester Subjects

1. Click **"Add Subject"**
2. Fill in subject details:
   ```
   Subject Code: HM 101
   Subject Name: Introduction to Hospitality Industry
   Description: Fundamentals of hospitality management
   Units: 3 units
   Lecture Hours: 2 hours/week
   Lab Hours: 1 hour/week
   Year Level: 1st Year
   Semester: 1st Semester
   Prerequisites: None
   ```
3. Click **"Save Subject"**

**Continue Adding First Year Subjects:**

| Code | Subject Name | Units | Year | Sem |
|------|--------------|-------|------|-----|
| HM 101 | Introduction to Hospitality Industry | 3 | 1 | 1 |
| HM 102 | Food and Beverage Service | 3 | 1 | 1 |
| HM 103 | Front Office Operations | 3 | 1 | 1 |
| GED 101 | English Communication | 3 | 1 | 1 |
| GED 102 | Mathematics for Hospitality | 3 | 1 | 1 |
| PE 101 | Physical Education 1 | 2 | 1 | 1 |
| NSTP 101 | National Service Training Program 1 | 3 | 1 | 1 |

**Total:** 20 units for 1st Year, 1st Semester

✅ **Result:** Complete curriculum defined for the course

---

### Phase 4: Course Section Creation & Faculty Assignment (By Dean)

**Who:** Dean

**When:** Before each semester starts (e.g., start of School Year 2025-2026, 1st Semester)

**Navigation:** Dean Dashboard → Course Sections → Create Section

**Example: Creating Section for HM 101**

1. Click **"Create Course Section"**
2. Fill in section details:
   ```
   Subject: HM 101 - Introduction to Hospitality Industry (select from dropdown)
   Section Name: HM 101 - Section A
   Academic Year: 2025-2026
   Semester: 1st Semester

   Schedule:
   - Day: Monday, Wednesday, Friday
   - Time: 8:00 AM - 10:00 AM
   - Room: Room 201

   Capacity: 40 students
   Faculty: Prof. Lisa Garcia (select from dropdown)

   Status: Open for Enrollment
   ```
3. Click **"Create Section"**
4. ✅ Section created and assigned to faculty

**Create Multiple Sections if Needed:**
- **HM 101 - Section A** (8:00 AM - 10:00 AM, Prof. Garcia) - 40 slots
- **HM 101 - Section B** (10:00 AM - 12:00 PM, Prof. Santos) - 40 slots

**Repeat for All Subjects in the Semester:**
- ✅ HM 102 - Food and Beverage Service (2 sections)
- ✅ HM 103 - Front Office Operations (2 sections)
- ✅ GED 101 - English Communication (3 sections)
- ... and so on

✅ **Result:**
- All subjects have available sections
- Faculty members are assigned to sections
- Students can now enroll in these sections

**What Faculty Sees:**

When Prof. Garcia logs in:
```
┌─────────────────────────────────────────────────────────────┐
│               FACULTY DASHBOARD - Prof. Lisa Garcia          │
├─────────────────────────────────────────────────────────────┤
│  📚 My Assigned Courses (SY 2025-2026, 1st Semester)        │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │ HM 101 - Introduction to Hospitality Industry - Sec A │ │
│  │ Schedule: MWF 8:00 AM - 10:00 AM | Room 201           │ │
│  │ Enrolled: 35/40 students                              │ │
│  │ [View Roster] [Submit Grades] [Mark Attendance]       │ │
│  └────────────────────────────────────────────────────────┘ │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │ HM 102 - Food and Beverage Service - Sec A            │ │
│  │ Schedule: TTh 1:00 PM - 4:00 PM | Lab 101             │ │
│  │ Enrolled: 38/40 students                              │ │
│  │ [View Roster] [Submit Grades] [Mark Attendance]       │ │
│  └────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

---

## Applicant Admission & Payment Workflow

**🚨 NEW WORKFLOW (with Payment Verification)**

### Complete Admission-to-Student Process

```
┌─────────────────────────────────────────────────────────────────┐
│          COMPLETE ADMISSION & PAYMENT WORKFLOW                   │
└─────────────────────────────────────────────────────────────────┘

PHASE 1: APPLICATION SUBMISSION
┌──────────────────────────────────────────────────────────────┐
│ 👤 APPLICANT                                                 │
│ 1. Register account at /apply                                │
│ 2. Fill personal information                                 │
│ 3. Upload required documents:                                │
│    ├─→ Valid ID                                             │
│    ├─→ Birth Certificate                                    │
│    ├─→ High School Transcript (or College for transferees) │
│    └─→ 2x2 Photo                                            │
│ 4. Submit application                                        │
│ ✅ Status: PENDING                                           │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
PHASE 2: APPLICATION REVIEW
┌──────────────────────────────────────────────────────────────┐
│ 🎫 ADMISSION OFFICER                                         │
│ 1. Login to admission dashboard                             │
│ 2. View pending applications                                │
│ 3. Review applicant information                             │
│ 4. Verify all documents uploaded ✅                          │
│ 5. Click "Approve & Generate Invoice"                       │
│ 6. Configure invoice:                                        │
│    ├─→ Admission Fee: ₱2,000                                │
│    ├─→ Registration Fee: ₱1,500                             │
│    ├─→ Other fees: (add/remove items)                       │
│    └─→ Due date: 7 days from now                            │
│ 7. Click "Generate Invoice"                                 │
│ ✅ Status: APPROVED (Invoice Generated)                      │
│ ✅ Invoice Number: INV-2025-00001                            │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
PHASE 3: PAYMENT UPLOAD
┌──────────────────────────────────────────────────────────────┐
│ 👤 APPLICANT                                                 │
│ 1. Login to applicant portal                                │
│ 2. Navigate to "Payment" section                            │
│ 3. View invoice details:                                     │
│    ├─→ Invoice #: INV-2025-00001                            │
│    ├─→ Total: ₱3,500                                        │
│    ├─→ Balance: ₱3,500                                      │
│    └─→ Due Date: Nov 27, 2025                               │
│ 4. Pay at cashier or via bank transfer                      │
│ 5. Click "Upload Payment Proof"                             │
│ 6. Fill payment details:                                     │
│    ├─→ Amount Paid: ₱3,500                                  │
│    ├─→ Payment Method: Bank Transfer                        │
│    ├─→ Payment Date: Nov 20, 2025                           │
│    ├─→ Reference #: BT-123456789                            │
│    └─→ Upload Receipt: receipt.jpg (max 5MB)                │
│ 7. Click "Submit Payment Proof"                             │
│ ✅ Status: AWAITING VERIFICATION                             │
│ ✅ Proof Number: PROOF-2025-00001                            │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
PHASE 4: PAYMENT VERIFICATION
┌──────────────────────────────────────────────────────────────┐
│ 💰 ACCOUNTING STAFF                                          │
│ 1. Login to accounting dashboard                            │
│ 2. Navigate to "Payment Verification"                       │
│ 3. View pending payment proofs                              │
│ 4. Click "View Receipt" to see uploaded proof               │
│ 5. Verify receipt matches bank records:                     │
│    ├─→ Amount: ₱3,500 ✓                                     │
│    ├─→ Reference: BT-123456789 ✓                            │
│    ├─→ Date: Nov 20, 2025 ✓                                 │
│    └─→ Bank: Confirmed in bank system ✓                     │
│ 6a. If valid: Click "Verify"                                │
│     └─→ Add notes: "Verified via bank confirmation"         │
│ 6b. If invalid: Click "Reject"                              │
│     └─→ Add reason: "Amount mismatch" (min 10 chars)        │
│ 7. Click "Confirm Verification" or "Confirm Rejection"      │
│ ✅ Status: PAYMENT VERIFIED                                  │
│ ✅ Invoice Status: PAID                                      │
│ ✅ Applicant notified                                        │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
PHASE 5: STUDENT CONVERSION
┌──────────────────────────────────────────────────────────────┐
│ 📋 REGISTRAR                                                 │
│ 1. Login to registrar dashboard                             │
│ 2. Navigate to "Applicant Management"                       │
│ 3. Filter: "Approved (Ready for Conversion)"                │
│ 4. See applicant with ✅ Payment Verified badge              │
│ 5. Click "Convert to Student"                               │
│ 6. Review applicant summary                                 │
│ 7. Set year level: 1st Year (or 2nd/3rd/4th for transfer)  │
│ 8. Enter initial password: (min 12 characters)              │
│ 9. Click "Convert to Student"                               │
│ ✅ Status: ENROLLED                                          │
│ ✅ Student ID Generated: 2025-00042                          │
│ ✅ User account created in Supabase                          │
│ ✅ Student can now login!                                    │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ 🎓 STUDENT (Former Applicant)                                │
│ Login: gabrielrebadulla@gmail.com                           │
│ Password: (set by registrar)                                │
│ Student ID: 2025-00042                                       │
│                                                              │
│ Now has access to:                                           │
│ ├─→ Student Dashboard                                        │
│ ├─→ Enrollment (course registration)                         │
│ ├─→ Grades Viewing                                           │
│ ├─→ Payment Management                                       │
│ └─→ Document Requests                                        │
└──────────────────────────────────────────────────────────────┘
```

### Payment Workflow Key Points

✅ **Invoice Generation** - Admission officer creates invoice (does NOT convert to student)
✅ **Payment Upload** - Applicant uploads proof after paying
✅ **Accounting Verification** - Accounting staff verifies payment before conversion
✅ **Registrar Conversion** - Only registrar can convert verified applicant to student
✅ **Audit Trail** - Every step is logged with timestamps and user actions

### Payment Rejection Scenario

If accounting rejects payment:

```
REJECTED PAYMENT FLOW
┌──────────────────────────────────────────────────────────────┐
│ 💰 ACCOUNTING rejects payment proof                          │
│ Reason: "Amount is ₱3,000 but should be ₱3,500"             │
│ ✅ Rejection saved                                           │
└──────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ 👤 APPLICANT sees rejection                                  │
│ ❌ Payment Status: REJECTED                                  │
│ ❌ Reason: "Amount is ₱3,000 but should be ₱3,500"          │
│                                                              │
│ 1. Pay the correct amount (₱3,500)                          │
│ 2. Upload new payment proof                                 │
│ 3. Submit for verification again                            │
│ ✅ New proof submitted: PROOF-2025-00002                     │
└──────────────────────────────────────────────────────────────┘
```

---

## Role-Specific Guides

### Admin (Superadmin)

**Key Responsibilities:**
- Create and manage all staff accounts
- Configure system settings
- Monitor system health
- Generate system-wide reports

**Common Tasks:**
1. **Create Staff Account** → User Management → Create Account
2. **View System Logs** → Audit Trail → View Logs
3. **Academic Year Setup** → Settings → Academic Year
4. **Backup Database** → System → Backups

---

### Dean

**Key Responsibilities:**
- Manage college courses and curriculum
- Assign faculty to course sections
- Monitor academic performance

**Common Tasks:**
1. **Create Course** → Course Management → Create Course
2. **Add Subjects** → Course → Subjects → Add Subject
3. **Create Section** → Course Sections → Create Section
4. **Assign Faculty** → Section → Assign Faculty

**Dashboard Overview:**
```
┌─────────────────────────────────────────────────────────────┐
│         DEAN DASHBOARD - College of Hospitality             │
├─────────────────────────────────────────────────────────────┤
│  📊 College Statistics                                       │
│  ├─→ Total Courses: 4                                       │
│  ├─→ Total Sections: 45                                     │
│  ├─→ Faculty Members: 12                                    │
│  └─→ Enrolled Students: 320                                 │
│                                                              │
│  📚 Course Management                                        │
│  ├─→ [Create New Course]                                    │
│  ├─→ [Manage Existing Courses]                              │
│  └─→ [View Curriculum]                                      │
│                                                              │
│  🗓️ Section Management (Current Semester)                   │
│  ├─→ [Create Course Sections]                               │
│  ├─→ [Assign Faculty to Sections]                           │
│  └─→ [View Section Enrollments]                             │
│                                                              │
│  👨‍🏫 Faculty Management                                      │
│  ├─→ [View Faculty List]                                    │
│  ├─→ [Faculty Load Summary]                                 │
│  └─→ [Performance Monitoring]                               │
└─────────────────────────────────────────────────────────────┘
```

---

### Admission Officer

**Key Responsibilities:**
- Review applicant applications
- Approve applications and generate invoices
- Monitor payment status

**Common Tasks:**
1. **Review Application** → Applications → View Pending
2. **Approve & Generate Invoice** → Application → Approve
3. **View All Invoices** → Invoices → View All

**Dashboard:**
```
┌─────────────────────────────────────────────────────────────┐
│               ADMISSION OFFICER DASHBOARD                    │
├─────────────────────────────────────────────────────────────┤
│  📊 Application Statistics                                   │
│  ├─→ Pending Applications: 15                               │
│  ├─→ Approved (Awaiting Payment): 25                        │
│  └─→ Total Applications: 120                                │
│                                                              │
│  📋 Pending Applications                                     │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ APP-2025-00123 | Juan Dela Cruz                      │  │
│  │ Course: BS Hospitality Management                    │  │
│  │ Status: PENDING | Documents: ✅ Complete             │  │
│  │ [Review Application] [Approve & Generate Invoice]    │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

---

### Accounting Staff

**Key Responsibilities:**
- Verify payment proofs
- Approve or reject payments
- Generate financial reports

**Common Tasks:**
1. **View Pending Payments** → Payment Verification → Pending
2. **Verify Payment** → Payment Proof → View → Verify
3. **Reject Payment** → Payment Proof → View → Reject

---

### Registrar

**Key Responsibilities:**
- Convert approved and paid applicants to students
- Manage student enrollments
- Process document requests

**Common Tasks:**
1. **Convert to Student** → Applicants → Ready for Conversion → Convert
2. **View Student Records** → Students → View All
3. **Enroll Student in Sections** → Enrollment → Create Enrollment

---

### Faculty

**Key Responsibilities:**
- Submit student grades
- Manage class attendance
- View assigned classes

**Common Tasks:**
1. **View Classes** → My Classes
2. **Submit Grades** → Class → Grade Submission
3. **Mark Attendance** → Class → Attendance

---

### Student

**Key Responsibilities:**
- Enroll in courses each semester
- View grades and schedules
- Pay fees
- Request documents

**Common Tasks:**
1. **Enroll in Courses** → Enrollment → Create Enrollment
2. **View Grades** → Grades → View All
3. **Pay Fees** → Payments → Make Payment
4. **View Schedule** → Schedule → Current Semester

---

## Support & Troubleshooting

### Common Issues

**Issue: Cannot login**
- ✅ Verify email and password are correct
- ✅ Check if account is active (contact admin)
- ✅ Try password reset

**Issue: Payment verification taking too long**
- ✅ Contact accounting office
- ✅ Ensure receipt is clear and readable
- ✅ Verify payment amount matches invoice

**Issue: Cannot enroll in courses**
- ✅ Check if sections are open for enrollment
- ✅ Verify payment is cleared
- ✅ Contact registrar if issues persist

### Contact Information

**Technical Support:**
- Email: support@ishrm.edu.ph
- Phone: (046) 123-4567

**Registrar Office:**
- Email: registrar@ishrm.edu.ph
- Office Hours: Mon-Fri, 8:00 AM - 5:00 PM

**Accounting Office:**
- Email: accounting@ishrm.edu.ph
- Office Hours: Mon-Fri, 8:00 AM - 4:00 PM

---

**End of User Guide**

**Document Version:** 2.0
**Last Updated:** November 20, 2025
**System:** MyISHRM Student Information System
**Institution:** International School of Hospitality and Restaurant Management
