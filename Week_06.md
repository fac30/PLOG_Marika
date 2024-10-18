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


#### 1. Evidence of Learning Outcomes Achieved

### SQL in Execute Program & SQL Workshop
- I learned about the different column types in SQL, specifically `TEXT`, `INTEGER`, and `REAL`.

```sql
exec(`CREATE TABLE cats (name TEXT, age INTEGER)`);
exec(`INSERT INTO cats (name, age) VALUES ('Ms. Fluff', 3)`);
exec(`SELECT * FROM cats`);
```

- **Constraints and Validations**: I explored constraints like `UNIQUE` and how they can ensure data integrity by preventing duplicate entries.

```sql
exec(`CREATE TABLE users (email TEXT UNIQUE, name TEXT)`);
exec(`INSERT INTO users (email, name) VALUES ('amir@example.com', 'Amir')`);
exec(`INSERT INTO users (email, name) VALUES ('amir@example.com', 'Amir')`);
```

- **Setting Up SQLite Database**: I set up a new Node project and used the `better-sqlite3` library to work with a SQLite database. I followed the tutorial to initialise a SQLite database in Node.js, create tables using a SQL schema, and execute SQL queries from JavaScript. This helped me understand how to integrate a relational database with a backend server.

```js
const Database = require("better-sqlite3");
const db = new Database(process.env.DB_FILE);
```

- **CRUD Operations with Prepared Statements**: I practiced implementing CRUD operations by creating prepared statements in Node.js using the `better-sqlite3` library. This involved creating functions to add new tasks, list tasks, and delete tasks from the database.

```js
const insert_task = db.prepare("INSERT INTO tasks (content) VALUES (?)");

function createTask(content) {
  insert_task.run(content);
}
```

- **Implementing Model Functions for Express App**: I applied the learned concepts to complete a database challenge involving an existing Node/Express web app. I wrote model functions for retrieving product information, performing searches, and adding category information.

```js
function listProducts() {
  return db.prepare("SELECT id, name, unit_price, units_in_stock FROM products").all();
}
```

#### 2. Learning Outcomes Struggled With or Need to Revisit

- **Handling NULL Values**: I struggled with understanding how `NULL` values work in SQL, specifically when applying `NOT NULL` constraints. I found it challenging to determine when to use `NULL` versus enforcing constraints, especially when considering real-world applications where missing values may exist.

```sql
exec(`CREATE TABLE users (name TEXT NOT NULL, login_count INTEGER NULL)`);
exec(`INSERT INTO users (name, login_count) VALUES (NULL, NULL)`);
```

- Writing Complex SQL Queries like searching for products by name or calculating stock value was challenging.

```sql
SELECT id, name, unit_price * units_in_stock AS stock_value FROM products;
```
### Project

#### 1. Evidence of Learning Outcomes Achieved

- **Taking on the Scrum Master Role**

Beeing a Scrum Master I focused on establishing an efficient workflow for the project. One of the main tasks was to set up Jira board for our FHR Sprint 1, which required creating epics, tasks, subtasks, and assigning them to team members. The process involved coordinating and ensuring the alignment of the entire team.
<img width="845" alt="Screenshot 2024-10-18 at 16 32 24" src="https://github.com/user-attachments/assets/28da5591-7157-4275-af51-29d8d758fce5">


Setting up and managing the Jira board provided me with a comprehensive understanding of the project workflow, helping me to break down larger objectives into manageable tasks. I gained confidence in using Jira to make our tasks more granular and ensuring to work on the MVP before stratching ourselves.

- **Collaborative Database Schema Creation**

My team and I collaborated to create the database schema for our project, which involved defining relationships between key entities. Initially, the schema design was quite ambitious, but after constructive feedback from our course facilitator, we opted to simplify the structure by removing some tables.
<img width="765" alt="Screenshot 2024-10-18 at 15 01 12" src="https://github.com/user-attachments/assets/1a497edb-9fde-4f5e-a138-4d9ff8675a94">


