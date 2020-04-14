# Database Security

![](https://media.giphy.com/media/11V3dAPYzVNP8s/giphy.gif)

---

- Why is it important to have passwords that are kept secret?

---

# The Problem

___

## Bad practises (From worse to better) 👿

- storing passwords as plain text on the database
`(id, username, password)`

- encrypting with a cipher key and storing passwords on the database

---

1. - add hashing algorithm (not perfect due to pigeonhole principle)
(bcrypt, scrypt, PBKDF2)


- Add some salt to the password. (concatanate string)

![](https://media.giphy.com/media/QOgvV9rV4hHpgNRBfQ/giphy.gif)

---

# The Solution 

---

- Summary of issues: 
-- storing passwords on databases
-- users putting in simple passwords. 

---

## Best practice

![](https://media.giphy.com/media/SvpHrehWvbZiin27sm/giphy.gif)
- Don't store passwords on databases at all 
- Use 3rd party solutions (e.g. Google, Microsoft, Facebook, Twitter)

---

## What to do instead?

- Find out!

---


### What is SQL injection?


- SQL injection is deliberately inserting SQL code via web page input.

- It can be malicious code used to break a database. 

---

- For a password on a user account to work we need the password to be TRUE;
- This can be done by entering a password match 
- OR
- This is where a hacker could include SQL in the password input.

username : johndoe
password : " or 1=1--

```JavaScript
uName = getRequestString("username");
uPass = getRequestString("userpassword");

sql = 'SELECT * FROM Users WHERE Name ="' + uName + '" AND Pass ="' + uPass + '"'
```

---

- Another malicious use of SQL injection is including this DROP TABLE

```SQL
SELECT * FROM Users; DROP TABLE Suppliers
```

---

### Protection

- Paramaterized statements:
```javascript=
var pg = require('pg');

var connection = "postgres://username:password@localhost/database";

var client = new pg.Client(connection);

// Query and parameters passed separately.
client.connect(function(err) {
  client.query(
    'select * from users where email = ?',
    [email],
    function(err, result) {
      // Do something with the retrieved data.
    });
  });

client.end();
```

---

- Query and data are sent to the database seperately - else the data may interfere with the program code

- Program sends first then the data follows on the second request

---

- Frameworks - 'Active Record'

- Escape or Sanitize user input with .replace()

```javascript=
SELECT * FROM Users WHERE Name ="" or "1"="1" AND Pass ="" or "1"="1"
```

---

## Refs: 
### Password stuff:
- Bad practises for storing user passwods: https://itnext.io/how-not-to-store-passwords-4955569e6e84

### SQL injections stuff: 
- https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/
---


