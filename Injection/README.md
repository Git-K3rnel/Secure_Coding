# Overview

### Root Cause

- Using string concatenation to generate a SQL statement
- Parser does not distinguish which part of the statement is code and which part is data


### Mitigation

1. HTML Encode all user input
2. Use static analysis tools
3. Parameterize SQL queries (prepared statements)
4. SQL parser can distinguish between code and data
5. Use Stored Procedures

### Parameterized SQL Queries

- allows the SQL query string to be defined in such a way that the client input can’t be treated as part of the SQL syntax

**Sample 1 :**

```sql
1 String query = “SELECT id, firstname, lastname FROM authors WHERE forename = ? and surname = ?”;
2 PreparedStatement pstmt = connection.prepareStatement( query );
3 pstmt.setString( 1, firstname );
4 pstmt.setString( 2, lastname );
```

```text
💡 When the ‘setString’ function is called, this function automatically checks that no SQL syntax is contained within the string value.
```

### **Avoid Using String Concatenation**

- you should never use string concatenation in combination with the client input value, especially if the concatenation involves building any items in the where clause

S**ample 2 :**

```sql
1 String query = “select id, firstname, lastname FROM authors”;
2
3 if (( firstname != NULL && firstname.length != 0 ) && ( lastname != NULL && lastname.length != 0 )) {
4 query += “WHERE forename = ? AND surname = ?”;
5 }
6 else if ( firstname != NULL && firstname.length != 0 ) {
7 query += “WHERE forename = ?”;
8 }
9 else if ( lastname!= NULL && lastname.length != 0 ) {
10 query += “WHERE surname = ?”;
11 }
12
13 query += “;”;
14
15 PreparedStatement pstmt = connection.prepareStatement( query )
```

```text
💡 if no firstname or lastname were given then the SQL statement would not have any WHERE clause, and the entire table would be returned.
```

### Use Flexible Parameterized Statements

- one option for flexible parameterized statements is to use ‘if’ statements to select the correct query based on the input values provided

**Sample 3 :**

```sql
1 String query;
2 PreparedStatement pstmt;
3
4 if ( (firstname!= NULL && firstname.length != 0) &&
5 lastname!= NULL && lastname.length != 0) ) {
6   query = “Select id, firstname, lastname FROM authors WHERE forename = ? and surname = ?”
7   pstmt = connection.prepareStatement( query );
8   pstmt.setString( 1, firstname );
9   pstmt.setString( 2, lastname );
10 }
11 else if (firstname != NULL && firstname.length != 0) {
12   query = “Select id, firstname, lastname FROM authors WHERE forename = ?”;
13   pstmt = connection.prepareStatement( query );
14   pstmt.setString( 1, firstname );
15 }
16 else if (lastname != NULL && lastname.length != 0){
17   query = “Select id, firstname, lastname FROM authors WHERE surname= ?”;
18   pstmt = connection.prepareStatement( query );
19   pstmt.setString( 1, lastname);
20 }
21 else{
22   throw NameNotSpecifiedException(); }
```

### What to Review

- Always validate user input by testing type, length, format, and range
- Test the size and data type of input and enforce appropriate limits
- Test the content of string variables and accept only expected values. Reject entries that contain binary data, escape
    
    sequences, and comment characters
    
- When you are working with XML documents, validate all data against its schema as it is entered
- Never build SQL statements directly from user input
- Use stored procedures to validate user input, when not using stored procedures use SQL API provided by platform.
    
    i.e. Parameterized Statements
    
- Implement multiple layers of validation
- Never concatenate user input that is not validated. String concatenation is the primary point of entry for script injection
