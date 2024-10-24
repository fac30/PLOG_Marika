## Guidance
Answer the following questions considering the learning outcomes for
- [Week 07](https://learn.foundersandcoders.com/course/syllabus/developer/week07-project04-authentication/learning-outcomes/)

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

# Project

### 1. Evidence of Learning Outcomes Achieved

- I extended the shopping cart functionality by storing cart items in `localStorage` and updating the cart count dynamically across components like the `Header` and `ShopCart`.
Managing cart state with `localStorage` improved the user experience by persisting the cart data across sessions. It also helped me better understand state management in React.
  
  ```tsx
  const addToCart = (product: Vinyl) => {
    const existingProductIndex = cartItems.findIndex(item => item.id === product.id);
    let updatedCart;
    if (existingProductIndex >= 0) {
      updatedCart = cartItems.map((item, index) => {
        if (index === existingProductIndex) {
          return { ...item, quantity: item.quantity + 1 };
        }
        return item;
      });
    } else {
      updatedCart = [...cartItems, { ...product, quantity: 1 }];
    }
    setCartItems(updatedCart);
    const newCartCount = updatedCart.reduce((acc, item) => acc + item.quantity, 0);
    setCartCount(newCartCount);
    localStorage.setItem("shoppingCart", JSON.stringify(updatedCart));
  };
  ```

- I fixed an issue where the cart count in the header did not accurately reflect the total quantity of items. By using the `reduce` method, I ensured the total items in the cart were calculated correctly. Although I resolved the cart count issue, It doesn't work correctly when the user go back to homepage.

```tsx
const Header = () => {
  const cartContext = useContext(CartContext);

  const totalItems = cartContext?.cartItems.reduce((acc, item) => acc + item.quantity, 0);

  return (
    <header>
      <IconWithText label={`Cart (${totalItems})`} />
    </header>
  );
};
```


- I extracted the `Quantifier` and `TotalPrice` components from the shopping cart to promote modularity and reusability. This helped to simplify the structure of my components and made the code more maintainable.

```tsx
const Quantifier = ({ quantity, onIncrease, onDecrease }: QuantifierProps) => (
  <div>
    <button onClick={onDecrease}>-</button>
    <span>{quantity}</span>
    <button onClick={onIncrease}>+</button>
  </div>
);

const TotalPrice = ({ amount }: TotalPriceProps) => (
  <div>
    <p>Total: £{amount.toFixed(2)}</p>
  </div>
);
```

- I customised the Tailwind theme to ensure consistent and accessible color schemes for text, background, and error states. This allowed me to maintain a consistent design across the website.

```js
theme: {
  extend: {
    colors: {
      primary: '#004BBD',
      accent: '#F97316',
      text: { primary: '#000000', secondary: '#4B5563' },
      background: { light: '#F6E9E9', default: '#FFFFFF', footer: '#B55252' },
      error: '#DC2626',
    },
  },
},
```

- Implemented navigation across pages using React Router, enabling seamless transitions between components like` Home`, `UserLogin`, and `ShopCart`. This improved the user experience by allowing navigation without page reloads.ying React Router, I improved my understanding of client-side routing, ensuring a better user experience by navigating without reloading the page.
  
Implementing React Router helped me better understand client-side routing and navigation within React. However, in one case, I replaced the `navigate` route with `<Link to={to}>` for better navigation handling.

```tsx
import { Link } from 'react-router-dom';

type IconWithTextProps = {
  IconComponent: React.FC<{ size: number }>;
  label: string;
  to: string;
  onClick?: () => void;
};

const IconWithText = ({ IconComponent, label, to, onClick }: IconWithTextProps) => {
  return (
    <Link to={to}>
      <button
        type="button"
        onClick={onClick}
        .........
```

### 2. Learning Outcomes Struggled With or Need to Revisit

- I decided to focus solely on React this week and left behind accessibility and responsiveness across multiple devices.

# Reflection + Next Step

This week, I made solid progress with the UI and shopping cart functionality, improving state management using React hooks and `localStorage`. The focus on reusable components and Tailwind CSS theme customization was crucial in building a scalable and maintainable codebase.

However, managing state across multiple components highlighted the limitations of my current approach, and I will need to refactor the shopping cart state management using React Context and `useReducer` for improved scalability and maintainability.

# SQL

## 1. Evidence of Learning Outcomes Achieved

- I learnt SQL commands for deleting data (`DELETE`) and dropping tables (`DROP TABLE`). I learned how to remove specific rows from a table using the `WHERE` clause and delete entire tables when necessary.

```sql
DELETE FROM users WHERE name = 'Betty';
```

- I learned how to define default values and constraints when creating SQL tables, which helps enforce data integrity and simplifies the insertion process.

```sql
CREATE TABLE users (
  name TEXT,
  login_count INTEGER NOT NULL DEFAULT 0
);
```

- I explored how to reference other tables using foreign keys to maintain referential integrity in a relational database.

```sql
CREATE TABLE people (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);

CREATE TABLE cats (
  owner_id INTEGER REFERENCES people(id),
  name TEXT NOT NULL
);
```

## 2. Learning Outcomes Struggled With or Need to Revisit

Complex Relationships and Foreign Keys: Although I grasped the basics of foreign keys, I found it challenging to manage complex relationships and cascading actions when deleting or updating records. I plan to explore advanced options like ON DELETE CASCADE to handle these scenarios more effectively.

SQL Injection Prevention: I understand the principles behind SQL injection attacks and the need to use parameterized queries. However, I struggled to put this into practice consistently and recognize when to apply it.


# **Authentication**

I struggled a lot with this topic. Although I understand the importance of user authentication, I found it difficult to finish the workshop, and I haven’t implemented it in my weekly project.
I struggled particularly with session creation, user registration, and secure log-in/out functionality.


## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
