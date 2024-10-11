## Guidance
Answer the following questions considering the learning outcomes for
- [Week 05](https://learn.foundersandcoders.com/course/syllabus/developer/week05-project03-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
> **[Learning outcomes...]**  
> [your evidence here]

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]

### Project
- **Back-Backend**
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
 
  - Refactored the backend `quizLogic` code, improving its structure and functionality. Removed unnecessary processing of `strength` and `weakness` in answers, correcting typos and undeclared variables for better code quality.

  - Introduced a generic `shuffledArray` function to enhance array randomization, allowing for flexibility with different data types:
    ```typescript
    function shuffledArray<T>(array: T[]): T[] {
    }
    ```
    This implementation reinforced my understanding of generics in TypeScript and how they enhance code reusability.

  - Implemented a `writeResults` function to save quiz results to a JSON file:
    ```typescript
    function writeResults(results: QuizResult[]): void {
      fs.writeFileSync(
        path.join(__dirname, "../../data/results.json"),
        JSON.stringify(results, null, 2)
      );
    }
    ```
    This helped me grasp file handling and data storage practices in Node.js.

- **Frontend-Backend**
  - Learned from my colleague how to implement local storage:
    ```typescript
    const handleClick = () => {
      if (quizName) {
        localStorage.setItem('quizTitle', quizName);
      }
      navigate(path);
    };
    ```
   I then Retrieved and displayed the stored quiz name on the Result Page:
    ```typescript
    useEffect(() => {
      const storedQuizName = localStorage.getItem('quizTitle');
      if (storedQuizName) setQuizName(storedQuizName);
    }, []);
    ```
  

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
 
  - Initially utilised a generic endpoint `http://localhost:3000/questions?`. With guidance from my colleague, I understand why I had to include quiz ID for more specific data retrieval:
    ```typescript
    http://localhost:3000/questions?quizId=${quizId}
    ```
  - Faced challenges ensuring data consistency between backend and frontend. Iteratively improved API calls and data handling to achieve better synchronisation.
  - I didn't consider accessibility at all while working on the project. I focused on aesthetics and deactivated the focus option on buttons during styling, which I plan to address moving forward.


### Cypress
- Successfully installed Cypress in my project using npm, despite encountering some initial dependency conflicts.  
- I completed the courses on [Cypress learning platform ](https://learn.cypress.io/#courses) including "Testing Your First Application," "Testing Foundations," "Cypress Fundamentals," and "Advanced Cypress Testing Concepts." These courses provided me with a comprehensive overview of Cypress capabilities.

##### Struggles
- Encountered challenges resolving dependency conflicts during Cypress installation, particularly between the required TypeScript version for `react-scripts` and the installed version:
  
  ```
  npm error code ERESOLVE
  npm error ERESOLVE could not resolve
  npm error While resolving: react-scripts@3.4.4
  npm error Found: typescript@4.9.5
  ```
I had to downgrade TypeScript to a version compatible with `react-scripts`, highlighting the importance of careful dependency management.

- While I successfully completed the Cypress courses and understood the concepts, I haven't yet fully applied this knowledge to my own project. 

### AWS
- I successfully launched an EC2 instance and configured security groups to allow SSH and HTTP traffic on `port 3000`. This allowed me to host my backend project.
- After transferring my project files to the EC2 instance using scp, I installed dependencies and ran the project. The server started on `localhost:3000` initially, and I attempted to configure it to run on 0.0.0.0:3000 to make it accessible externally.
- I worked on a separate aws branch in my backend project and pushed changes to GitHub. I pulled these changes onto the EC2 instance to deploy them.

- Issue with Server Binding:  
  The BIG challenge was getting the server to bind to 0.0.0.0 instead of localhost. Initially, the server was only accessible within the EC2 instance. Despite trying several fixes, the server remained bound to localhost:3000, preventing external access.

- Syncing GitHub Branches and Deployment:  
  I encountered issues with syncing my aws branch from my local machine to the EC2 instance. Changes that I made locally were not correctly reflected after being pulled onto the EC2 instance, and ultimately, I was unable to deploy the backend of my project.  
![Screenshot_2024-10-11_at_13 20 35](https://github.com/user-attachments/assets/da2d4556-e529-4f8d-8869-99536479797a)



## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
