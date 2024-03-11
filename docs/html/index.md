---
title: HTML
hide:
   - tags

tags:
- HTML



---

#  HTML


---

##  HTML



#### What is HTML?
HTML (Hypertext Markup Language) is the standard markup language for creating web pages. It defines the structure and content of a webpage using tags and attributes.

#### Basic Structure of an HTML Document
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is a paragraph.</p>
</body>
</html>
```

### HTML Elements and Tags
#### Headings
```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

#### Paragraphs
```html
<p>This is a paragraph.</p>
```

#### Links
```html
<a href="https://www.example.com">Visit Example</a>
```

#### Images
```html
<img src="image.jpg" alt="Description of the image">
```

### HTML Attributes
#### src Attribute (for images)
Specifies the URL of the image source.
```html
<img src="image.jpg" alt="Description of the image">
```

#### href Attribute (for links)
Specifies the URL of the linked page.
```html
<a href="https://www.example.com">Visit Example</a>
```

### HTML Lists
#### Ordered List
```html
<ol>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ol>
```

#### Unordered List
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

#### Definition List
```html
<dl>
    <dt>Term 1</dt>
    <dd>Description 1</dd>
    <dt>Term 2</dt>
    <dd>Description 2</dd>
</dl>
```

### HTML Forms
#### Text Input
```html
<input type="text" name="firstname" placeholder="First Name">
```

#### Password Input
```html
<input type="password" name="password" placeholder="Password">
```

#### Submit Button
```html
<input type="submit" value="Submit">
```

 
HTML is the foundation of web development. By understanding its basic elements, tags, and attributes, you can create simple web pages and forms. As you advance, you'll learn more about CSS for styling and JavaScript for interactivity, making your web pages more dynamic and engaging.



#### Tables
Tables are used to display data in rows and columns.
```html
<table>
    <tr>
        <th>Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>John</td>
        <td>25</td>
    </tr>
    <tr>
        <td>Jane</td>
        <td>30</td>
    </tr>
</table>
```

#### Forms (Continued)
##### Radio Buttons
```html
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female
```

##### Checkboxes
```html
<input type="checkbox" name="vehicle1" value="Bike"> I have a bike<br>
<input type="checkbox" name="vehicle2" value="Car"> I have a car
```

##### Select Dropdown
```html
<select name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="mercedes">Mercedes</option>
  <option value="audi">Audi</option>
</select>
```

#### Semantic HTML
Semantic HTML elements convey meaning to both the browser and developer, aiding in accessibility and SEO.
- `<header>`: Represents a group of introductory or navigational aids.
- `<nav>`: Defines a section of navigation links.
- `<section>`: Defines a section in a document.
- `<article>`: Represents a self-contained piece of content.
- `<footer>`: Defines a footer for a document or section.

#### HTML5 Features
HTML5 introduced new features and elements, including:
- `<video>` and `<audio>`: Embed multimedia content.
- `<canvas>`: For drawing graphics dynamically.
- `<svg>`: Scalable Vector Graphics.
- `<progress>`: Displays progress of a task.
- `<meter>`: Represents a scalar measurement.




#### Embedding Multimedia
HTML provides tags to embed multimedia content such as videos, audio, and images.

##### Video
```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
```

##### Audio
```html
<audio controls>
  <source src="music.mp3" type="audio/mp3">
  Your browser does not support the audio tag.
</audio>
```

#### HTML Entities
HTML entities are special codes used to display reserved characters and symbols.
```html
&copy; <!-- Copyright symbol -->
&hearts; <!-- Heart symbol -->
&amp; <!-- Ampersand symbol -->
```

#### Meta Tags
Meta tags provide metadata about the HTML document.
```html
<meta charset="UTF-8">
<meta name="description" content="Description of the web page">
<meta name="keywords" content="keyword1, keyword2, keyword3">
<meta name="author" content="Author Name">
```

#### Semantic HTML5 Tags
HTML5 introduced semantic tags for better document structure and accessibility.

##### `<header>`
```html
<header>
    <h1>Welcome to My Website</h1>
</header>
```

