## Guidance
Answer the following questions considering the learning outcomes for
- [Week 02](https://learn.foundersandcoders.com/course/syllabus/developer/week02-project02-chatbot/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
- Using npm to manage dependencies: I initialised a new Node.js project using `npm init -y`, and then installed the `figlet` module to generate ASCII art. I created a script `asciiArtGenerator.js` to use figlet and write the output to a file called `asciiArt.txt`. After running the script, I could see the generated ASCII art of "Hello World" in `asciiArt.txt`. Here is part of the code:
  ```javascript
  const figlet = require('figlet');
  const fs = require('fs');

  figlet('Hello World', (err, data) => {
    if (err) {
      console.log('Something went wrong...');
      return;
    }
    fs.writeFileSync('asciiArt.txt', data);
  });
  ```

- Setting up an Express server: I created a basic Express HTTP server in the `Work09_NodeAndExpress_YourName` repository. I followed the instructions to define routes that respond to `GET` request, and handle JSON responses. Here is the code for my basic server:
  ```javascript
  const express = require('express');
  const server = express();

  server.get('/', (req, res) => {
    res.send('<h1>Hello from Express</h1>');
  });

  server.listen(3000, () => {
    console.log('Server running on http://localhost:3000');
  });
  ```

  When I visited `http://localhost:3000` in my browser, I saw "Hello from Express" displayed on the page.

  - *Execute Program*: Understanding asynchronous tasks using setTimeout in JavaScript, Managing multiple asynchronous timers, 

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
- Understanding HTTP and Middleware in Express: While working on the second workshop (`Work09_NodeAndExpress_YourName`), I struggled with setting up middleware and handling HTTP POST requests. Initially, I encountered some errors, and my teammate helped me debug.
- I plan to revisit this topic to better understand how middleware works, and I am still not fully comfortable with the HTTP request/response cycle.

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
