# Forgot Password

- Notify user by (phone sms, email) such that the user has to click a link in the email that takes them to your site and ask the user to enter a new password
- Ask user to enter login credentials they already have (Facebook, Twitter, Google, Microsoft Live, OpenID etc) to validate user before allowing user to change password
- Send notification to user to confirm registration or forgot password usage
- Send notifications that account information has been changed for registered email

**General Consideration**

- The identity and shared secret/password must be transferred using encryption to provide data confidentiality
- A shared secret can never be stored in clear text format, even if only for a short time in a message queue
- A shared secret must always be stored in hashed or encrypted format in a database
- When reporting an invalid entry back to a user, the username and or password should not be identified as being invalid
