# Relational vs non-relational databases

What's the difference between relational (SQL) and non-relational (NoSQL) databases?

---

## Questions to consider

1. How is data structured in a SQL database? 
    - What about a NoSQL one?
2. What are some advantages of relational data? 
    - Are there disadvantages?

---

## How is data structured in a SQL database?
- Data is stored within tables
- The tables are contained within database object containers that are called Schemas.
- Schema refers to:
>  "collection of objects linked with a particular database username"

---

-  Schema also works as a security boundary, where you can limit database user permissions to be on a specific schema level only. 
-  Imagine the schema as a folder that contains a list of files. 

![image alt](https://media0.giphy.com/media/l2Je5Mochl7iyWHoQ/giphy.gif)

---

## Fun facts about tables

-  You can create up to 2.1m tables in a database and up to 1024 columns in each table!


---

- Proper table design, will make it easier to  retrieve data from the table.

![image alt](https://i.gifer.com/1olT.gif)


---

## What about a NoSQL?

(“non SQL” or “not only SQL”)

![](https://media.giphy.com/media/XeqCauSi9UbEMi7YUm/giphy.gif)
:no_good: tables/schema 

---

![](https://i.imgur.com/J6rva5W.png)

src: [NoSQL vs SQL](https://www.mongodb.com/nosql-explained/nosql-vs-sql)

---

### Different purposes

1. Document database
2. Key-value
3. Wide-column stores 
4. Graph databases

:rocket: (read) speed, flexibility
:crab: Horizontal scaling

---

## Advantages of relational (SQL) data
![](https://media.giphy.com/media/YHmYWQI6IL6Te/giphy.gif)

---

Users
| id | name |
| - | - |
| 1 | Hannah |
| 2 | Ako |

Orders
| user_id | meal_id | meal | price |
| - | - | - | - |
| 1 | 1 | Katsu Curry | £8.99 |
| 2 | 2 | Georgian Dumplings | £1,000,000 |

---

### Different tables related to each other so data is not duplicated
e.g. Instead of inserting a new column into the  Orders table and repeating all the "name" values, you relate it the the "id" from the User table.

![](https://i.imgur.com/RlWHJ4F.png)

---

### Data is kept in columns so it is easier to make certain queries
e.g. You can easily get the total price of all orders by querying the data in Orders "price" column. 

```SQL
SELECT SUM(price) FROM Orders;
```

In a NoSQL database you would have to filter through all the objects and find the "price" key to get all the values back, and then add them all up.

---

## Disadvantages of relational (SQL) data
![](https://media.giphy.com/media/j1s5Sv4iolneE/giphy.gif)

---

### Lack of support
![image alt](https://media.giphy.com/media/HjlKKc14d5tBK/giphy.gif)

---

### Too many joins
![image alt](https://media.giphy.com/media/RMTQiRYAuvvJb1k6al/giphy.gif)


---

### Advanced Planning
![image alt](https://media.giphy.com/media/l3vR6aasfs0Ae3qdG/giphy.gif)

---

An example of this would be creating different tables that are connected by foreign-keys.
![](https://i.imgur.com/kzMAi15.png)


---

**How would you select cast members for Game of Thrones in season 1?**

___

## Useful resources

-  [Databases: how they work, a a brief history](https://seldo.com/posts/databases_how_they_work_and_a_brief_history) (just the first part of relation and NoSQL
- [NoSQL explained | MongoDB](https://www.mongodb.com/nosql-explained)
- [Why You Should Never Use MongoDB](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/)
