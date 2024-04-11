# rust for dummies ;)

## Table of Contents
1. [Basic Syntax](#basic-syntax)
2. [Structures and Enums](#structures-and-enums)
3. [Macros](#macros)
4. [Closures and Higher Order Functions](#closures-and-higher-order-functions)
5. [Command Line Arguments](#command-line-arguments)
6. [Type Casting](#type-casting)
7. [Error Handling](#error-handling)
8. [Common Libraries](#common-libraries)
9. [Sorting Algorithms](#sorting-algorithms)
10. [Linked Lists](#linked-lists)
11. [Memory Management](#memory-management)
12. [File Operations](#file-operations)
13. [String Manipulations](#string-manipulations)
14. [References and Borrowing](#references-and-borrowing)
15. [Debugging and Error Handling](#debugging-and-error-handling)
16. [Best Practices](#best-practices)
17. [Code Styling](#code-styling)
18. [Compiling and Building](#compiling-and-building)
19. [Concurrency](#concurrency)
20. [Additional Notes](#additional-notes)

## 1. Basic Syntax <a name="basic-syntax"></a>
- **Variables and Types**
  ```rust
  let age: i32 = 30; // Integer
  let price: f32 = 19.99; // Floating point number
  let grade: char = 'A'; // Character
  ```

- **Conditional Statements**
  ```rust
  if condition { /* code if condition is true */ } 
  else if another_condition { /* code if another_condition is true */ } 
  else { /* code if all conditions are false */ }
  ```

- **Loops**
  ```rust
  for i in 0..10 { /* code executed 10 times */ }
  while condition { /* code executed while condition is true */ }
  loop { /* code */ if !condition { break; } } // code executed at least once and then while condition is true
  ```

- **Functions**
  ```rust
  fn function_name(parameters) -> return_type { /* function body */ }
  ```

## 2. Structures and Enums <a name="structures-and-enums"></a>
- **Usage**
  ```rust
  struct Person {
    name: String,
    age: i32,
    salary: f32,
  };
  
  enum Status {
    Active,
    Inactive,
  }
  ```

## 3. Macros <a name="macros"></a>
- **Usage**
  ```rust
  macro_rules! say_hello {
    () => {
        println!("Hello, world!");
    };
  }
  ```

## 4. Closures and Higher Order Functions <a name="closures-and-higher-order-functions"></a>
- **Usage**
  ```rust
  let add = |x, y| x + y;
  let apply = |f, x, y| f(x, y);
  ```

## 5. Command Line Arguments <a name="command-line-arguments"></a>
- **Usage**
  ```rust
  use std::env;
  let args: Vec<String> = env::args().collect();
  ```

## 6. Type Casting <a name="type-casting"></a>
- **Usage**
  ```rust
  let x = 10;
  let y = x as f64;
  ```

## 7. Error Handling <a name="error-handling"></a>
- **Usage**
  ```rust
  use std::fs::File;
  let f = File::open("file.txt").expect("Error opening file");
  ```

## 8. Common Libraries <a name="common-libraries"></a>
- **Usage**
  ```rust
  use std::io; // Standard input/output functions
  use std::collections::HashMap; // Data structures
  use std::fs; // File handling functions
  use std::thread; // Thread handling functions
  ```

## 9. Sorting Algorithms <a name="sorting-algorithms"></a>
- **Bubble Sort**
  ```rust
  fn bubble_sort(mut nums: Vec<i32>) -> Vec<i32> {
    let len = nums.len();
    for _ in 0..len {
        for j in 0..(len - 1) {
            if nums[j] > nums[j + 1] {
                nums.swap(j, j + 1);
            }
        }
    }
    nums
  }
  ```

- **Insertion Sort**
  ```rust
  fn insertion_sort(mut nums: Vec<i32>) -> Vec<i32> {
    for i in 1..nums.len() {
        let mut j = i;
        while j > 0 && nums[j - 1] > nums[j] {
            nums.swap(j, j - 1);
            j -= 1;
        }
    }
    nums
  }
  ```

## 10. Linked Lists <a name="linked-lists"></a>
- **Definition**
  ```rust
  use std::collections::LinkedList;
  let mut list: LinkedList<i32> = LinkedList::new();
  ```

- **Inserting a Node**
  ```rust
  list.push_back(data);
  ```

- **Deleting a Node**
  ```rust
  list.pop_front();
  ```

- **Traversing a Linked List**
  ```rust
  for element in list.iter() {
    println!("{}", element);
  }
  ```

## 11. Memory Management <a name="memory-management"></a>
- **Ownership and Borrowing**
  ```rust
  let s = String::from("hello"); // s comes into scope
  takes_ownership(s); // s's value moves into the function and is no longer valid here
  let x = 5; // x comes into scope
  makes_copy(x); // x would move into the function, but i32 is Copy, so it’s okay to still use x afterward
  ```

## 12. File Operations <a name="file-operations"></a>
- **Reading and Writing Files**
  ```rust
  use std::fs;
  let contents = fs::read_to_string("file.txt").expect("Error reading the file");
  fs::write("file.txt", "Hello, world!").expect("Unable to write file");
  ```

## 13. String Manipulations <a name="string-manipulations"></a>
- **Common Functions**
  ```rust
  let len = s.len(); // Get string length
  let s2 = s.clone(); // Copy string
  let s3 = s + &s2; // Concatenate strings
  let cmp = s == s2; // Compare strings
  ```

## 14. References and Borrowing <a name="references-and-borrowing"></a>
- **Usage**
  ```rust
  let s = String::from("hello"); // s is a String
  let len = calculate_length(&s); // &s is a reference to s
  ```

## 15. Debugging and Error Handling <a name="debugging-and-error-handling"></a>
- **Check Return Values**
  ```rust
  let f = File::open("file.txt").expect("Error opening file");
  ```

- **Asserts**
  ```rust
  assert!(condition, "Error message");
  ```

## 16. Best Practices <a name="best-practices"></a>
- **Avoid Shadowing:** Each variable should have a unique name.
- **Use `const` Keyword:** For non-modifiable parameters and variables.
- **Modular Programming:** Use functions and split code across multiple files for better organization.
- **Comments:** Document the "why", not the "what". Use comments to explain complex code sections.

## 17. Code Styling <a name="code-styling"></a>
- Be consistent with naming conventions (snake_case for variables and functions, CamelCase for types).
- Use consistent indentation (e.g., 4 spaces) and spacing.
- Choose a consistent style for curly braces.

## 18. Compiling and Building <a name="compiling-and-building"></a>
- **Compiler Warnings:** Use `cargo build` to compile the code and see warnings.
- **Cargo.toml:** Use for managing larger projects.

## 19. Concurrency <a name="concurrency"></a>
- **Thread Safety:** Rust's ownership model helps in protecting shared resources.
- **Atomic Operations:** Use for certain operations on shared variables to prevent race conditions.

## 20. Additional Notes <a name="additional-notes"></a>
- **Error Handling:** Always validate the return values from library functions for potential errors.
- **Memory Safety:** Rust's ownership model helps in preventing common bugs like null pointer dereferencing, double free, etc.
- **File Operations:** Ensure files are closed after finishing operations to avoid resource leaks. In Rust, this is handled automatically when the `File` object goes out of scope.
