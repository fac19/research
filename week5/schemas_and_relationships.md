# SCHEMAS AND RELATIONSHIPS

![scheming](https://media1.giphy.com/media/l3vRaFMVyMFkpOg8g/200.gif?cid=e1bb72ffe60d7f6fb597965245ee1bfe7548b305f54586f4&rid=200.gif)

---

![indexing](https://i.imgur.com/6gCkOqP.png)

---

![Venn](https://i.imgur.com/HrVJ6Hf.png)


---

## What we're going to talk about
How schemas describe a relational database:
- Three types of data relationships 
- Schemas and how 'foreign keys' can help us connect our data

---

## But first, what is a schema?!

A set of information in a table is okay, but it is much better if we can relate that information to other tables that hold even more juicy data.

A **schema** describes the relationships in a given database by associating certain headings, or keys, from those tables.

![table](https://media.giphy.com/media/8MBqK5fACFvMc/giphy.gif)

---

## Here's one we made earlier...

![](https://i.imgur.com/G2RTrBm.png)

- `user_id` refers directly to a value in a different table.

---

### What does that mean? :face_with_monocle: 

- By relating tables, we avoid duplicating info.
- NAMES 'collection' of tables.
- Can contain: views, indexes, sequences, data types, operators, and functions.

---

### Why use it?

- To allow many users to use one database without interfering with each other.
- To organize database objects into logical groups to make them more manageable.
- Third-party applications can be put into separate schemas so they do not collide with the names of other objects.

---

## Relationship types
- One to one
- One to many
- Many to many

![](https://media.giphy.com/media/4ryp9Ihw0BEyc/giphy.gif)

---

## Junction Tables
A method of representation for many-to-many relationships which prevents duplicate entries.
Sits between two tables which form the relationships and relates information on those relationships.
e.g. Table 1: Student name, age, address
Table 2: Class name, teacher name, dates
Each row in each table could be matched to any number of rows in the other

---

Junction table - Class name + student name

Joins the  keys of related tables.

![](https://i.imgur.com/e7POTKP.png)


---

## Foreign keys 

Every table has a primary key, which is foreign to every other table in the database.

---

### They help us to establish relationships :heart:

Specificity and efficiency


---

## Why these are important
The first rule of database normalization is that...

![](https://media1.giphy.com/media/1AfLx8dLTVoHK/200.gif?cid=e1bb72ff491030f9c275251ddcbe5b352433df7ece91b58f&rid=200.gif)

---

>Each table cell should contain a single, discrete piece of data
>

Because we can create simple, clearly defined links between each bit of data.

---

### The thing is that us humans, we forget things...
Take this table for example and scale it us to 100s or 1000s or users:

![](https://i.imgur.com/7StKMz0.png)

---

If we have lots of data floating around with no clearly defined relationships it's easy to get

![lost](https://media1.giphy.com/media/1bAdvIjqaXCSc/200.gif?cid=e1bb72ffb00e095f23d6f8fb64d885a05d2f7adb32fd9900&rid=200.gif)

---

We can't assume that everyone working on the database will know and understand the implicit relationships between data. 

Foreign keys make sure when new people start using a database these relationships are already explicitly defined.

---

![doggies](https://media3.giphy.com/media/XHVmD4RyXgSjd8aUMb/200.gif?cid=e1bb72ffecacd53f14b6701dcc158e5a38a8c472fbe4983b&rid=200.gif)




