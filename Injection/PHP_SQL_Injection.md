# PHP SQL Injection

- An SQL injection attack consists of injecting SQL query portions in the back-end database system via the client interface in the web application

**Sample 4 :**

```php
1 <?php
1 $pass=$_GET["pass"];
2 $con = mysql_connect(‘localhost’, ‘owasp’, ‘abc123’);
3 mysql_select_db(“owasp_php”, $con);
4 $sql="SELECT card FROM users WHERE password = '".$pass."'";
5 $result = mysql_query($sql);
6 ?>
```

### Mitigation

- use `addslashes()` function
- use `mysql_real_escape_string()` function

### **Addslashes**

- You will avoid Sql injection using addslashes() only in the case when you wrap the query string with quotes

**Sample 5 :**

```php
1 $id = addslashes( $_GET[‘id’] );
2 $query = 'SELECT title FROM books WHERE id = ' . $id;
```

### mysql_real_escape_string():

- is a little bit more powerful than addslashes() as it calls MySQL’s library function mysql_real_escape_string, which prepends backslashes to the following characters: `\x00`, `\n`, `\r`, `\`, `‘`, `“` and `\x1a`
