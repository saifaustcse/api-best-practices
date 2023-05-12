## API Best Practices and Naming Conventions

> API best practices and naming conventions are essential for creating effective and maintainable APIs. These practices and conventions include guidelines for resource naming, versioning, URI structure, error handling, and security, among others. Adhering to these best practices can improve the usability, scalability, and consistency of APIs, and make them easier to use for both developers and end-users.

> In this context, it is important to consider the needs of the target audience and the overall goals of the API when designing and implementing the best practices and naming conventions.

## Give a Star! :star:

> If you find this documentation helpful for learning , please give it a star. Your support is appreciated!

## Find me

> Find me if you wish [@Saif(https://www.linkedin.com/in/saif-aust-cse/).

### Table of Contents

| No. | Topic                                                       |
| --- | ----------------------------------------------------------- |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)           |

1.  ### Breakdown of the parts a URL

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_path.png?raw=true" width="700" height="300">
    <div>

    Here is an example of full path API URLs:

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_url.webp?raw=true" width="700" height="300">
    <div>

2.  ### Use JSON as the Format for Sending and Receiving Data

    In modern API development, JSON (JavaScript Object Notation) has become the standard format for sending and receiving data. It has largely replaced XML and HTML due to its simplicity and widespread support.

    JSON is widely supported by programming languages such as JavaScript, Python, and PHP. These languages provide built-in methods for parsing and manipulating JSON data. For example, Python has json.loads() and json.dumps() for working with JSON.

    When sending JSON data in an API response, it's important to set the Content-Type header to `application/json`. This ensures that the client interprets the data correctly.

    In server-side frameworks like Express, setting the Content-Type header is often handled automatically. Express provides the express.json() middleware specifically for parsing JSON data in the request body. Alternatively, the body-parser NPM package can be used for the same purpose.

    By using JSON as the data format and setting the appropriate Content-Type header, API developers can ensure efficient and reliable data transmission between clients and servers.

    The rewritten information focuses on the benefits of using JSON, highlights the support in various programming languages, and explains the importance of setting the Content-Type header. It also provides specific examples for working with JSON in Python and mentions popular server-side frameworks like Express.

    **[⬆ Back to Top](#table-of-contents)**

3.  ### Use HTTP methods to communicate intent

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

4.  ### Do not use verbs in the URI

    Instead of using verbs in the endpoint paths, it is advisable to structure the paths based on the resources they represent.

    Here are a few examples to show how the endpoints should look like,

    | Do's            | Don'ts               |
    | --------------- | -------------------- |
    | POST /users     | POST /createUser     |
    | GET /users      | GET /getAllUsers     |
    | GET /users/1    | GET /getUserById/1   |
    | PUT /users/1    | PUT /updateUser/1    |
    | PATCH /users/1  | PATCH /modifyUser/1  |
    | DELETE /users/1 | DELETE /deleteUser/1 |

    **[⬆ Back to Top](#table-of-contents)**

5.  ### Use Plural nouns

    Use plural when possible unless they are singleton resources.

    Here are a few examples to show how the endpoints should look like,

    | Do's                        | Don'ts                              |
    | --------------------------- | ----------------------------------- |
    | POST /users                 | POST /user                          |
    | GET /users                  | GET /user                           |
    | GET /users/123              | GET /user/123                       |
    | PUT /users/123              | PUT /user/123                       |
    | PATCH /users/123            | PATCH /user/123                     |
    | DELETE /users/123           | DELETE /user/123                    |
    | GET /users?name=John&age=30 | GET /users?userName=John&userAge=30 |

    **[⬆ Back to Top](#table-of-contents)**

6.  ### Use Lowercase letters

    URIs should start with a letter and use only lowercase letters.

    Here are a few examples to show how the endpoints should look like,

    | Do's       | Don'ts           |
    | ---------- | ---------------- |
    | GET /users | GET /getAllUsers |
    | GET /users | GET /GetAllUsers |
    | GET /users | GET /USERS       |

    **[⬆ Back to Top](#table-of-contents)**

7.  ### Use hyphens (-) to separate words or segments in the URI path

    Avoid using underscores, camel case, Pascal case, spaces, special characters in URIs. Instead, use hyphens (-) to separate words or segments in the URI path. This practice improves readability and ensures compatibility across different systems and platforms.

    Here are a few examples to show how the endpoints should look like,

    | Do's            | Don'ts            |
    | --------------- | ----------------- |
    | /user-roles     | /user_roles       |
    | /user-roles     | /User_Roles       |
    | /user-roles     | /userRoles        |
    | /user-roles     | /UserRoles        |
    | /user-roles     | /user%20roles     |
    | /user-roles     | /user roles       |
    | /user-roles/123 | /user_roles/123   |
    | /user-roles/123 | /User_Roles/123   |
    | /user-roles/123 | /userRoles/123    |
    | /user-roles/123 | /UserRoles/123    |
    | /user-roles/123 | /user roles/123   |
    | /user-roles/123 | /user%20roles/123 |

    **[⬆ Back to Top](#table-of-contents)**

8.  ### Use Underscore (\_) separate query strings in the URI path

    literals or expressions in the query strings are separated using underscores (\_) to improve readability and maintain consistency in URI formatting

    Here are a few examples to show how the endpoints should look like,

    | Do's                                  | Don'ts                              |
    | ------------------------------------- | ----------------------------------- |
    | /api/users?sort_by=firstName_desc     | /api/users?sortBy=firstName_desc    |
    | /api/users?filter_by=active           | /api/users?filterBy=active          |
    | /api/users?page_size=10&page_number=2 | /api/users?pageSize=10&pageNumber=2 |
    | /api/users?search_query=john          | /api/users?searchQuery=john         |

    **[⬆ Back to Top](#table-of-contents)**

9.  ### Use Nesting on Endpoints to Show Relationships

    Sometimes, API endpoints can have relationships with each other, and in those cases, it can be helpful to nest them for better clarity and understanding

    Here are a few examples to show how the endpoints should look like,

    | Do's                     | Don'ts                           |
    | ------------------------ | -------------------------------- |
    | /api/users/1/roles       | /api/users/1/roles               |
    | /api/users/1/roles/3     | /api/users/1/roles/3             |
    | /api/users/1/friends     | /api/users/1/friends             |
    | /api/users/1/friends/2   | /api/users/1/friends/2           |
    | /api/users/1/posts       | /api/users/1/posts               |
    | /api/users/1/posts/5     | /api/users/1/posts/5             |
    | /api/posts/5/comments    | /api/users/1/posts/5/comments    |
    | /api/posts/5/comments/10 | /api/users/1/posts/5/comments/10 |

    **[⬆ Back to Top](#table-of-contents)**

10. ### Limit the nesting of resources to a reasonable level by using top-level resources

    This avoids overly complex and deeply nested URIs and makes the API more intuitive and easy to use. A flatter and more modular structure is promoted, leading to better scalability and maintainability of the API.

    Here are a few examples to show how the endpoints should look like,

    | Do's                     | Don'ts                                   |
    | ------------------------ | ---------------------------------------- |
    | /api/comments/10/replies | /api/users/1/posts/5/comments/10/replies |
    | /api/posts/5/tags        | /api/users/1/posts/5/tags                |
    | /api/comments/10/likes   | /api/users/1/posts/5/comments/10/likes   |
    | /api/posts/5/author      | /api/users/1/posts/5/author              |
    | /api/users/1/followers   | /api/users/1/posts/5/author/followers    |

    **[⬆ Back to Top](#table-of-contents)**

11. ### Use forward slashes (/) for hierarchy but not trailing forward slash (/)

    It is recommended to use forward slashes for indicating hierarchy, but not to use a trailing forward slash.

    Here are a few examples to show how the endpoints should look like,

    | Do's                        | Don'ts                               |
    | --------------------------- | ------------------------------------ |
    | POST /users                 | POST /user/                          |
    | GET /users                  | GET /user/                           |
    | GET /users/123              | GET /user/123/                       |
    | PUT /users/123              | PUT /user/123/                       |
    | PATCH /users/123            | PATCH /user/123/                     |
    | DELETE /users/123           | DELETE /user/123/                    |
    | GET /users?name=John&age=30 | GET /users?userName=John&userAge=30/ |

    **[⬆ Back to Top](#table-of-contents)**

12. ### Use query component to filtering, sorting, paging, and field selection

    As your database grows, managing it can become a daunting task, especially when it comes to retrieving specific data without exposing the entire database. To address this challenge, REST APIs offer four types of filtering options: filtering, sorting, paging, and field selection.

    By leveraging these options, you can retrieve the necessary data efficiently and effectively, without compromising security or overloading the client's bandwidth.

    Filtering
    Using this you can filter results that satisfy your required conditions. You can use search parameters like country, creation, date and etc for this.

    GET /users?country=UK
    GET /users?creation_date=2021-10-11
    GET /users?creation_date=2021-10-11

    Sorting

    You can sort your results in ascending and descending order using this option.

    GET /users?sort=birthdate_date:asc
    GET /users?sort=birthdate_date:desc

    Paging
    Using the ‘limit’ option, you can narrow down the results to the required number. You can also use ‘offset’ to show the part of the overall results displayed.

    GET /users?limit=120
    GET /users?offset=3
    
    Field Selection
    Using the field selection function, you can request to display a specific part of the data available for that object. While you query an object with many fields, you can specify the fields in your response. An object will have ‘Name’, ‘Surname’, ‘Birthdate’, ‘Email’, ‘Phone’ as its fields.

    For example, when you want to retrieve the birthdate and email to automate birthday wishes. You can use a query like this:

    For a specific user:

    GET/ users/123?fields=name,birthdate,email
    For a full list of users:

    GET/ users?fields=name,birthdate,email

    **[⬆ Back to Top](#table-of-contents)**

13. ### References

    Many articles were followed and among them, certain articles proved to be highly valuable. These articles provided great insight and served as inspiration for writing this article from my own perspective.

    - [medium](https://medium.com/@nadinCodeHat/rest-api-naming-conventions-and-best-practices-1c4e781eb6a5)
    - [freecodecamp](https://www.freecodecamp.org/news/rest-api-best-practices-rest-endpoint-design-examples/)
    - [josipmisko](https://josipmisko.com/posts/rest-api-best-practices)
    - [hevodata](https://hevodata.com/learn/rest-api-best-practices/)
    - [partech](https://www.partech.nl/nl/publicaties/2020/07/9-trending-best-practices-for-rest-api-development#)
    - [stackoverflow](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)
    - [twitter](https://developer.twitter.com/en/docs/api-reference-index)
    - [apidocjs](https://apidocjs.com/example/)
    - [github](https://docs.github.com/en)
    - [github](https://github.com/microsoft/api-guidelines/blob/vNext/Guidelines.md)

    **[⬆ Back to Top](#table-of-contents)**

## Good Practices

- [Microsoft REST API Guidelines](https://github.com/Microsoft/api-guidelines/)
- [Learn REST: A RESTful Tutorial](http://www.restapitutorial.com/) и [книга](https://github.com/tfredrich/RestApiTutorial.com/raw/master/media/RESTful%20Best%20Practices-v1_2.pdf) по мотивам сайта
- [How to design a REST API](http://blog.octo.com/en/design-a-rest-api/)
- [Best Practices for Designing a Pragmatic RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
- [White House Web API Standards](https://github.com/WhiteHouse/api-standards)
- [10 Best Practices for Better RESTful API](http://blog.mwaysolutions.com/2014/06/05/10-best-practices-for-better-restful-api/)
- [API design best practices](http://blogs.mulesoft.com/tag/series/)
- [Создание RESTful API](http://anton.shevchuk.name/php/create-restful-api/)
- [Шпаргалка по созданию RESTful API](http://noteskeeper.ru/1161/)

## Errors and statuses

- [API Best Practices: Response Handling](http://blogs.mulesoft.com/api-best-practices-response-handling/)
- [RESTful API Design: what about errors?](https://blog.apigee.com/detail/restful_api_design_what_about_errors)
- [Error handling considerations and best practices](http://soabits.blogspot.ru/2013/05/error-handling-considerations-and-best.html)

## Pagination

- [API pagination best practices](http://stackoverflow.com/questions/13872273/api-pagination-best-practices)

## Examples

- [twitter](https://dev.twitter.com/rest/public)
- [github](https://developer.github.com/v3/)
- [instagram](https://instagram.com/developer/endpoints/)
- [facebook](https://developers.facebook.com/docs/graph-api/using-graph-api/)
- [vk](http://vk.com/dev/methods)
- [pinterest](https://developers.pinterest.com/docs/api/overview/)

## Tools

- [Swagger Framework for APIs](http://swagger.io/)
- [apiDoc](http://apidocjs.com/)

## Testing in a browser

- [Postman для google chrome](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)

## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
