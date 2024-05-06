# File system hierarchy of a Web project

## Web Development Project
- Root Folder
- Asset Folder
- Components / Modules Folder
- Pages / Routes Folder
- Context / State Management Folder
- Hooks
- Layouts Folder
- Data Folder
- Features / Modules Folder
- Utilities / Helper Folder

## When structuring a web development project, organizing your files and folders effectively is crucial for maintainability and collaboration. Here’s a common structure for a web project:

1. Root Folder (Project Directory):
    - This is the main folder for your entire project. It contains all other files and subfolders.
    - Commonly named after your project (e.g., my-website).

2. Assets Folder: Contains all static assets used in your web application:
    - Images (.jpg, .png, .svg)
    - Icons
    - Fonts (.woff, .woff2)
    - CSS files (.css)
    - JavaScript files (.js)

3. Components or Modules Folder:
    - Holds reusable UI components or modules.

Examples:
    - Navbar
    - Footer
    - Buttons
    - Cards

4.  Pages or Routes Folder:
- Contains individual views or pages of your web application.
- Each page may have its own subfolder with related components and styles.

Example:
- Home
- Home.vue (Vue component)
- Home.css (styles)

5. Context or State Management Folder: 
- Stores global state management files (if using frameworks like React or Vue). 

Example: 
- context 
- UserContext.js

6. Hooks Folder:
- Holds custom React hooks or Vue composition functions.

Example:
- useLocalStorage.js

7. Layouts Folder:
- Defines the general look and feel of the web pages.
- Contains layout-based components (e.g., sidebar, navbar, footer).

8. Data Folder:
- Stores text data or configuration files (e.g., JSON files).
- Useful for managing content that appears in multiple sections or pages.

9. Features or Modules Folder:
- Organizes features or functionality specific to different parts of your app.

Example:
- Authentication
- Login.vue
- Register.vue

10. Utilities or Helpers Folder:
- Contains utility functions or helper files. 

Example: 
- api.js (for making API requests) 
- dateUtils.js (for handling dates)
