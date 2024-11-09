## Guidance
Answer the following questions considering the learning outcomes for Week 09

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
- This week, I learnt PHP fundamentals through Laracasts course. I practiced using basic data types, operators, and functions like `isset`, `empty`, and array manipulation functions. PHP’s syntax feels somewhat more verbose than JavaScript

-   While working on the basics of PHP, I implemented CRUD operations for a notes application, which required manipulating data structures.

```php
$note = $db->query('select * from notes where id = :id', [
    'id' => $_GET['id']
])->findOrFail();

```


- I implemented a service container pattern, binding classes like `Database` to a container for centralised dependency management. This made the code more modular and organised.

```php
$container->bind('Core\\Database', function () {
    $config = require base_path('config.php');
    return new Database($config['database']);
});
App::setContainer($container);

```

- I learnt how to implement a custom routing system to controllers and handling HTTP methods:

```php
$router->get('/note', 'controllers/notes/show.php');
$router->post('/notes', 'controllers/notes/store.php');

```

In the **controller** folder, I used the `index.php` file to render views with dynamic data. This was achieved with the `view()`function, which loads the specified view file and allows passing data (e.g., `heading`):

```php
view("index.view.php", [
    'heading' => 'Home',
]);

```

  
- I used PHP superglobals such as `$_GET`, `$_POST`, `$_SESSION`. I practiced handling form submissions using` $_POST` and dynamically updating pages using `$_GET`. These superglobals remind me of JavaScript’s localStorage but feel more integrated into server-side data handling.
- **Form handling**: I used `htmlspecialchars` and `filter_var` to sanitize and validate input fields, which I learned is essential for preventing common security issues.

See two examples of these concepts:

```php
<?php
if (isset($_POST['submit'])) {
    $name = htmlspecialchars($_POST['name']);
    echo "Hello, $name!";
}
?>
```


```php
<?php
$email = filter_var($_POST['email'], FILTER_SANITIZE_EMAIL);
if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Valid email: $email";
} else {
    echo "Invalid email format.";
}
?>
```

- Lambda functions in PHP are unnamed, quick functions, similar to JavaScript arrow functions.
    
    ```php
    $addNumbers = function($a, $b) {
        return $a + $b;
    };
    
    ```


 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
- Following the tutorial’s rapid refactoring presented challenges. Frequent changes caused breaking points, making debugging difficult and make difficult to understand the logic of each modification.

- Implementing basic authorization was manageable, but understanding secure access control and validating user permissions was challenging.

- Namespaces were particularly challenging to implement in my code structure. They helped in organising classes and avoiding conflicts, especially when multiple classes had similar names. However, the concept was intruduce while my project was broken due to route refactoring process.

```php
// File: Core/Database.php
namespace Core;

class Database {
    public function connect() {
        // Connection logic here
    }
}

// Accessing the Database class with a namespace
use Core\Database;

$db = new Database();
$db->connect();
 ```

### 3. Other concepts I learnt: 
Debugging Tools: 
**`var_dump()`**: Outputs detailed information about variables, useful for debugging.
**`echo`**: Prints simple outputs, often for displaying text or values.
**`die()`**: Halts execution, commonly used after errors to prevent further processing.

- **Classes and objects** allow for modular, secure code. Visibility keywords (`public`, `private`) control access to class members.

- **`__construct`**: Special function that initialises class objects, similar to constructors in JavaScript.

- **`namespac`** helps organise and avoid naming conflicts, particularly in larger applications.

- **String Concatenation**: Concatenate strings with the `.` operator, e.g., `$fullName = $firstName . " " . $lastName;`, akin to `+` in JavaScript.

- **`__DIR__`** returns the directory of the current file, useful for setting relative paths.

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
