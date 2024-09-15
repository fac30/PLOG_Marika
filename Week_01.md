## Guidance

Answer the following questions considering the learning outcomes for

- [Week 01](https://learn.foundersandcoders.com/course/syllabus/developer/week01-project01-basics/learning-outcomes/)
  
Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

Assessment
1. Show evidence of some of the learning outcomes you have achieved this week.
### Accessibility
I ensured that semantic HTML elements such as `<header>`, `<main>`, `<section>`, `<form>`, and `<footer>` were used correctly to make the structure clearer for screen readers.
```
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width-device-width, initial-scale=1" />
    <title>My Messy Site</title>
    <link href="challenge.css" rel="stylesheet" />
  </head>

  <body>
    <header>
    <h1>My Messy Site</h1>
    <p>I Love Coding</p>
  </header>

    <img src="./catonkeyboard.jpeg" alt="My cat sitting on my keyboard"/>
    

    <section>
      <h2>First Section Header</h2>

      <p>
      </p>
    </section>
    
    <section>
      <h2>Second Section Header</h2>

      <p>
      </p>
    </section>
    
    <form action="/" method="post">
      <label for="first-name">First Name</label>
      <input id="first-name" type="text" />

      <label for="last-name">Last Name</label>
      <input id="last-name" type="text" />

      <label for="email">Email</label>
      <input id="email" type="email" />

      <label for="password">Password</label>
      <input id="password" type="password" />
      <button type="button">Submit</button>
    </form>

    <footer>Copyright John 2015. All rights reserved</footer>
  </body>
</html>

```
2. **Ensure a web page is readable for screen readers**
   - I used appropriate labeling and aria attributes where needed to ensure that elements are accessible by screen readers. For example:

   ```html
   <button aria-label="Toggle navigation menu">
     <svg id="openIcon" aria-hidden="true">...</svg>
   </button>
   ```

3. **Tools used to check accessibility**
   - Chrome's Lighthouse helped with checking for screen reader compatibility, keyboard navigation, and contrast issues.
  
### Design
- I used Flexbox to layout elements in a row and align them effectively. For example:
   
   ```css
   header {
     display: flex;
     justify-content: space-between;
     align-items: center;
   }
   ```

   - I used CSS Grid to create a responsive gallery layout. Here’s an example:
   
   ```css
   .grid {
     display: grid;
     grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr));
     gap: 1rem;
   }
   ```

### Workflow
  - I structured my commits logically, ensuring that each change was meaningful and related to a specific task.

### HTML Forms
 - I used correct input types for collecting different information (e.g., `email`, `tel`, `password`):
   
   ```html
   <form>
     <label for="email">Email</label>
     <input type="email" id="email" name="email" required />

     <label for="tel">Telephone</label>
     <input type="tel" id="tel" name="tel" required />
   </form>
   ```
- I included proper labels for each form input and used `fieldset` and `legend` to group radio buttons for accessibility:
   
   ```html
   <fieldset>
     <legend>Preferred contact method</legend>
     <label for="contact-email">Email</label>
     <input id="contact-email" type="radio" name="contact" value="email" />
   </fieldset>
   ```

2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
#### **CSS Stack Layout**
I struggled on creating layouts using the **CSS stack utility** (specifically stacking elements vertically with different gap sizes).

#### **JavaScript Arrays (Execute Program)**
I’ve struggled with some of the **JavaScript array exercises** in **Execute Program**. Specifically, I’m finding it challenging to remember all the different methods like `splice()`, `push()`, and `shift()`, `map()`, `filter()`, and `slice()`.

Feedback (For CF's)
[Course Facilitator name]
[What went well]
[Even better if]
