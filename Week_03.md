## Guidance
Answer the following questions considering the learning outcomes for
- [Week 03](https://learn.foundersandcoders.com/course/syllabus/developer/week03-project03-server/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
> **[Learning outcomes...]**  
> [your evidence here]
- Successfully installed and managed Node.js versions using `nvm`.
  
- Configured an Express.js project for secure environment variable management using `dotenv` and verified successful integration.

- Set up and configured `tsconfig.json` to ensure the TypeScript compiler properly handles the project.

- Structured a TypeScript-based Express application and confirmed the successful initialization of the Express server.

- Installed TypeScript and the necessary packages using the following command:

    ```bash
    npm install -D typescript @types/express @types/node ts-node nodemon
    ```

- **TypeScript vs. JavaScript:** Completed 60% of the TypeScript basics on Execute Program, gaining a solid understanding of the advantages of TypeScript over JavaScript. TypeScript’s static typing allows errors to be caught at compile time rather than runtime, significantly reducing bugs and improving code quality and maintainability.

- Developed a POST endpoint for saving answers to a JSON file. Debugged and fixed issues related to missing method implementations.

    ```typescript
    // Pushing new answer to the existing JSON data
    const newAnswer = new Answer(req.body.id, req.body.questionId, req.body.text, req.body.isCorrect);
    answers.push(newAnswer);
    ```
- Tested the POST endpoint using the following `curl` command:

    ```bash
    curl -X POST http://localhost:3000/users \
    -H "Content-Type: application/json" \
    -d '{"id": 3, "name": "User3", "points": 50}'
    ```

- Integrated `nodemon` for automatically restarting the server during development, enhancing productivity by allowing rapid feedback without manually restarting the server after each change.

    ```bash
    npm run dev
    ```

- Used Jira for the first time to manage project tasks, track progress, and collaborate with the team.
<img width="1036" alt="Screenshot 2024-09-24 at 23 58 46" src="https://github.com/user-attachments/assets/53778add-9583-4b69-a445-dde34b74f03c">


 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]
- **TypeScript:**
    - Initially struggled with understanding the TypeScript compilation process but eventually gained clarity on the importance of the `dist` directory.

    - Found tuples challenging; plan to revisit and practice more examples.

    - Mistakenly installed dependencies globally, which caused issues. Learned the importance of adhering to best practices by using local installations.

    - Faced challenges with merge conflicts during team collaboration, which caused delays and required additional effort to ensure everyone’s changes were successfully integrated.

    - Found it challenging to implement and understand asynchronous file operations with callbacks in TypeScript. 

    ```typescript
    // Handling file read and write operations with callbacks
    fs.readFile(userFilePath, 'utf8', (err, data) => {
      if (err) return callback(err);
      const users: User[] = JSON.parse(data);
      users.push(this);
      fs.writeFile(userFilePath, JSON.stringify(users, null, 2), callback);
    });
    ```

- **Database:**
    - Implemented a method to save user data to a JSON file, handling file system operations and asynchronous callbacks.

    ```typescript
    // Ensuring directory and file exist before saving data
    if (!fs.existsSync(userFilePath)) {
      fs.writeFileSync(userFilePath, '[]');
    }
    ```

- **Database Design Challenges:**
    - Encountered significant challenges in designing mock databases, particularly in setting up relationships between data entities. The large volume of manual data entry was overwhelming and decided to cut it down.
<img width="287" alt="Screenshot 2024-09-25 at 22 09 20" src="https://github.com/user-attachments/assets/76490c6a-2b31-4a30-94e6-a562ff905593">


Here an example of the answer.json file
```typescript
  {
    "id": 1,
    "questionId": 1,
    "text": "Marika",
    "isCorrect": true
  },
 ```

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
