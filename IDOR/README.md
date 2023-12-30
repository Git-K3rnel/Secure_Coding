# Overview

### Root Cause

The source of the problem of this risk is based on the manipulation or updating of the data generated previously at server side

**Sample Code1**

```php
String query = “SELECT * FROM accts WHERE account = ?”; PreparedStatement pstmt = connection.
prepareStatement(query , ... );
pstmt.setString( 1, request.getParameter(“acct”));
ResultSet results = pstmt.executeQuery();
```

```text
💡 The attacker simply modifies the ‘acct’ parameter in their browser to send whatever account number they want. If the application does not perform user verification, the attacker can access any user’s account, instead of only the intended customer’s account.
```
