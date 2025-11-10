# Patient Data Retention & Auto-Cleanup Policy

## Overview
This system implements an automatic data retention policy **ONLY for PATIENT accounts** to ensure data privacy and compliance with data protection regulations.

## ⚠️ IMPORTANT: Role-Based Policy

### Who is Affected?
- ✅ **PATIENT accounts**: Automatically deleted after 30 days of inactivity
- ❌ **DOCTOR accounts**: NEVER automatically deleted (stored indefinitely)
- ❌ **NURSE accounts**: NEVER automatically deleted (stored indefinitely)  
- ❌ **ADMIN accounts**: NEVER automatically deleted (stored indefinitely)

## Policy Details

### Automatic Deletion After 30 Days of Inactivity (PATIENTS ONLY)
- **Trigger**: Patient accounts that have not logged in for 30 consecutive days
- **Scope**: Complete account deletion including:
  - User account credentials
  - All patient records created by the user
  - All glucose readings
  - All appointments
  - All alerts
  - All associated medical data

### Automated Warning System
Patients receive automatic notifications at multiple intervals before deletion:

- **Day 30 (First Warning)**: Initial notification sent
- **Day 15**: Reminder notification
- **Day 7**: Weekly reminder
- **Day 5**: Urgent warning (5 days remaining)
- **Day 3**: Critical warning (3 days remaining)
- **Day 2**: Final warning (2 days remaining)
- **Day 1**: Last chance warning (1 day remaining)
- **Day 0**: Critical alert - deletion imminent

**Warning Delivery Methods:**
1. **In-App Alerts**: Created in the alerts system
2. **Sidebar Notifications**: Displayed when patient logs in
3. **Activity Log**: All warnings logged for audit trail
4. **Email Notifications**: (Ready for implementation - placeholder in code)

## How It Works

### 1. Automatic Cleanup on App Startup
- The system runs `cleanup_inactive_patient_data()` every time the app starts
- Checks for patient accounts with `last_login` older than 30 days
- If no `last_login` exists, uses the `created_at` date
- Automatically deletes qualifying accounts and all associated data

### 2. Automated Warning System
- **Primary Function**: `check_and_send_deletion_warnings()`
  - Runs on app startup
  - Checks all patient accounts for inactivity
  - Sends warnings at threshold days (30, 15, 7, 5, 3, 2, 1, 0)
  - Creates in-app alerts
  - Logs all warnings in `deletion_warnings` table
  
- **Warning Notification Function**: `send_deletion_warning_notification()`
  - Prevents duplicate warnings (one per day per threshold)
  - Creates severity-based messages (WARNING, URGENT, CRITICAL)
  - Logs to activity_log for audit trail
  - Ready for email integration

- **Display Function**: `check_patient_inactivity_warning()`
  - Shows warnings in sidebar for logged-in patients
  - Displays countdown of days remaining before deletion
  - Only shown to patients (not doctors/nurses/admins)

### 3. Admin Management Panel
- **Location**: Settings → System tab (Doctor/Admin only)
- **Features**:
  - View patients approaching deletion (25-29 days)
  - View patients ready for deletion (30+ days)
  - View recent deletion warnings sent (last 10)
  - Manual cleanup trigger button
  - Manual warning check trigger button
  - Activity logs of all cleanup operations
  - Clear policy statement that only patients are affected

## For Patients

### How to Keep Your Account Active
Simply log in to your account at least once every 30 days. Each login resets the inactivity counter.

### What Happens If You Don't Login
You will receive warnings at multiple intervals:
- **Day 30**: First warning notification
- **Day 15**: Reminder (15 days remaining)
- **Day 7**: Weekly reminder (7 days remaining)
- **Day 5**: Urgent warning (5 days remaining)
- **Day 3**: Critical warning (3 days remaining)
- **Day 2**: Final warning (2 days remaining)
- **Day 1**: Last chance (1 day remaining)
- **Day 0**: Account deletion occurs
- **No Recovery**: Once deleted, data cannot be recovered

### Notification Methods
1. **In-App Alerts**: Check your Alerts section
2. **Sidebar Warning**: Visible when you log in
3. **Email** (if configured): Sent to your registered email

## For Administrators

### Viewing Inactive Accounts
1. Log in as Doctor/Admin
2. Go to Settings → System tab
3. Scroll to "Inactive Patient Data Management"
4. View metrics and lists of inactive patients

### Manual Cleanup
1. Navigate to System Settings
2. Click "Run Manual Cleanup Now"
3. System will delete all accounts inactive for 30+ days
4. Confirmation message shows number of accounts deleted

### Activity Logs
All cleanup operations are logged in the activity_log table with:
- Username: SYSTEM (for automatic) or admin username (for manual)
- Action: AUTO_CLEANUP or MANUAL_CLEANUP
- Details: List of deleted accounts
- Timestamp: When the cleanup occurred

## Technical Implementation

### Database Schema Requirements
The system requires the following columns in the `users` table:
- `last_login` (TIMESTAMP): Updated on each successful login
- `created_at` (TIMESTAMP): Account creation date
- `role` (TEXT): User role (must be 'patient' for cleanup to apply)

### Database Tables Added
1. **deletion_warnings** - Tracks all warnings sent to patients
   - username, warning_type, days_remaining, warning_sent_at, email_sent

### Functions Added
1. `cleanup_inactive_patient_data()` - Main cleanup function (PATIENTS ONLY)
2. `check_and_send_deletion_warnings()` - Automated warning system
3. `send_deletion_warning_notification()` - Individual warning sender
4. `check_patient_inactivity_warning()` - Sidebar warning display
5. Admin panel in `settings_page()` - Management interface

### Cleanup Process
```
1. Calculate cutoff date (30 days ago)
2. Query patient accounts with last_login < cutoff_date
3. For each inactive patient:
   a. Find all patient_ids created by user
   b. Delete readings for each patient_id
   c. Delete appointments for each patient_id
   d. Delete alerts for each patient_id
   e. Delete patient records
   f. Delete user account
   g. Log the cleanup action
4. Commit all changes
```

## Compliance & Privacy

### GDPR Compliance
- Automatic data deletion after inactivity period
- Clear notification to users about data retention
- Complete data erasure (right to be forgotten)

### HIPAA Considerations
- Secure deletion of all medical records
- Audit trail of all cleanup operations
- No orphaned data remains in system

## Configuration

### Changing the Retention Period
To modify the 30-day retention period, update the following:

1. In `cleanup_inactive_patient_data()`:
   ```python
   cutoff_date = (datetime.now() - timedelta(days=30)).isoformat()
   ```

2. In `check_patient_inactivity_warning()`:
   ```python
   if days_inactive >= 25:  # Warning threshold
       days_remaining = 30 - days_inactive
   ```

3. Update warning messages accordingly

## Testing

### Test Scenarios
1. **Create test patient account**
2. **Manually set last_login to 31 days ago** in database
3. **Restart app or trigger manual cleanup**
4. **Verify account and data are deleted**

### SQL for Testing
```sql
-- Set account to 31 days old
UPDATE users 
SET last_login = datetime('now', '-31 days')
WHERE username = 'test_patient' AND role = 'patient';

-- Verify deletion
SELECT * FROM users WHERE username = 'test_patient';
```

## Support

For questions or issues with the data retention policy:
1. Contact system administrator
2. Review activity logs for cleanup history
3. Check Settings → System tab for current status

---

**Last Updated**: November 4, 2025
**Version**: 1.0
