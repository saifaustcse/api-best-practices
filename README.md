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

2.  ### Use HTTP methods to communicate intent

    One of the key principles of REST APIs is the use of standard HTTP methods to communicate the intent of the request.

    The following table helps you in understanding the REST API Verbs:

    | REST Verb | Action                                               |
    | --------- | ---------------------------------------------------- |
    | GET       | Fetches a record or set of resources from the server |
    | OPTIONS   | Fetches all available REST operations                |
    | POST      | Creates a new set of resources or a resource         |
    | PUT       | Updates or replaces the given record                 |
    | PATCH     | Modifies the given record                            |
    | DELETE    | Deletes the given resource                           |

    Reources :

    - [PATCH vs PUT in REST API ](https://josipmisko.com/posts/patch-vs-put-rest-api) Differences between PATCH and PUT

    **[⬆ Back to Top](#table-of-contents)**

3.  ### Do not use verbs in the URI

    Instead of using verbs in the endpoint paths, it is advisable to structure the paths based on the resources they represent.

    Here are a few examples to show how the endpoints should look like,

    | Incorrect            | Correct         |
    | -------------------- | --------------- |
    | GET /getAllUsers     | GET /users      |
    | GET /getUserById/1   | GET /users/1    |
    | POST /createUser     | POST /users     |
    | PUT /updateUser/1    | PUT /users/1    |
    | DELETE /deleteUser/1 | DELETE /users/1 |
    | PATCH /modifyUser/1  | PATCH /users/1  |

    **[⬆ Back to Top](#table-of-contents)**

4.  ### Use Plural nouns

    Use plural when possible unless they are singleton resources.

    Here are a few examples to show how the endpoints should look like,

    | Do's                        | Don'ts                              |
    | --------------------------- | ----------------------------------- |
    | GET /users/123              | GET /user/123                       |
    | POST /users                 | POST /user                          |
    | GET /users                  | GET /user                           |
    | PUT /users/123              | PUT /user/123                       |
    | PATCH /users/123            | PATCH /user/123                     |
    | DELETE /users/123           | DELETE /user/123                    |
    | GET /users?name=John&age=30 | GET /users?userName=John&userAge=30 |

    **[⬆ Back to Top](#table-of-contents)**

5.  ### Use Lowercase letters

    URIs should start with a letter and use only lowercase letters.

    Here are a few examples to show how the endpoints should look like,

    | Incorrect        | Correct    |
    | ---------------- | ---------- |
    | GET /getAllUsers | GET /users |
    | GET /GetAllUsers | GET /users |
    | GET /USERS       | GET /users |

    **[⬆ Back to Top](#table-of-contents)**

6.  ### Use hyphens (-) to separate words or segments in the URI path

    Avoid using underscores, spaces, special characters, camel case, or Pascal case in URIs. Instead, use hyphens (-) to separate words or segments in the URI path. This practice improves readability and ensures compatibility across different systems and platforms.

    Here are a few examples to show how the endpoints should look like,

    | Incorrect URIs    | Correct URIs    |
    | ----------------- | --------------- |
    | /userRoles        | /user-roles     |
    | /UserRoles        | /user-roles     |
    | /user_roles       | /user-roles     |
    | /user roles       | /user-roles     |
    | /user%20roles     | /user-roles     |
    | /userRoles/123    | /user-roles/123 |
    | /User_Roles       | /user-roles     |
    | /user roles/123   | /user-roles/123 |
    | /user-roles/abc   | /user-roles/abc |
    | /User-Roles/123   | /user-roles/123 |
    | /user_roles/123   | /user-roles/123 |
    | /user%20roles/123 | /user-roles/123 |

    **[⬆ Back to Top](#table-of-contents)**

7.  ### Underscore separate query strings

    literals or expressions in the query strings are separated using underscores (\_) to improve readability and maintain consistency in URI formatting

    Here are a few examples to show how the endpoints should look like,

    | Incorrect                           | Correct                               |
    | ----------------------------------- | ------------------------------------- |
    | /api/users?sortBy=firstName_desc    | /api/users?sort_by=firstName_desc     |
    | /api/users?filterBy=active          | /api/users?filter_by=active           |
    | /api/users?pageSize=10&pageNumber=2 | /api/users?page_size=10&page_number=2 |
    | /api/users?searchQuery=john         | /api/users?search_query=john          |

    **[⬆ Back to Top](#table-of-contents)**

8.  ### References

    I have followed many articles but among them, the following articles are really helpful. Those articles helped me a lot and also encourage me to write this article according to my understanding.

    - [dotnettutorials](https://dotnettutorials.net/course/dot-net-design-patterns/) Design Patterns in C# With Real-Time Examples

    **[⬆ Back to Top](#table-of-contents)**

## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
