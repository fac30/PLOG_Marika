## Guidance
Answer the following questions considering the learning outcomes for
- [Week 04](https://learn.foundersandcoders.com/course/syllabus/developer/week04-project03-frontend/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
> **[Learning outcomes...]**  
> [your evidence here]
-  I worked on building functional components in React and passing props to make them dynamic.
Started with the React workshop: I created a Greeting component that takes a name as a prop and displays it on the page.
```
function Greeting(props: {name: string}) {
    console.log(props);  // Logs the props, {name: "oli"}
    return <p>Hello {props.name}</p>;  // Displays "Hello oli"
}
```
- I learned how to handle side-effects and manage global state using useEffect. I built logic to fetch quiz questions and answers from an API and set that data in the component’s state. Here’s how I fetched the quiz data when the component first loads:
```
useEffect(() => {
  const fetchQuestions = async () => {
    try {
      const questionsResponse = await fetch('http://localhost:3000/questions');
      const questionsData = await questionsResponse.json();
      setQuestions(questionsData);
    } catch (error) {
      setError('Failed to fetch questions or answers.');
    }
  };
  fetchQuestions();
}, []);
```
- Backend Code Example:

```
import cors from 'cors';

const corsOptions = {
  origin: 'http://localhost:5173',  // Frontend URL
  methods: ['GET', 'POST', 'PATCH', 'DELETE'],  // Allowed methods
  credentials: true,  // Allow credentials like cookies
};

app.use(cors(corsOptions));
```
This was a great learning experience in connecting the front and back ends, especially ensuring that CORS was properly configured for data fetching.


- I set up routing for my app so users can move between different pages without a full page refresh. I used React Router to navigate from the homepage to the quiz explore page.
 ```
import { BrowserRouter as Router, Route, Routes, useNavigate } from "react-router-dom";

const navigate = useNavigate();
const goToExplore = () => navigate('/explore');
<Button onClick={goToExplore} text="Explore quizzes" />;
```
- I got more comfortable using TypeScript with React by creating reusable components with type safety. For example, I built a custom Button component that accepts both custom props and standard HTML attributes.
```
interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  text: string;                     
  onClick: () => void;               
  buttonName: string;                  
  type: 'button'
}
```

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]

- I ran into issues with TypeScript’s type inference, especially when working with quiz results. I kept getting errors like never[] because I didn’t define the types correctly from the start. Here’s an interface I defined for quiz results:
```
  interface QuizResult {
  questionId: number;
  correct: boolean;
}
const resultsJson: QuizResult[] = [];
```

-  I encountered some frustrating issues where variable name conflicts led to errors on the webpage. In some cases, I didn’t pass the correct props, which broke certain components.

- I had some difficulties implementing page navigation. React Router worked well, but getting everything set up and pass props propely was difficult and led to errors.

### 3. Bonus
When I get more comfortable with React, I’d like to focus on building accessible applications. I know it’s an important aspect of web development, and I’m keen to learn more about how to properly implement accessibility features in my components.


## Feedback (For CF's)
> [**Course Facilitator name**]

Alexander

> [*What went well*]

Excellent. I loved how you explained your learnings and the code snippets. Everything is quite concise and right to the point

> [*Even better if*]
