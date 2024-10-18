## Guidance
Answer the following questions considering the learning outcomes for
- [Week 06](https://learn.foundersandcoders.com/course/syllabus/developer/week06-project04-databases/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
> **[Learning outcomes...]**  
> [your evidence here]

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]
>


# 1. Evidence of Learning Outcomes Achieved

### SQL in Execute Program & SQL Workshop
- I learned about the different column types in SQL, specifically `TEXT`, `INTEGER`, and `REAL`.

```sql
exec(`CREATE TABLE cats (name TEXT, age INTEGER)`);
exec(`INSERT INTO cats (name, age) VALUES ('Ms. Fluff', 3)`);
exec(`SELECT * FROM cats`);
```

- Constraints and Validations: I explored constraints like `UNIQUE` and how they can ensure data integrity by preventing duplicate entries.

```sql
exec(`CREATE TABLE users (email TEXT UNIQUE, name TEXT)`);
exec(`INSERT INTO users (email, name) VALUES ('amir@example.com', 'Amir')`);
exec(`INSERT INTO users (email, name) VALUES ('amir@example.com', 'Amir')`);
```

- Setting Up SQLite Database: I set up a new Node project and used the `better-sqlite3` library to work with a SQLite database. I followed the tutorial to initialise a SQLite database in Node.js, create tables using a SQL schema, and execute SQL queries from JavaScript. This helped me understand how to integrate a relational database with a backend server.

```js
const Database = require("better-sqlite3");
const db = new Database(process.env.DB_FILE);
```

- CRUD Operations with Prepared Statements: I practiced implementing CRUD operations by creating prepared statements in Node.js using the `better-sqlite3` library. This involved creating functions to add new tasks, list tasks, and delete tasks from the database.

```js
const insert_task = db.prepare("INSERT INTO tasks (content) VALUES (?)");

function createTask(content) {
  insert_task.run(content);
}
```

- Implementing Model Functions for Express App: I applied the learned concepts to complete a database challenge involving an existing Node/Express web app. I wrote model functions for retrieving product information, performing searches, and adding category information.

```js
function listProducts() {
  return db.prepare("SELECT id, name, unit_price, units_in_stock FROM products").all();
}
```

# 2. Learning Outcomes Struggled With or Need to Revisit

- Handling NULL Values: I struggled with understanding how `NULL` values work in SQL, specifically when applying `NOT NULL` constraints. I found it challenging to determine when to use `NULL` versus enforcing constraints, especially when considering real-world applications where missing values may exist.

```sql
exec(`CREATE TABLE users (name TEXT NOT NULL, login_count INTEGER NULL)`);
exec(`INSERT INTO users (name, login_count) VALUES (NULL, NULL)`);
```

- Writing Complex SQL Queries like searching for products by name or calculating stock value was challenging.

```sql
SELECT id, name, unit_price * units_in_stock AS stock_value FROM products;
```


## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
