## API Best Practices and Naming Conventions

> API best practices and naming conventions are essential for creating effective and maintainable APIs. These practices and conventions include guidelines for resource naming, versioning, URI structure, error handling, and security, among others. Adhering to these best practices can improve the usability, scalability, and consistency of APIs, and make them easier to use for both developers and end-users.

> In this context, it is important to consider the needs of the target audience and the overall goals of the API when designing and implementing the best practices and naming conventions.

## Give a Star! :star:

> If you find this documentation helpful for learning , please give it a star. Your support is appreciated!

> Find me if you wish [saif](https://www.linkedin.com/in/saif-aust-cse/).

### Table of Contents

| No. | Topic                                                       |
| --- | ----------------------------------------------------------- |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)           |

What is REST API?

1.  ### What is REST API?

1.  ### Breakdown of the parts a URL

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_path.png?raw=true" width="700" height="300">
    <div>

    Here is an example of full path API URLs:

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_url.webp?raw=true" width="700" height="300">
    <div>

1.  ### Use JSON as the Format for Sending and Receiving Data

- REST APIs can use various data structures, not limited to JSON. Resources can be images, HTML documents, or any other data format.
- JSON is commonly used in many company API guidelines due to its popularity and widespread support.
- When using JSON, adhere to best practices:
  - Use valid JSON Schema for both request and response bodies to ensure consistency and data validation.
  - Set the "Content-Type" header to "application/json" in all API requests and responses involving JSON data.
  - Utilize JSON even for error messages, avoiding plain text or HTML responses.

Here's an example of a simple API that accepts JSON payloads in requests and returns JSON in responses:

**API Endpoint:** `/user`

**Method:** POST

**Description:** This API allows clients to create a new user by sending a JSON payload in the request. The API will then return a JSON response containing the details of the newly created user.

    **Request Payload:**

    {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "age": 30
    }

    **Response:**

    {
    "id": "123456789",
    "name": "John Doe",
    "email": "john.doe@example.com",
    "age": 30,
    "createdAt": "2023-07-19T12:34:56Z"
    }

    In this example, the client sends a JSON payload with the user's name, email, and age in the request. The server processes the request, creates a new user, and responds with a JSON object containing the newly created user's details, including an automatically generated `id` and `createdAt` timestamp.

    By using JSON for both the request payload and the response, the API ensures a standardized data format and efficient data exchange between the client and the server.

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

4.  ### Use appropriate data structure

    It's a common misconception that REST API must use JSON structure. But REST is all about a resource. That resource can be a JPEG image, HTML document, or any data structure.

    Find out what works for you. A lot of company API guidelines force the use of JSON.

    Valid JSON schema
    If you use JSON, follow these best practices:

    Valid JSON Schema should be used for both request and response bodies.
    Include the "Content-Type" header set to "application/json" in all requests and responses when sending JSON data.
    Use JSON even when communicating error messages. Don't just return plain text or HTML.

5.  ### Pick your JSON field naming convention (and stick to it)

    JSON standard doesn't impose a field naming convention, but it's a best practice to pick one and stick with it.

    Convention Description Example
    snake_case Lowercase letters with underscores separating words "user_name"
    camelCase
    Lowercase first letter of first word, capitalizing the first letter of subsequent words

    "userName"
    PascalCase Capitalizing the first letter of each word "UserName"
    kebab-case Lowercase letters with hyphens separating words "user-name"
    camelCase and snake_case are the most common. I prefer camelCase and I don't recommend PascalCase or kebab-case.

6.  ### Do not use verbs in the URI

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

7.  ### Use Plural nouns

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

8.  ### Use Lowercase letters

    URIs should start with a letter and use only lowercase letters.

    Here are a few examples to show how the endpoints should look like,

    | Do's       | Don'ts           |
    | ---------- | ---------------- |
    | GET /users | GET /getAllUsers |
    | GET /users | GET /GetAllUsers |
    | GET /users | GET /USERS       |

    **[⬆ Back to Top](#table-of-contents)**

9.  ### Use hyphens (-) to separate words or segments in the URI path

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

10. ### Use Underscore (\_) separate query strings in the URI path

    literals or expressions in the query strings are separated using underscores (\_) to improve readability and maintain consistency in URI formatting

    Here are a few examples to show how the endpoints should look like,

    | Do's                                  | Don'ts                              |
    | ------------------------------------- | ----------------------------------- |
    | /api/users?sort_by=firstName_desc     | /api/users?sortBy=firstName_desc    |
    | /api/users?filter_by=active           | /api/users?filterBy=active          |
    | /api/users?page_size=10&page_number=2 | /api/users?pageSize=10&pageNumber=2 |
    | /api/users?search_query=john          | /api/users?searchQuery=john         |

    **[⬆ Back to Top](#table-of-contents)**

11. ### Use Nesting on Endpoints to Show Relationships

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

12. ### Limit the nesting of resources to a reasonable level by using top-level resources

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

13. ### Use forward slashes (/) for hierarchy but not trailing forward slash (/)

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

14. ### Use query component to filtering, sorting, paging, and field selection

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

15. ### Use consistent error messages

    In most cases, HTTP status codes are not enough to explain what went wrong.

    To help your API consumers, include a structured JSON error message.

    The response should include the following information:

    Error code: A machine-readable error code that identifies the specific error condition.
    Error message: A human-readable message that provides a detailed explanation of the error.
    Error context: Additional information related to the error, such as the request ID, the request parameters that caused the error, or the field(s) in the request that caused the error.
    Error links: URLs to resources or documentation that provide additional information about the error and how it can be resolved.
    Timestamp: The time when the error occurred.

16. ### Use Status Codes in Error Handling

    You should always use regular HTTP status codes in responses to requests made to your API. This will help your users to know what is going on – whether the request is successful, or if it fails, or something else.

    Below is a table showing different HTTP Status Code ranges and their meanings:

    STATUS CODE RANGE MEANING
    100 – 199 Informational Responses.
    For example, 102 indicates the resource is being processed
    300 – 399 Redirects
    For example, 301 means Moved permanently
    400 – 499 Client-side errors
    400 means bad request and 404 means resource not found
    500 – 599 Server-side errors
    For example, 500 means an internal server error

17. ### Version your APIs

    Always attempt to version your APIs. You can provide an upgrade path without making any fundamental changes to the existing APIs by versioning your APIs. You can also let users know that updated versions of the API are accessible at the following fully-qualified URIs.

    http://api.example.com/v1/store/employees/{emp-id}
    Introduction in any major breaking update can be avoided with the following /v2.

    http://api.example.com/v1/store/items/{item-id}
    http://api.example.com/v2/store/employees/{emp-id}/address

18. ### Consider applying a rate limit for API calls

    Rate limiting is a technique for limiting the number of API requests that a client can make in a given time period.

    The API response will usually include information about the rate limit and the client's current usage, so that the client can adjust its behavior accordingly.

    A "429 Too Many Requests" HTTP status code and the "Retry-After" header are commonly used to enforce rate limits on API calls.

    The 429 Too Many Requests error status code indicates that the user has sent too many requests in a given amount of time and the API has temporarily blocked further requests from that user.
    The Retry-After header specifies the amount of time the user must wait before making additional requests.
    The Retry-Remaining header specifies the count of remaining calls in the given time frame.

19. ### References

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
