# ORM

- Object/Relation Mapping (ORM) facilitates the storage and retrieval of domain objects via HQL (Hibernate Query Language) or .NET Entity framework.

**Bad Java Code Examples**

```java
List results = session.createQuery("from Items as item where item.id = " + currentItem.getId()).list();
```

**Bad .Net Code Example**

```vbnet
string userName = ctx.GetAuthenticatedUserName();
String query = "SELECT * FROM Items WHERE owner = '"
+ userName + "' AND itemname = '"
+ ItemName.Text + "'";
List items = sess.CreateSQLQuery(query).List()
```

- Code reviewer needs to make sure any data used in an HQL query uses HQL parameterized queries so that it would be used as data and not as code