##### `<nav>`
```html
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

##### `<footer>`
```html
<footer>
    <p>&copy; 2024 My Website</p>
</footer>
```

#### Comments in HTML
Comments in HTML are not displayed in the browser but can be useful for adding notes to your code.
```html
<!-- This is a comment -->
```
 

---

## HTML5 features

### 1. **Semantic HTML Tags**:

Tags like `<header>`, `<nav>`, `<section>`, `<article>`, and `<footer>` are used to provide better structure and semantics to the application's layout, aiding accessibility and SEO.


- **Description**: HTML5 introduced semantic tags that provide meaning to the structure of web content. These tags improve accessibility and SEO.

- **Usage in React**:
    - Use semantic tags like `<header>`, `<footer>`, `<article>`, `<section>`, and `<nav>` to organize your React components.
    - Example:

    ```jsx
    <header>
      <h1>My React App</h1>
    </header>
    <nav>
      {/* Navigation links */}
    </nav>
    <section>
      {/* Main content */}
    </section>
    <footer>
      {/* Footer content */}
    </footer>
    ```


### 2. **Video and Audio**:

`<video>` and `<audio>` elements are employed to embed multimedia content, such as videos and audio files, directly into the application.

- **Description**: HTML5 introduced `<audio>` and `<video>` elements for embedding multimedia content directly in web pages.
- **Usage in React**:
    - Use these elements to embed audio and video files in your React components.
    - Example:

    ```jsx
    <video controls>
      <source src="my-video.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
    ```


### 3. **Canvas**: 

The `<canvas>` element allows for dynamic rendering of graphics and animations directly within the application, often used in games or data visualization components.

### 4. **SVG (Scalable Vector Graphics)**: 

SVG elements are utilized for creating scalable vector graphics, enabling the rendering of high-quality and resolution-independent images and icons.

### 5. **Form Enhancements**: 

HTML5 introduced various enhancements to form elements, including new input types (`<input type="date">`, `<input type="email">`, etc.), validation attributes, and elements like `<datalist>` for providing autocomplete options.


- **Description**: HTML5 provides form enhancements like new input types (`date`, `email`, `number`, etc.) and attributes (`required`, `pattern`, etc.).
- **Usage in React**:
    - Utilize these input types and attributes in your React forms.
    - Example:

    ```jsx
    <input type="email" placeholder="Enter your email" required />
    <input type="date" />
    ```


### 6. **LocalStorage and SessionStorage**: 

The `localStorage` and `sessionStorage` APIs are employed for client-side storage of data, allowing applications to store user preferences, session information, or cached data.


- **Description**: HTML5 introduced local storage and session storage for client-side data persistence.
- **Usage in React**:
    - Use `localStorage` or `sessionStorage` to store and retrieve data in your React application.
    - Example:

    ```jsx
    // Save data
    localStorage.setItem('username', 'john_doe');

    // Retrieve data
    const savedUsername = localStorage.getItem('username');
    ```


### 7. **Drag and Drop**: 

HTML5's native drag and drop functionality is utilized to implement intuitive user interactions, such as reordering items in lists or uploading files by dragging them onto designated areas.

### 8. **Geolocation**: 

The Geolocation API enables React applications to access the user's geographical location, allowing for location-based services and features.

### 9. **Web Workers**: 

HTML5 Web Workers are used to execute scripts in background threads, enabling concurrent processing and improving the application's responsiveness, especially for CPU-intensive tasks.

### 10. **IndexedDB**: 

The IndexedDB API is employed for client-side storage of structured data, providing a more robust alternative to `localStorage` for managing larger datasets.


### 11. **Canvas and SVG Graphics**

- **Description**: HTML5 includes the `<canvas>` element for drawing graphics and the `<svg>` element for scalable vector graphics.
- **Usage in React**:
    - Use `<canvas>` for custom drawings and animations.
    - Use `<svg>` for creating vector-based graphics.
    - Example:

    ```jsx
    <canvas id="myCanvas"></canvas>
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" fill="blue" />
    </svg>
    ```
 
 
---






