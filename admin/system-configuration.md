# System Configuration

Advanced system configuration for administrators.

---

## 🎓 Academic Year Setup

**Navigation:** Admin Dashboard → Settings → Academic Year

**Steps:**
1. Click **"Create Academic Year"**
2. Enter:
   - Year: e.g., "2025-2026"
   - Start Date: August 1, 2025
   - End Date: May 31, 2026
3. Set as **"Active"**
4. Click **"Save"**

**Semesters:**
- Create semesters within academic year:
  - 1st Semester (Aug - Dec)
  - 2nd Semester (Jan - May)
  - Summer (Jun - Jul)

---

## 🏫 College Management

**Create College:**
1. Admin Dashboard → College Management
2. Click **"Create College"**
3. Enter:
   - College Name
   - College Code (e.g., CHT)
   - Assign Dean
4. Click **"Save"**

---

## 📧 Email Configuration

**Email notifications require Supabase SMTP setup.**

See: [Email Setup Guide](https://github.com/your-org/myishrm-api/docs/EMAIL_SETUP_QUICKSTART.md)

---

## 🔒 Security Settings

### Password Policy
- Minimum: 12 characters
- Complexity: Required
- Expiration: 90 days (optional)

### Session Management
- Access token: 15 minutes
- Inactivity timeout: 15 minutes
- Warning at: 12 minutes

---

## 📊 System Monitoring

**View Logs:**
- Admin Dashboard → System Logs
- Filter by:
  - User
  - Action
  - Date range
  - Module

**Audit Trail:**
- All critical operations logged
- Immutable record
- Export capability

---

## 🔧 Advanced Configuration

For advanced configuration, consult technical documentation or contact support@ishrm.edu.ph

**Portal:** [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
