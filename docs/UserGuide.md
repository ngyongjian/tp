# User Guide

<!-- TOC -->
- [Introduction](#introduction)
    - [Target user profile](#target-user-profile)
    - [Problem addressed](#problem-addressed) 
- [Access Management](#access-management)
    - [Login an account](#login)
    - [Signup an account](#signup)
    - [Change password](#password)
    - [Help in login/signup](#help)
    - [Logout from an account](#logout)
    - [Exit the application](#exit)
- [Features](#features)
    - [Search book](#search)
    - [Check book availability](#check)
    - [Borrow book](#borrow)
    - [Renew borrow period of book](#renew)
    - [Check borrowing status](#status)
    - [Return book](#return)
    - [Add/delete book](#librarian)
    - [List book](#list)
    - [View history](#history)
- [FAQ](#faq)
- [Command Summary](#command-summary)
  <!-- TOC -->

## Introduction
Product Name: Duke of Books

### Target user profile:
This program is designed for National University of Singapore (NUS) Computer Science (CS) 
students who wish to borrow and read CS related books.

### Problem addressed:
CS students are often busy, so a command line interface (CLI) program without a GUI can make 
finding the books they need quick and efficient. This software can also help them keep track 
of loans and return dates.


## Quick Start

1. Ensure that you have Java 11 installed.
2. Download the latest version of `DukeOfBooks` from [here](https://github.com/AY2223S2-CS2113-F10-4/tp/releases).

## Access Management
To perform any actions, users must first log in to their account.

### <a name="login"> Login an account: `login` </a>
Log in the system using your username and password. 

Format:
* login -username USERNAME -password PASSWORD

Examples:
```text
|| Enter command: login -username me -password my$password
|| Login Success!
|| ===================================================
|| Welcome My Name!
```

### <a name="signup"> Signup an account: `signup` </a>
Sign up for a new account by providing a unique username, password, and the user's actual name.

Format: 
* signup -username USERNAME -password PASSWORD -name NAME

Examples:
```text
|| Enter command: signup -username me -password my$password -name My Name
|| Sign up success!
|| ===================================================
|| Welcome My Name!
```

### <a name="password"> Change password: `password` </a>
Change the password of a user.

Format: 
* password -username USERNAME -old OLD_PASSWORD -new NEW_PASSWORD

Examples:
```text
|| Enter command: password -username me -old my$password -new new$password
|| Password has been reset!
```

### <a name="help"> Help in login/signup: `help` </a>
Get a list of commands related to accessing the system.

Format:
* help

Examples:
```text
|| Enter command: help
|| login -username [username] -password [password]
|| signup -username [username] -password [password] -name [name]
|| password -username [username] -old [old password] -new [new password]
|| exit: exits the application
```

### <a name="logout"> Logout from an account: `logout` </a>
This command allows the user to log out of the system. It can only be used after the user has logged in. After logging out, the user can log in again with the same or a different account.

Format:
* logout

Examples: 
```text
|| Enter command: logout
|| Logging out...
```

### <a name="exit"> Exit the application: `exit` </a>
This command is used to exit the application and should only be executed after logging out of the system. It terminates Duke of Books.

Format: 
* exit

Examples:
```text
|| Enter command: exit
||
|| Exiting DukeOfBooks as requested ...
|| ===================================================
|| Goodbye!
```

## Features

### <a name="search"> Search book: `search` </a>
Search for a book by title and/or topic. The search string will be matched with a subset of the title/topic of the target book, and any matching books will be returned. Note that multiple books can be returned during searching.

Format:
* search -title TITLE
* search -topic TOPIC
* search -title TITLE -topic TOPIC

Examples:
```text
|| Enter command: search -title Thinking in Java
|| The Search Results:
|| ===================================================
|| No.1
|| ISBN: 978-0131872486
|| Title: Thinking in Java
|| Author: Bruce Eckel
|| Topic: Computer Programming

|| Enter command: search -topic Operating Systems
|| The Search Results:
|| ===================================================
|| No.1
|| ISBN: 978-1119800361
|| Title: Operating System Concepts
|| Author: Abraham Silberschatz
|| Topic: Operating Systems
|| ===================================================
|| No.2
|| ISBN: 978-0357433836
|| Title: Guide to Operating Systems
|| Author: Greg Tomsho
|| Topic: Operating Systems

|| Enter command: search -title Guide to Operating Systems -topic Operating Systems
|| The Search Results:
|| ===================================================
|| No.1
|| ISBN: 978-0357433836
|| Title: Guide to Operating Systems
|| Author: Greg Tomsho
|| Topic: Operating Systems
```

### <a name="check"> Check book availability: `check` </a>
Check if a book is available for borrowing. The system will return either "Borrowed" or "Not borrowed" status of the book.
Format:
* check -title TITLE

Examples:
```text
|| Enter command: check -title Guide to Operating Systems
|| Status: Not borrowed
```

### <a name="borrow"> Borrow book: `borrow` </a>
Borrow a book from the library.

Format:
* borrow -title TITLE

Examples:
```text
|| Enter command: borrow -title Introduction to Algorithms
|| Borrow is successful.
```

### <a name="renew"> Renew borrow period of book: `renew` </a>
Renew the borrowing period of a book for a fixed duration.

Format:
* renew -title TITLE

Examples:
```text
|| Enter command: renew -title Introduction to Algorithms
|| Item has been renewed!
```

### <a name="status"> Check borrowing status: `status` </a>
Check the borrowing status of a book. The system will return one of the following status: "Not borrowed", "Borrowed" with details, or "Overdue" with details.

Format:
* status -title TITLE

Examples:
```text
|| Enter command: status -title Guide to Operating Systems
|| Status: Not borrowed
```

### <a name="return"> Return book: `return` </a>
Return a book to the library.

Format:
* return -title TITLE

Examples:
```text
|| Enter command: return -title Introduction to Algorithms
|| Item has been returned!
```

### <a name="librarian"> Add/Delete book: `librarian` </a>
This method is used by the librarian to add or delete books to/from the library for users. It is a superuser privilege and should not be used by anyone else.

Format:
* librarian -title TITLE -topic TOPIC -author AUTHOR -isbn ISBN -action add
* librarian -title TITLE -topic TOPIC -author AUTHOR -isbn ISBN -action delete

Examples:
```text
|| Enter command: librarian -title Introduction to OOP -topic java -author Java legends -isbn 1234567890123 -action add
|| Action: add is successful. Introduction to OOP updated

|| Enter command:  librarian -title Introduction to OOP -topic java -author Java legends -isbn 1234567890123 -action delete
|| Action: delete is successful. Introduction to OOP updated
```

### <a name="list"> List book: `list` </a>
List all the books in the library.

Format:
* list

Examples:
```text
|| Enter command: list
|| Books in Library:
|| ===================================================
|| No.1
|| ISBN: 978-0131872486
|| Title: Thinking in Java
|| Author: Bruce Eckel
|| Topic: Computer Programming
|| ===================================================
|| No.2
|| ISBN: 978-0275967765
|| Title: Cpp Programming Language
|| Author: Bjarne Stroustrup
|| Topic: Computer Programming
|| ===================================================
|| No.3
|| ISBN: 978-1133608424
|| Title: Data Structures and Algorithms in Cpp
|| Author: Adam Drozdek
|| Topic: Data Structures and Algorithms
|| ===================================================
|| No.4
|| ISBN: 978-1119800361
|| Title: Operating System Concepts
|| Author: Abraham Silberschatz
|| Topic: Operating Systems
|| ===================================================
```

### <a name="history"> View history: `history` </a>
Users can view their borrowing history for books with this command.

Format:
* history

Examples:
```text
|| Enter command: history
|| These are the books you have borrowed thus far:
|| 1. ISBN: 978-0262033848
|| Title: Introduction to Algorithms
|| Author: Thomas H Cormen
|| Topic: Data Structures and Algorithms Status: borrowed
|| 2. ISBN: 978-0262033848
|| Title: Introduction to Algorithms
|| Author: Thomas H Cormen
|| Topic: Data Structures and Algorithms Status: borrowed
```

## FAQ

**Q**: How do I transfer my data to another computer? 

**A**: Data is stored in the text files found in the `./tp/database` directory. To transfer the data to another computer, just transfer the files over to the new target computer, and keep the files in the same directory.

**Q**: Why I cannot change my password after logging in?  

**A**: You need to log out using `logout` before changing password. 

**Q**: I cannot exit the application 

**A**: You must first logout of the application before you can exit the application. The application
has been designed this way to ensure maximum security for you!

**Q**: Not all data is saved when I exit the application

**A**: The application is designed to be hosted and run on a server without it being closed. Thus,
there will be records that could be loss when exiting. Saving all data in this system through a
text file is not feasible due to the inability to enforce the relation between objects when the
system is loaded again.

**Q**: When I renew the book, nothing happens

**A**: Do not worry, our application is time sensitive! `renew` will only work if you renew the book,
not on the same day you borrowed the book. While you might not be able to test this during PE, it definitely
works!

## Command Summary

| Action                      | Format                                   | Example                                                                                      |
|:----------------------------|:-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| Login an account            | `login -username USERNAME -password PASSWORD`                                  | `login -username me -password my$password`                                                    |
| Signup an account           | `signup -username USERNAME -password PASSWORD -name NAME`                      | `signup -username me -password my$password -name My Name`                                    |
| Change password             | `password -username USERNAME -old OLD_PASSWORD -new NEW_PASSWORD`              | `password -username me -old old$password -new new$password`                            |
| Help in login/signup        | `help`                                                                         | `help`                                                                                        |
| Logout from an account      | `logout`                                                                       | `logout`                                                                                      |
| Exit the application        | `exit`                                                                         | `exit`                                                                                        |
| Search book by title        | `search -title TITLE`                                                          | `search -title Python Programming`                                                            |
| Search book by topic        | `search -topic TOPIC`                                                          | `search -topic Software Engineering`                                                          |
| Combined search             | `search -title TITLE -topic TOPIC`                                             | `search -title Cpp Programming Language -topic Computer Programming`                    |
| Check book availability     | `check -title TITLE`                                                           | `check -title Python Programming`                                                            |
| Borrow book                 | `borrow -title TITLE`                                                          | `borrow -title Python Programming`                                                            |
| Renew borrow period of book | `renew -title TITLE`                                                           | `renew -title C++Primer`                                                                      |
| Check borrowing status      | `status -title TITLE`                                                          | `status -title C++Primer`                                                                    |
| Return book                 | `return -title TITLE`                                                          | `return -title C++Primer`                                                                    |
| Add book                    | `librarian -title TITLE -topic TOPIC -author AUTHOR -isbn ISBN -action add`    | `librarian -title C++Primer -topic Programming -author James -isbn 12345 -action add`    |
| Delete book                 | `librarian -title TITLE -topic TOPIC -author AUTHOR -isbn ISBN -action delete` | `librarian -title C++Primer -topic Programming -author James -isbn 12345 -action delete` |
| List book                   | `list`                                                                         | `list`                                                                                        |
| View history                | `history`                                                                      | `history`                                                                                    |
