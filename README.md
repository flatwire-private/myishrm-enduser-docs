# MyISHRM Student Information System

**Welcome to MyISHRM Documentation**

MyISHRM is a comprehensive Student Information System designed for the International School of Hospitality and Restaurant Management (ISHRM). This system manages the complete academic lifecycle from applicant admission to student graduation.

---

## System Access

**Portal URL:** [https://myishrm.flatwire.io](https://myishrm.flatwire.io)

---

## Enrollment Workflow

New to MyISHRM? Start here to understand how enrollment works.

**[View the Complete Enrollment Workflow](enrollment-workflow.md)**

The enrollment process follows 5 steps:

```
APPLICANT → ADMISSION → APPLICANT → ACCOUNTING → REGISTRAR
 (Apply)    (Approve)    (Pay)      (Verify)    (Convert)
```

1. **Applicant** submits application online
2. **Admission** reviews and approves, generates invoice
3. **Applicant** pays and uploads payment proof
4. **Accounting** verifies the payment
5. **Registrar** converts applicant to student

---

## Test Accounts

For testing and training purposes, use these credentials:

| Role | Email/Student ID | Password |
|------|-------|----------|
| **Super Admin** | superadmin@ishrm.edu.ph | ISHRMAdmin2025! |
| **Admin** | admin@ishrm.edu.ph | adminadmin |
| **Registrar** | registrar@ishrm.edu.ph | registrarregistrar |
| **Dean** | dean@ishrm.edu.ph | deandean |
| **Admission** | admission@ishrm.edu.ph | admissionadmission |
| **Accounting** | accounting@ishrm.edu.ph | accountingaccounting |
| **Faculty** | faculty@ishrm.edu.ph | facultyfaculty |
| **Student** | 2024-00001 | studentstudent |

**Important:** These are test accounts for training purposes only. Change passwords in production.

> **Initial setup:** The Super Admin account (`superadmin@ishrm.edu.ph`) is created by `scripts/create_superadmin.py` during system bootstrap. It has full system access and can manage all other roles. **Change this password immediately after first login.**

---

## Documentation Sections

### For System Administrators
Complete setup and management guides for system administrators.

**[System Administrator Guide](admin/system-admin-guide.md)**
- Initial system setup and superadmin access
- Staff account management (Registrar, Dean, Admission, Accounting, Faculty)
- College and academic program configuration
- Course sections and faculty assignment
- System maintenance and troubleshooting

### For End Users
User guides organized by role.

**[User Guides by Role](users/user-guides.md)**
- **[Admission Officer Guide](users/admission-officer.md)** - Review applications, generate invoices
- **[Accounting Staff Guide](users/accounting-staff.md)** - Verify payments, financial management
- **[Registrar Guide](users/registrar.md)** - Convert applicants, manage enrollments
- **[Dean Guide](users/dean.md)** - Manage courses, assign faculty
- **[Faculty Guide](users/faculty.md)** - Submit grades, manage classes
- **[Student Guide](users/student.md)** - View grades, enroll in courses, pay fees
- **[Applicant Guide](users/applicant.md)** - Apply for admission, upload documents

### Payment & Admission Workflow
Complete payment-gated admission process.

**[Payment & Admission Workflow](users/payment-workflow.md)**
- Application submission and document upload
- Admission review and invoice generation
- Payment proof upload
- Accounting verification
- Final student conversion by Registrar

---

## Quick Start

**For System Administrators:**
1. Start with the [System Administrator Guide](admin/system-admin-guide.md)
2. Follow the [Initial Setup Checklist](admin/system-admin-guide.md#initial-system-setup-checklist)
3. Create staff accounts using [Staff Account Management](admin/system-admin-guide.md#staff-account-management)

**For End Users:**
1. Go to [User Guides](users/user-guides.md)
2. Select your role from the list
3. Follow the step-by-step instructions

**First Time Login:**
1. Visit [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
2. Enter your email and password
3. Follow on-screen instructions

---

## User Roles

| Role | Primary Responsibility | Access Level |
|------|----------------------|--------------|
| **Admin** | System configuration, staff account creation | Full system access |
| **Dean** | Course management, faculty assignment | College data |
| **Registrar** | Student enrollment, record management | All student data |
| **Accounting** | Payment verification, financial reports | Financial records |
| **Admission** | Application review, invoice generation | Applicant data |
| **Faculty** | Grade submission, class management | Assigned classes |
| **Student** | View grades, enroll, pay fees | Own records |
| **Applicant** | Submit application, upload documents | Own application |

---

## Support & Help

**Common Issues:**
- [Troubleshooting Guide](admin/troubleshooting.md)
- [Common User Issues](users/common-issues.md)

---

**System Version:** 2.0
**Last Updated:** November 20, 2025
**Institution:** International School of Hospitality and Restaurant Management
**Portal:** [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
