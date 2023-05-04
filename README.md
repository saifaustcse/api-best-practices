## Software Design Patterns

> Though there are 1000’s of articles about **Software Design Patterns**, I have written this article is in order to document with simple C# realworld example with short and easy description. I have also created another repository regarding [Software Design principles](https://github.com/saifaustcse/software-design-patterns) which can be helpful as well.

## Give a Star! :star:

> If you like or are using this project to learn or start your solution, please give it a star. Thanks!

## Find me

> Find me if you wish [@Saif(https://www.linkedin.com/in/saif-aust-cse/).

### Table of Contents

| No. | Topic                                                  |
| --- | ------------------------------------------------------ |
| 1   | [What are Design Patterns?](#What-are-Design-Patterns) |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)      |

1.  ### Use JSON as the Format for Sending and Receiving Data

    In modern API development, JSON (JavaScript Object Notation) has become the standard format for sending and receiving data. It has largely replaced XML and HTML due to its simplicity and widespread support.

    JSON is widely supported by programming languages such as JavaScript, Python, and PHP. These languages provide built-in methods for parsing and manipulating JSON data. For example, Python has json.loads() and json.dumps() for working with JSON.

    When sending JSON data in an API response, it's important to set the Content-Type header to `application/json`. This ensures that the client interprets the data correctly.

    In server-side frameworks like Express, setting the Content-Type header is often handled automatically. Express provides the express.json() middleware specifically for parsing JSON data in the request body. Alternatively, the body-parser NPM package can be used for the same purpose.

    By using JSON as the data format and setting the appropriate Content-Type header, API developers can ensure efficient and reliable data transmission between clients and servers.

    The rewritten information focuses on the benefits of using JSON, highlights the support in various programming languages, and explains the importance of setting the Content-Type header. It also provides specific examples for working with JSON in Python and mentions popular server-side frameworks like Express.

    **[⬆ Back to Top](#table-of-contents)**

2.  ### Use Nouns Instead of Verbs

    When designing a REST API, it is recommended to use nouns in the endpoint paths rather than verbs. This is because HTTP methods such as GET, POST, PUT, PATCH, and DELETE already represent the actions that can be performed on a resource.

    The following table helps you in understanding the REST API Verbs:

    | REST Verb | Action                                               |
    | --------- | ---------------------------------------------------- |
    | GET       | Fetches a record or set of resources from the server |
    | OPTIONS   | Fetches all available REST operations                |
    | POST      | Creates a new set of resources or a resource         |
    | PUT       | Updates or replaces the given record                 |
    | PATCH     | Modifies the given record                            |
    | DELETE    | Deletes the given resource                           |

    Do not use verbs in the URI. Instead of using verbs in the endpoint paths, it is advisable to structure the paths based on the resources they represent.

    Here are a few examples to show how the endpoints should look like,

    | Incorrect            | Correct           |
    | -------------------- | ----------------- |
    | GET /getAllUsers     | GET /users        |
    | GET /getUserById/1   | GET /users/1      |
    | POST /createUser     | POST /users       |
    | PUT /updateUser/1    | PUT /users/1      |
    | DELETE /deleteUser/1 | DELETE /users/1   |
    | PATCH /modifyUser/1  | PATCH /users/1    |
    | HEAD /checkUser/1    | HEAD /users/1     |
    | OPTIONS /listUsers   | OPTIONS /users    |
    | TRACE /traceUser/1   | TRACE /users/1    |
    | CONNECT /connectUser | CONNECT /users    |


    **[⬆ Back to Top](#table-of-contents)**

3.  ### Use Plural nouns

    Use plural when possible unless they are singleton resources.

    Here's the table with examples for all HTTP methods:

    | Do's                        | Don'ts                              |
    | --------------------------- | ----------------------------------- |
    | GET /users/123              | GET /user/123                       |
    | POST /users                 | POST /user                          |
    | GET /users                  | GET /user                           |
    | PUT /users/123              | PUT /user/123                       |
    | PATCH /users/123            | PATCH /user/123                     |
    | DELETE /users/123           | DELETE /user/123                    |
    | OPTIONS /users              | OPTIONS /user                       |
    | HEAD /users                 | HEAD /user                          |
    | GET /users?name=John&age=30 | GET /users?userName=John&userAge=30 |


    **[⬆ Back to Top](#table-of-contents)**

4.  ### References

    I have followed many articles but among them, the following articles are really helpful. Those articles helped me a lot and also encourage me to write this article according to my understanding.

    - [dotnettutorials](https://dotnettutorials.net/course/dot-net-design-patterns/) Design Patterns in C# With Real-Time Examples

    **[⬆ Back to Top](#table-of-contents)**

## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
