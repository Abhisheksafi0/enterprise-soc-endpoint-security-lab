# Windows Account Activity Monitoring with Splunk

Demonstrates the collection, analysis, and investigation of Windows Security Events related to successful and failed logons, logoffs, account creation, account deletion, and account changes. SPL queries are used to identify account behavior.

## Windows Security Event logs.

### 4624 → Successful Logon.
Indicates that a user successfully authenticated and logged on to a Windows system.
Useful for monitoring legitimate access and identifying unexpected login activity.
## SPL
    index=main EventCode=4624 host="DESKTOP-VFCO3RU"

<img width="1919" height="767" alt="image" src="https://github.com/user-attachments/assets/fc76f52d-7bc7-45a1-99a1-a4e1a201ed1f" />

### 4625 → Failed Logon.
Indicates that a logon attempt failed because authentication was unsuccessful.
Multiple 4625 events may indicate password guessing, brute-force activity, or unauthorized access attempts.
## SPL
Failure_Reason = Unknown user name or bad password.

    index=main EventCode=4625 host="DESKTOP-VFCO3RU"

<img width="1917" height="801" alt="image" src="https://github.com/user-attachments/assets/41fa04ab-2168-4ec6-a536-14ea013e2aa2" />

### 4634 → Logoff.
Indicates that a user session was terminated and the account logged off from the Windows system.
Useful for tracking when user sessions end and understanding account activity timelines.
## SPL
    index=main EventCode=4634 Account_Domain="SHRAWAN-LPA"

<img width="1910" height="731" alt="image" src="https://github.com/user-attachments/assets/87b03e66-4afc-45ac-bd86-910e0e16eaa9" />

### 4720 → Account Created.
Indicates that a new user account was created on the Windows system.
Unexpected account creation should be investigated because attackers may create accounts for persistence.
## SPL
    index=main EventCode=4720 "ComputerName=DESKTOP-VFCO3RU"

<img width="1910" height="772" alt="image" src="https://github.com/user-attachments/assets/1eec79d1-a7c0-42bc-8415-73891d24835c" />

### 4726 → Account Deleted.
Indicates that a user account was deleted from the Windows system.
Unexpected account deletion can be investigated as potentially suspicious administrative or attacker activity.
## SPL 
    index=main EventCode=4726 "ComputerName=DESKTOP-VFCO3RU"
    | table EventCode Account_Name source Message

<img width="1906" height="778" alt="image" src="https://github.com/user-attachments/assets/8d4fc39c-227a-42ed-979d-4deccab7bd3f" />






