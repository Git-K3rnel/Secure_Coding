# Overview

Authentication is the gateway to the functionality you are wishing to protect

**Authentication Methods**

- Passwords
- Client certificate
- biometrics
- OTP
- OAUTH
- SSO

**What to Review**

- Ensure the login page is only available over TLS
- Make sure your usernames/user-ids are case insensitive
    - user ‘smith’ and user ‘Smith’ are not different
- Ensure failure messages for invalid usernames or passwords do not leak information
- Do not log invalid passwords
- Minimum length of the passwords should be enforced by the application
- Implement temporary account lockouts or rate limit login responses to prevent brute force
- Forcing the users to change passwords after a set period of time
    - store a reference (e.g. hash) of the last 5 or more passwords to ensure the user is not re-using old password
- Password complexity should be enforced
