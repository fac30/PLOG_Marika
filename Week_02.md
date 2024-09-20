## Guidance
Answer the following questions considering the learning outcomes for
- [Week 02](https://learn.foundersandcoders.com/course/syllabus/developer/week02-project02-chatbot/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
### 1. Show evidence of some of the learning outcomes you have achieved this week.

**Using npm to Manage Dependencies**
- I initialised a Node.js project using `npm init -y` and installed the `figlet` module to generate ASCII art. Below is the code snippet from my script, `asciiArtGenerator.js`, which successfully generated ASCII art and stored it in `asciiArt.txt`:
  
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

**Setting up an Express Server**
- I created a basic Express HTTP server that handles `GET` requests and responds with HTML. Here’s the relevant code snippet:
  
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

**Understanding Asynchronous JavaScript**
- I implemented asynchronous functions using `async/await`, particularly for handling API calls in my Discord bot project. Here’s a simplified example of handling OpenAI responses:
  
  ```javascript
  async function handleOpenAIResponse(message) {
    try {
      const reply = await getOpenAIResponse(message.content);
      await message.channel.send(reply);
    } catch (error) {
      console.error("Error with OpenAI:", error);
      await message.channel.send("There was an error processing your request.");
    }
  }
  ```

**OpenAI Chat Integration**
- I integrated OpenAI's API into my Discord bot to generate dynamic responses based on user inputs. Here’s a concise version of the code demonstrating this integration:
  
  ```javascript
  const completion = await openai.createChatCompletion({
    model: "gpt-3.5-turbo",
    messages: [{ role: "user", content: userInput }],
  });

  return completion.choices[0].message.content;
  ```

**Error Handling and Secure Environment Configuration**
- I ensured secure handling of sensitive data using environment variables and implemented error handling across the bot's functions. Here's a snippet showing secure configuration and error handling:
  
  ```javascript
  import dotenv from 'dotenv';
  dotenv.config();

  async function getOpenAIResponse(messageToAI) {
    try {
      const completion = await openai.createChatCompletion({...});
      return completion.choices[0].message.content;
    } catch (error) {
      console.error("Error with OpenAI API:", error);
      return "Error processing your request.";
    }
  }
  ```

**Project Management**
- To manage the project efficiently, my team and I used a task board and timeline to break down tasks, prioritise them, and track progress(divided into "To Do," "In Progress," and "Done" columns). This structured approach ensured steady progress and timely completion of the project tasks. Additionally, the timeline helped in coordinating tasks with deadlines, ensuring that everything was completed within the set timeframe. 

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to revisit.

**Understanding HTTP and Middleware in Express**
- I struggled with setting up middleware and handling HTTP POST requests during the `Work09_NodeAndExpress_YourName` workshop. Below is the key part of the code where I faced issues:
  
  ```javascript
  server.use(express.json());

  server.post('/data', (req, res) => {
    res.send(`Received: ${req.body}`);
  });
  ```
**Additional notes:**
- Initially, I felt intimidated by the Execute Program concurrency course, so I decided to first complete the related Codecademy courses on Promises and Async-Await. This approach helped me feel more prepared and confident to tackle the Execute Program course.

- Adapting the OpenAI and Discord template code was challenging despite reading the documentation. Pair programming was highly beneficial; my teammate and I collaborated on debugging, refactoring, and modularising the code' files, leading to cleaner and more efficient project outcomes. This experience significantly contributed to my learning progress.

**Project Work Example:**
- **Code Example**: Below is an example from the project code I worked on, which implements Discord’s message components like buttons and handles interactions:

  ```javascript
  import { Events, ActionRowBuilder, ButtonBuilder, ButtonStyle } from "discord.js";

  export default {
    name: Events.InteractionCreate,

    async execute(interaction) {
      if (interaction.isButton()) {
        try {
          if (interaction.customId === "confirm") {
            await interaction.update({ content: "Action confirmed!", components: [] });
          } else if (interaction.customId === "cancel") {
            await interaction.update({ content: "Action cancelled.", components: [] });
          }
        } catch (error) {
          console.error("Interaction update failed:", error);
        }
      }
    },
  };
  ```

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
