## Guidance
Answer the following questions considering the learning outcomes for
- [Week 08](https://learn.foundersandcoders.com/course/syllabus/developer/week08-project04-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
> **[Learning outcomes...]**  
> [your evidence here]

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]

## React 
#### 1. Evidence of Learning Outcomes Achieved

- **Implementing Global State Management with React Context**: Implemented global state management with React Context to manage the shopping cart state across components (`ProductCard`, `ShopCart`, `Header`). Using `useReducer`, I centralised cart actions, including adding, removing, and updating quantities.

    ```javascript
    import { createContext, useContext, useReducer } from "react";

    const CartContext = createContext({ state: initialState, dispatch: () => null });

    const cartReducer = (state, action) => {
      switch (action.type) {
        case "ADD_TO_CART":
          // logic to add item
        case "DECREASE_QUANTITY":
          // logic to decrease item quantity
        default:
          return state;
      }
    };

    export const CartProvider = ({ children }) => {
      const [state, dispatch] = useReducer(cartReducer, initialState);
      return (
        <CartContext.Provider value={{ state, dispatch }}>
          {children}
        </CartContext.Provider>
      );
    };
    ```

- **Creating a Custom Hook for Context Access**: Developed a custom hook, `useCartContext`, to simplify accessing cart state and actions across components. 

    ```typescript
    export const useCartContext = () => {
      const context = useContext(CartContext);
      if (!context) {
        throw new Error("useCartContext must be used within a CartProvider");
      }
      return context;
    };
    ```

- **TypeScript Type Safety and Component Refactoring**: IrRefactored several components, and it was a long job, to ensure TypeScript type safety. Below an example of how I defined interfaces for props and state to eliminate implicit `any` types, reducing potential runtime errors.


    ```typescript
    interface CartItem {
      id: string;
      name: string;
      price: number;
      quantity: number;
    }

    interface CartState {
      items: CartItem[];
      totalAmount: number;
    }

    const initialState: CartState = {
      items: [],
      totalAmount: 0,
    };
    ```

- **Implemented Cart Summary with Dynamic Shipping Options**: Based on feedback from Max, I updated the `CartSummary` component to fetch shipping options from the database. Now users can select a preferred option, which then adjusts the delivery charge and total price.

    ```typescript
    useEffect(() => {
      fetch('http://localhost:3000/shipping-options')
        .then(response => response.json())
        .then(data => setShippingOptions(data))
        .catch(error => console.error('Error:', error));
    }, []);
    ```


#### 2. Learning Outcomes Struggled With or Need to Revisit

- I initially struggled to decide between `useState` and `useReducer` for managing cart state. I eventually chose `useReducer` to handle the cart's complex logic.


    ```javascript
    const cartReducer = (state, action) => {
      switch (action.type) {
        case "ADD_TO_CART":
          // logic for adding item
        default:
          return state;
      }
    };
    ```


- **Managing Type Conflicts with TypeScript Prop Interfaces**: Encountered TypeScript errors when passing complex objects, such as social media icons, as props in components. Initially defined `name` as a `string`, which caused conflicts when JSX elements were passed. Adjusted `name` to `React.ReactNode`, which resolved the issue.
  - **Code Example**:

    ```typescript
    const socialLinks = [
      { name: <FaFacebookF />, url: "https://www.facebook.com" },
      { name: <FaTwitter />, url: "https://www.twitter.com" },
    ];
    ```
    
- **Managing Type Conflicts with TypeScript Prop Interfaces**: Encountered TypeScript errors when passing objects, such as social media icons, as props in components. Initially defined `name` as a `string`, which caused conflicts when JSX elements were passed. Adjusted `name` to `React.ReactNode`, which resolved the issue.

    ```typescript
    const socialLinks = [
      { name: <FaFacebookF />, url: "https://www.facebook.com" },
      { name: <FaTwitter />, url: "https://www.twitter.com" },
    ];
    ```


## Deployment
#### 1. Evidence of Learning Outcomes Achieved

- **Automating Frontend Deployment with GitHub Actions and AWS CDK**: Configured an automated deployment pipeline using GitHub Actions and AWS CDK for the frontend. The pipeline builds, tests, and deploys the application to an AWS S3 bucket. The CI/CD process has made deployments quicker and more reliable.

    ```yaml
    name: Frontend Deployment
    on:
      push:
        branches:
          - main
    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout code
            uses: actions/checkout@v2
          - name: Install dependencies
            run: npm install
          - name: Build frontend
            run: npm run build
          - name: Deploy to S3
            env:
              AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
              AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
            run: aws s3 sync ./dist s3://my-bucket-name --delete
    ```


- **AWS Deployment and EC2 Configuration**: Successfully deployed the backend using EC2 and configured `pm2` for process management.

    ```typescript
    const app = new cdk.App();
    new Pro04BackendCdkStack(app, 'Pro04CdkStack', {
      env: { account: 'account-id', region: 'eu-west-2' }
    });
    app.synth();
    ```

### 2. Learning Outcomes Struggled With or Need to Revisit

- **TypeScript Compilation in GitHub Actions**: I realised that TypeScript configuration in `tsconfig.json` needed adjustments. This issue was evident by GitHub Actions not recognising type declarations during deployment, which required adding steps to ensure TypeScript compiles correctly in the CI environment.

- **Troubleshooting AWS CDK Stack Rollbacks and Updates** : Had an `UPDATE_ROLLBACK_FAILED` error during deployment, which prevented the CloudFormation stack from updating. I decided to manually deleting the stack, and retrying deployment, but I failed to do so and gave up.
<img width="945" alt="Screenshot 2024-10-29 at 16 53 10" src="https://github.com/user-attachments/assets/abdde838-c2a4-4ac2-9671-69bad0cc8242">


- Faced TypeScript compilation errors in the CI pipeline due to missing module declarations, specifically `aws-cdk-lib`. This required adjusting TypeScript settings and ensuring that all necessary dependencies were installed in the CI environment.
![Screenshot%202024-10-29%20at%2014 24 56](https://github.com/user-attachments/assets/376a150f-0f1b-42a3-ac2b-7e6971231aff)


- **Mistakenly Running Backend on an Incorrect Machine**: Accidentally ran the backend on the wrong computer, leading to confusion and deployment delays.



## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
