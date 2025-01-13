**Assignment: Internet Technology Module - 3**

### 1. How Array Can Be Implemented in PHP (Using Foreach Loop)
In PHP, arrays are a versatile data structure that can store multiple values within a single variable. They play a vital role in managing data efficiently and support various types, including indexed, associative, and multidimensional arrays. Among the many ways to work with arrays, the `foreach` loop is particularly useful for simplifying iteration through array elements.

#### Example of Using Foreach with Indexed Array:
```php
$fruits = array("Apple", "Banana", "Orange");

foreach ($fruits as $fruit) {
    echo "Fruit: $fruit<br>";
}
```
**Detailed Explanation:**
- The `$fruits` array holds three elements: "Apple", "Banana", and "Orange".
- The `foreach` loop takes each value from the array, assigns it to the `$fruit` variable during each iteration, and executes the code inside the loop.
- The result is that each fruit name is printed sequentially, followed by a line break.

#### Example with Associative Array:
```php
$studentMarks = array("John" => 85, "Jane" => 90, "Smith" => 78);

foreach ($studentMarks as $name => $marks) {
    echo "$name scored $marks marks.<br>";
}
```
**Detailed Explanation:**
- The `studentMarks` array consists of key-value pairs where names (keys) are mapped to marks (values).
- The `foreach` loop iterates through each pair, assigning the current key to `$name` and the value to `$marks`, which allows you to display a custom message for each student.

---

### 2. What is Regular Expression
A regular expression (regex or regexp) is a sequence of characters defining a search pattern. They are invaluable in tasks like validating inputs, searching for specific data in strings, or replacing text patterns. Regular expressions are widely supported in PHP via functions like `preg_match` (to check patterns), `preg_replace` (to replace text), and `preg_split` (to split strings).

#### Example:
```php
$email = "test@example.com";
if (preg_match("/^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$/", $email)) {
    echo "Valid email format.";
} else {
    echo "Invalid email format.";
}
```
**Detailed Explanation:**
- **Pattern Breakdown:**
  - `^` and `$` ensure that the match covers the entire string from start to finish.
  - `\w+` matches one or more word characters (letters, digits, and underscores).
  - `@` ensures the string contains an `@` symbol.
  - `[a-zA-Z_]+?` ensures the domain contains only valid letters or underscores.
  - `\.` matches a literal dot.
  - `[a-zA-Z]{2,3}` matches common domain suffixes (e.g., `com`, `org`).
- The example validates email input and provides user feedback based on the match result.

---

### 3. Why Database is Required in Web Application
Web applications need to handle and process large amounts of data dynamically and securely, making databases essential for efficient operation.

#### Reasons for Using Databases in Web Applications:
1. **Dynamic Data Storage:** Databases store dynamic data like user profiles, orders, and blog posts. When a user interacts with the application, the relevant data is retrieved or updated in real-time.
2. **Data Retrieval:** SQL (Structured Query Language) allows specific and efficient data extraction based on conditions, like finding a product by ID.
3. **Security:** Databases provide built-in tools to handle data access controls and encryption to secure sensitive information like passwords and financial data.
4. **Consistency and Integrity:** Through constraints and validation rules, databases ensure that only valid and consistent data gets stored.
5. **Scalability:** Modern databases are designed to handle increasing amounts of data and concurrent user access as applications grow.

---

### 4. Steps to Create a Database, Additional Tables, Insert Rows, and Display Results in phpMyAdmin
phpMyAdmin is an intuitive graphical interface for managing MySQL databases without needing command-line interactions.

#### Steps:
1. **Creating a Database:**
   - Log in to phpMyAdmin.
   - Click "New" in the left navigation pane.
   - Enter a database name (e.g., `schoolDB`) and click "Create".

2. **Adding a Table:**
   - Select the database you just created.
   - Click "Create Table" and specify a table name (e.g., `students`).
   - Define columns with attributes like name, data type (e.g., `INT`, `VARCHAR`), and constraints (`Primary Key`, `Not Null`).

3. **Inserting Rows:**
   - Go to the "Insert" tab of your table.
   - Fill in the column values (e.g., ID = 1, Name = "John", Marks = 85) and click "Go".

4. **Displaying Data:**
   - Use the "SQL" tab to execute queries:
     ```sql
     SELECT * FROM students;
     ```
   - View the query result, which lists all rows and their respective columns in the table.

---

### 5. How Can We Connect MySQL with PHP
PHP facilitates interaction with MySQL databases through extensions like MySQLi (Improved) and PDO (PHP Data Objects). 

#### Example Using MySQLi:
```php
$servername = "localhost";
$username = "root";
$password = "";
$database = "schoolDB";

// Create Connection
$conn = new mysqli($servername, $username, $password, $database);

// Check Connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

echo "Connected successfully!";
```
**Explanation:**
- The `new mysqli` object is instantiated with the database server’s details.
- If the connection is unsuccessful, the script halts with an error message.
- A successful connection prints a success message and allows further operations.

---

### 6. What is CRUD Operation on MySQL
CRUD refers to the basic operations of Create, Read, Update, and Delete performed on databases.

#### CRUD Overview:
1. **Create:** Add new records to a table.
   ```sql
   INSERT INTO students (id, name, marks) VALUES (1, 'John', 85);
   ```

2. **Read:** Retrieve data from the database.
   ```sql
   SELECT * FROM students;
   ```

3. **Update:** Modify existing records.
   ```sql
   UPDATE students SET marks = 90 WHERE id = 1;
   ```

4. **Delete:** Remove specific records.
   ```sql
   DELETE FROM students WHERE id = 1;
   ```

---

### 7. What is JavaScript
JavaScript is a versatile scripting language that enhances interactivity and functionality in web applications. Unlike server-side languages like PHP, JavaScript operates directly in the browser, allowing real-time interactivity.

#### Features:
- **Dynamic Content:** Update web page elements dynamically without reloading the entire page.
- **DOM Manipulation:** Access and modify HTML and CSS on-the-fly.
- **Event Handling:** Respond to user actions like clicks, key presses, or mouse movements.
- **Cross-Browser Compatibility:** Widely supported across web browsers.

#### Example:
```html
<button onclick="showMessage()">Click Me</button>
<script>
function showMessage() {
    alert("Hello! Welcome to JavaScript.");
}
</script>
```
---

### 8. How Validation is Checked Using JavaScript (Email Validation)
Validation ensures that user inputs meet specific criteria before being submitted to a server. Using JavaScript, validations like checking for a correctly formatted email can be done on the client side.

#### Example of Email Validation:
```html
<form onsubmit="return validateEmail()">
    <label for="email">Email:</label>
    <input type="text" id="email" name="email">
    <button type="submit">Submit</button>
</form>
<script>
function validateEmail() {
    let email = document.getElementById("email").value;
    let regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

    if (!regex.test(email)) {
        alert("Invalid email address!");
        return false;
    }
    alert("Valid email address.");
    return true;
}
</script>
```
**Detailed Explanation:**
- The `regex` pattern checks for a proper email format with characters before and after the `@` symbol and a domain extension.
- If the input is invalid, the `alert` function notifies the user and form submission is halted.

