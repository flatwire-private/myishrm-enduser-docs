# System Administrator Troubleshooting

Common admin issues and solutions.

---

## 🔐 Account Management

### Cannot Create Staff Account
**Check:**
- Email not already in use
- Valid email format
- Required fields filled
- Correct role selected

### Staff Cannot Login
**Verify:**
- Account is active (not disabled)
- Correct email and password
- Email verified (if verification enabled)
- Role assigned correctly

---

## 🎓 Academic Setup

### Cannot Create College
**Possible Issues:**
- College code already exists
- Missing required fields
- Dean not selected

### Course Creation Fails
**Check:**
- Course code unique
- College selected
- All required fields filled

---

## 💾 Database Issues

### Migration Failed
**Steps:**
1. Check database connection
2. View migration logs:
   ```bash
   docker logs ishrm-api --tail 100
   ```
3. Rollback if needed:
   ```bash
   docker exec ishrm-api alembic downgrade -1
   ```
4. Contact technical support

---

## 🔧 System Maintenance

### Regular Maintenance Tasks

**Weekly:**
- Review system logs
- Check disk space
- Monitor user accounts

**Monthly:**
- Database backup verification
- User activity audit
- Performance review

---

## 📞 Escalation

For critical issues, contact:
- **Technical Lead:** support@ishrm.edu.ph
- **Emergency:** (046) 123-4567

**Portal:** [https://myishrm.flatwire.io](https://myishrm.flatwire.io)
