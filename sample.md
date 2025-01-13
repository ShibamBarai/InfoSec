**Assignment: Internet Technology Module - 2**

### 1. Different Types of HTML Tags
HTML (HyperText Markup Language) serves as the foundation of web development, enabling the creation and design of structured web pages. It is made up of tags, which dictate how different elements of a webpage are displayed. Tags are enclosed within angle brackets `<>` and are mostly used in pairs: opening `<tag>` and closing `</tag>`. Some tags, like `<img>`, are self-closing, requiring no closing counterpart.

#### Detailed Explanation of Common HTML Tags:

1. **Structural Tags:**
   - `<html>`: Specifies the root element of an HTML document.
   - `<head>`: Encapsulates metadata like title, linked CSS files, or JavaScript files.
   - `<body>`: Contains the content displayed on the webpage, such as text, images, and videos.

2. **Heading Tags:**
   - `<h1>` to `<h6>`: Used to define headings. The `<h1>` tag represents the largest heading, while `<h6>` denotes the smallest.
     ```html
     <h1>Primary Heading</h1>
     <h3>Subheading</h3>
     ```

3. **Text and Formatting Tags:**
   - `<p>`: Used for defining paragraphs.
   - `<b>` or `<strong>`: Renders bold text, emphasizing its importance.
   - `<i>` or `<em>`: Italicizes text.
   - `<u>`: Underlines the text for emphasis.
     ```html
     <p>This is a <strong>bold</strong> paragraph.</p>
     ```

4. **Link and Media Tags:**
   - `<a>`: Creates hyperlinks to navigate between webpages or external sites.
     ```html
     <a href="https://example.com">Visit Our Website</a>
     ```
   - `<img>`: Adds images to the page.
     ```html
     <img src="image.jpg" alt="A Sample Image">
     ```
   - `<video>` and `<audio>`: Used for embedding video and audio content, respectively.

5. **List Tags:**
   - `<ul>`: Creates bulleted unordered lists.
   - `<ol>`: Creates numbered ordered lists.
   - `<li>`: Represents individual items within lists.
     ```html
     <ul>
       <li>First Item</li>
       <li>Second Item</li>
     </ul>
     ```

6. **Form Tags:**
   - `<form>`: Facilitates user input submission through forms.
   - `<input>`: Represents input fields, like text or passwords.
   - `<button>`: Adds buttons users can click on.
     ```html
     <form action="submit.php">
       <input type="text" name="username">
       <button>Submit</button>
     </form>
     ```

7. **Table Tags:**
   - `<table>`: Organizes data in rows and columns.
   - `<tr>`: Defines table rows.
   - `<td>`: Represents columns (or cells).
     ```html
     <table>
       <tr>
         <td>Cell 1</td>
         <td>Cell 2</td>
       </tr>
     </table>
     ```

---

### 2. What is CSS and DIV

#### CSS (Cascading Style Sheets):
CSS is used to separate content structure from design in web development. This allows easy styling and layout management of web pages.

- **Types of CSS with Examples:**
  1. **Inline CSS:** Applied directly to HTML tags using the `style` attribute. This is ideal for applying styles to specific elements quickly.
     ```html
     <p style="color: red;">This is a red paragraph.</p>
     ```
  2. **Internal CSS:** Written within a `<style>` tag, embedded inside the `<head>` section.
     ```html
     <style>
       body {
         background-color: lightblue;
       }
     </style>
     ```
  3. **External CSS:** Defined in a separate file (e.g., `style.css`). This file is linked in the HTML using the `<link>` tag.
     ```html
     <link rel="stylesheet" href="styles.css">
     ```
     Example in CSS File:
     ```css
     h1 {
       color: green;
     }
     ```

#### DIV:
The `<div>` tag is a container used to group and organize HTML elements into logical sections, making it easier to style or manipulate sections independently.

- **Example of `<div>` Usage:**
  ```html
  <div style="border: 1px solid black; padding: 10px;">
    <h2>Section Title</h2>
    <p>This content is inside a div container.</p>
  </div>
  ```