- **Front-End Project Setup**

I was responsible for setting up the front-end repository, configuring the folder structure, and installing necessary dependencies. This included Vite, Prettier, TypeScript configurations, Tailwind, and Git conventional commit standards.

<img width="139" alt="Screenshot 2024-10-18 at 16 33 47" src="https://github.com/user-attachments/assets/6aa16db8-1072-4bef-a3f4-7a1d2faf6f34">

Configuring these tools helped me improve my understanding of front-end tooling and efficient development processes. It also strengthened my ability to apply standards to ensure consistent and maintainable code across the project.

- **React & Accessibility**:  This week, I successfully refactored key components like `Header`, `Footer`, and `Main` from the homepage into their own files, improving the maintainability and clarity of the app structure. I gained a better understanding of how React’s component-based architecture promotes modularity and reuse. For example, I extracted `IconWithText` from the `Header` component for better flexibility.
        
        ```tsx
  
        const Header = () => {
          return (
            <header className="bg-white p-4 shadow">
              <Logo aria-label="Font Hill Records logo" />
              <SearchBar />
              <div className="flex items-center space-x-4">
                <IconWithText IconComponent={FaUserCircle} label="Account" />
                <IconWithText IconComponent={FaShoppingBag} label="Cart" />
              </div>
            </header>
          );
        };
  
        ```

- **React Router for Navigation**: I wrapped the entire app in `Router` to solve a blank page issue and ensure seamless navigation between different components. Even though the routing logic isn't fully implemented, this work sets up a flexible structure for future expansion.
        
        ```tsx
        <Router>
          <Header />
          <Routes>
            <Route path="/" element={<HomePage />} />
            {/* Other routes will go here */}
          </Routes>
          <Footer />
        </Router>
        ```

- **Accessibility Enhancements**: I added aria labels and descriptive text to the user and cart icons in the `Header` to enhance accessibility. These updates ensure that screen readers can accurately describe elements to visually impaired users.
        
        ```tsx
        <IconWithText IconComponent={FaUserCircle} label="Account" />
        <IconWithText IconComponent={FaShoppingBag} label="Cart" />
        ```

#### 2. Learning Outcomes Struggled With or Need to Revisit
- **Setting Up Jira Board**: Setting up and categorising tasks in Jira was initially challenging, as the interface was less intuitive than expected especially in creating the actual team board.

- **Writing Effective Git Commit Messages**: I initially found it challenging to write commits because the requirement to use specific terminology and maintain a strict format was very difficult at first. However, I apreciate it as it foster etter collaboration and consistency within the team.
This positive effect became evident in writing pull request descriptions, see evedence: 
<img width="971" alt="Screenshot 2024-10-18 at 14 54 06" src="https://github.com/user-attachments/assets/7ee37017-a790-4792-9761-9efffcb87e6c">

- **Linking Navigation to Database Schema**: I started mapping the links in the `NavBar` to the sections defined in our database schema (e.g., Vinyls, Genres, Artists), but I haven’t yet connected these to actual routes or components.
        
        ```tsx
        <Link to="/vinyls">VINYLS</Link>
        <Link to="/artists">ARTISTS</Link>
        ```


### Reflection
- This week, taking on the role of Scrum Master taught me how to balance carefully planing, team delegations with technical contributions. Setting up the project repositories and ensuring consistent standards across the team has provided me a solid foundation for our project and increased my confidence.
- Refactoring the front-end by extracting components like the Header, Footer, and Main sections from HomePage made me more aware of the importance of reusability and maintainability in React. Thinking more granularly about each component helped reduce redundancy. I also added interactive elements, such as user icons and a promotional banner to the Header, enhancing the overall UI/UX. 

What I left behind this week:
- Implementing search functionality.
- Integrating routing with dynamic content based on the database schema.


## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
