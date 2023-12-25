# Out-of-Band Communication

The main reason an application would wish to communicate with the end user via these separate channels is for security

**Examples of sensitive operations could include**

- Changing password
- Changing account details, such as e-mail address, home address, etc
- Transferring funds in a banking application
- Submitting, modifying or cancelling orders

**What to Review**

- Recognize the risk of the system being abused. Attackers would like to flood someone with SMS messages from your site, or e-mails to random people
- When possible, only authenticated users can access links that cause an out-of-band feature to be invoked (forgot password being an exception)
- Rate limit the interface, thus users with infected machines, or hacked accounts, can’t use it to flood out-of-band messages to a user
- Do not allow the feature to accept the destination from the user, only use registered phone numbers, e-mails, addresses.
