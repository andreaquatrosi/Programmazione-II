#### First
---

### Exercise: Library Management System

**Objective:** Create a library management system that allows you to manage books, perform operations on them, and keep track of their details.

**Requirements:**

1. **Class Definitions:**
   - **Class `Book`:**
     - **Private Members:**
       - `int id` (book ID)
       - `char* title` (title of the book)
       - `char* author` (author of the book)
       - `int copies` (number of copies available)
     - **Public Methods:**
       - Constructors: Default, Parameterized, and Copy Constructor
       - Destructor
       - Assignment Operator Overload
       - Getter and Setter methods
       - Method to increment the number of copies
       - Method to decrement the number of copies (ensure it doesn’t go below zero)
       - Method to display book details
     - **Friend Functions:**
       - A function to find a book by title (search through an array of books)
       - A function to compare two books based on the number of copies
       - Overload the `<<` operator to display book details

   - **Class `Library`:**
     - **Private Members:**
       - `Book* books` (array of books)
       - `int numBooks` (number of books in the library)
     - **Public Methods:**
       - Constructor and Destructor
       - Method to add a book
       - Method to remove a book by ID
       - Method to display all books
       - Method to sort books by the number of copies (ascending order)
       - Method to find the book with the most copies

2. **Implementation:**
   - Implement all the methods described above for both classes.
   - In the `main` function:
     - Allow the user to input the number of books and their details.
     - Display all the books.
     - Add functionality to increment or decrement copies of a book.
     - Search for a book by title.
     - Find and display the book with the most copies.
     - Sort and display all books based on the number of copies.

3. **Additional Requirements:**
   - Use dynamic memory allocation for the `title` and `author` attributes in the `Book` class.
   - Ensure that you handle memory management correctly to avoid leaks.
   - Test edge cases like trying to decrement copies below zero and searching for a non-existent book.

**Example Output:**

```
How many books do you want to add? 3

Enter details for Book 1:
ID: 101
Title: C++ Programming
Author: John Doe
Copies: 5

Enter details for Book 2:
ID: 102
Title: Data Structures
Author: Jane Smith
Copies: 3

Enter details for Book 3:
ID: 103
Title: Algorithms
Author: Alice Brown
Copies: 7

Books in the library:
ID: 101, Title: C++ Programming, Author: John Doe, Copies: 5
ID: 102, Title: Data Structures, Author: Jane Smith, Copies: 3
ID: 103, Title: Algorithms, Author: Alice Brown, Copies: 7

Finding book by title 'Data Structures':
ID: 102, Title: Data Structures, Author: Jane Smith, Copies: 3

Incrementing copies of book ID 102...
Copies updated. New count: 4

Book with the most copies:
ID: 103, Title: Algorithms, Author: Alice Brown, Copies: 7

Sorting books by number of copies:
ID: 102, Title: Data Structures, Author: Jane Smith, Copies: 4
ID: 101, Title: C++ Programming, Author: John Doe, Copies: 5
ID: 103, Title: Algorithms, Author: Alice Brown, Copies: 7
```

**Hints:**
- Use dynamic memory allocation for the `title` and `author` strings in the `Book` class.
- Carefully manage memory allocation and deallocation.
- Implement appropriate error handling for user inputs and operations.