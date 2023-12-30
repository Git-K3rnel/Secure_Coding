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

**What to Review**

- map out all locations in the code being reviewed where user input is used to reference objects directly
    - user input is used to access a database row
    - accessing a file
    - application page, . . .
 

  ### Over-Posting (Mass assignments)
  Depending on the models you create, there might be sensitive data that you would not like to be modified. The vulnerability is exploited when a malicious user modifys a model’s fields, which are not exposed to the user via the view, and the malicious user to change hidden model values adds additional model parameters

**Sample Code2**

```java
public class user
{
public int ID { get; set; } <- exposed via view
public string Name { get; set; } <- exposed via view
public bool isAdmin{ get; set; } <-hidden from view
}
```

Corresponding view (HTML) :

```html
D: <%= Html.TextBox(“ID”) %> <br>
Name: <%= Html.TextBox(“Name”) %> <br>
<-- no isAdmin here!
```