---

### 3. Properties of PHP Variables and XML

#### PHP Variables:
Variables in PHP serve as containers for storing data. A variable in PHP starts with a `$` sign and follows specific naming conventions.

- **Key Features of PHP Variables:**
  1. Names must start with `$` and can include letters, numbers, and underscores, but cannot start with a number.
  2. PHP variables are dynamically typed, meaning their data type changes based on assigned values.
  3. Variables in PHP are case-sensitive.

- **Examples of Common PHP Variable Types:**
  - **String Variable:** Holds textual data.
    ```php
    $greeting = "Hello, World!";
    ```
  - **Integer Variable:** Stores whole numbers.
    ```php
    $num = 42;
    ```
  - **Array Variable:** Holds a list of values.
    ```php
    $fruits = array("Apple", "Banana", "Mango");
    ```

#### XML (Extensible Markup Language):
XML provides a format for storing and exchanging structured data. It is both human-readable and machine-readable, making it ideal for configurations and data exchanges between systems.

- **Example of XML Format:**
  ```xml
  <library>
    <book>
      <title>Mastering PHP</title>
      <author>Jane Doe</author>
    </book>
  </library>
  ```

---

### 4. How Conditions are Checked in PHP (CGI)
In PHP, conditional statements allow decisions to be made based on specific conditions. These are essential for implementing logic in web applications.

#### Types of PHP Conditional Statements:

1. **If Statement:** Executes code only if a condition is true.
   ```php
   $age = 20;
   if ($age >= 18) {
       echo "You are eligible to vote.";
   }
   ```

2. **If-Else Statement:** Includes an alternate block of code for when the condition is false.
   ```php
   if ($age >= 18) {
       echo "Adult";
   } else {
       echo "Minor";
   }
   ```

3. **If-ElseIf-Else Statement:** Allows multiple conditions to be evaluated in sequence.
   ```php
   if ($marks >= 90) {
       echo "Grade: A";
   } elseif ($marks >= 75) {
       echo "Grade: B";
   } else {
       echo "Grade: C";
   }
   ```

---

### 5. Different Types of Loops in PHP
Loops enable repetitive execution of code while a condition is satisfied. PHP provides multiple loop constructs:

1. **For Loop:** Executes a block of code a fixed number of times.
   ```php
   for ($i = 1; $i <= 5; $i++) {
       echo "Count: $i<br>";
   }
   ```

2. **While Loop:** Repeats code as long as the condition remains true.
   ```php
   $i = 1;
   while ($i <= 5) {
       echo "Value: $i<br>";
       $i++;
   }
   ```

3. **Do-While Loop:** Executes code once and repeats it as long as the condition remains true.
   ```php
   $i = 1;
   do {
       echo "Number: $i<br>";
       $i++;
   } while ($i <= 5);
   ```

4. **Foreach Loop:** Specifically used for iterating over arrays.
   ```php
   $colors = array("Red", "Blue", "Green");
   foreach ($colors as $color) {
       echo "$color<br>";
   }
   ```

---

### 6. What is List (Array) Data Structure in PHP
In PHP, arrays are used to store multiple values under one variable. Arrays make it easy to manipulate and organize data.

#### Types of Arrays in PHP:

1. **Indexed Arrays:** Use numeric indices to access elements.
   ```php
   $cities = array("New York", "London", "Mumbai");
   echo $cities[0]; // Outputs: New York
   ```

2. **Associative Arrays:** Use key-value pairs.
   ```php
   $person = array("name" => "John", "age" => 30);
   echo $person["name"]; // Outputs: John
   ```

3. **Multidimensional Arrays:** Contain arrays within arrays, enabling representation of complex structures like grids.
   ```php
   $matrix = array(
       array(1, 2, 3),
       array(4, 5, 6)
   );
   echo $matrix[1][2]; // Outputs: 6
   ```

