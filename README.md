## API Best Practices and Naming Conventions

> API best practices and naming conventions are essential for creating effective and maintainable APIs. These practices and conventions include guidelines for resource naming, versioning, URI structure, error handling, and security, among others. Adhering to these best practices can improve the usability, scalability, and consistency of APIs, and make them easier to use for both developers and end-users.

> In this context, it is important to consider the needs of the target audience and the overall goals of the API when designing and implementing the best practices and naming conventions.

## Give a Star! :star:

> If you find this documentation helpful for learning , please give it a star. Your support is appreciated!

> Find me if you wish [saif](https://www.linkedin.com/in/saif-aust-cse/).

## Table of Contents

| No. | Topic                                                       |
| --- | ----------------------------------------------------------- |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 1   | [Breakdown of the parts a URL](#Breakdown-of-the-parts-URL) |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)           |

## 1. What is REST API?

REST API is an API that follows a set of rules for an application and services to communicate with each other. As it is constrained to REST architecture, REST API is referred to as RESTful API. REST APIs provide a way of accessing web services in a flexible way without massive processing capabilities.

<div  style="text-align: center;">
        <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/rest-api-model.png?raw=true" width="700" height="300">
<div>

REST API standards
The REST API standards are a must-follow for all the REST APIs. The REST API standards have a list of constraints to abide by. These constraints are explained below.

1. Statelessness
   Systems aligning with the REST paradigm are bound to become stateless. For Client-Server communication, stateless constraint enforces servers to remain unaware of the client state and vice-versa. A constraint is applied by using resources instead of commands, and they are nouns of the web that describe any object, document, or thing to store/send to other resources.

2. Cacheable
   Cache helps servers to mitigate some constraints of statelessness. It is a critical factor that has improved the performance of modern web applications. Caching not only enhances the performance on the client-side but also scales significant results on the server-side. A well-established cache mechanism would drastically reduce the average response time of your server.

3. Decoupled
   REST is a distributed approach, where client and server applications are decoupled from each other. Irrespective of where the requests are initiated, the only information the client application knows is the Uniform Resource Identifier (URI) of the requested resource. A server application should pass requested data via HTTP but should not try modifying the client application.

4. Layered System
   A Layered system makes a REST architecture scalable. With RESTful architecture, Client and Server applications are decoupled, so the calls and responses of REST APIs go through different layers. As REST API is layered, it should be designed such that neither Client nor Server identifies its communication with end applications or an intermediary.

5. Client-Server
   The client and server applications must be able to function without the help of each other. Both the server application and the client application must abide by the separation of concerns agreement. By this agreement, when altering the client end, there should not be any impact on the server application. And also, when the code of the server is altered, it should not affect the client end. This enhances the scalability and flexibility of the interface across platforms.

6. Code on demand (optional)
   Of all the constraints, this one is optional. The usual format used while sending resources is JSON REST API or XML. But whenever it is required, you are provided with an option to return executable code. This will support the main part of your application.

## 2. Breakdown of the parts a URL

<div  style="text-align: center;">
        <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_path.png?raw=true" width="700" height="300">
<div>

Here is an example of full path API URLs:

<div  style="text-align: center;">
        <img src="https://github.com/saifaustcse/rest-api-best-practices/blob/main/images/api_url.webp?raw=true" width="700" height="300">
<div>

## 3. Use HTTP methods to communicate intent

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

## 4. Use Appropriate Data Structure

It's a common misconception that REST API must use JSON structure. But REST is all about a resource. That resource can be a JPEG image, HTML document, or any data structure.

Find out what works for you. A lot of company API guidelines force the use of JSON. When using JSON, follow these best practices:

- Use valid JSON Schema for both request and response bodies to ensure consistency and data validation.
- Set the "Content-Type" header to "application/json" in all API requests and responses involving JSON data.
- Utilize JSON even for error messages, avoiding plain text or HTML responses.

**Example API Endpoint: `/user` Method: `POST`**

**Description:** This API allows clients to create a new user by sending a JSON payload in the request. The API will then return a JSON response containing the details of the newly created user.

**Request Payload:**

```json
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "age": 30
}
```

**Response:**

```json
{
  "id": "123456789",
  "name": "John Doe",
  "email": "john.doe@example.com",
  "age": 30,
  "createdAt": "2023-07-19T12:34:56Z"
}
```

By using JSON for both the request payload and the response, the API ensures a standardized data format and efficient data exchange between the client and the server.

## 5. Pick your JSON Field Naming Convention (and Stick to It)

When working with JSON data, it's important to establish a consistent field naming convention for better readability and maintainability. While JSON doesn't enforce any specific naming convention, following a standard practice can greatly improve code consistency. Here are some common conventions along with their descriptions and examples:

1. **snake_case:**

   - Lowercase letters with underscores separating words.
   - Example: "user_name"

2. **camelCase:**

   - Lowercase first letter of the first word, capitalizing the first letter of subsequent words.
   - Example: "userName"

3. **PascalCase:**

   - Capitalizing the first letter of each word.
   - Example: "UserName"

4. **kebab-case:**
   - Lowercase letters with hyphens separating words.
   - Example: "user-name"

Out of these conventions, **camelCase** and **snake_case** are the most widely used and recommended. For consistency, it's best to choose one of these conventions and use it throughout your JSON data structures.

## 3. Use Consistent Error Messages

In API development, relying solely on HTTP status codes to convey error information may not be sufficient for effective error handling. To provide better support for API consumers, it is recommended to include structured JSON error messages in the API responses.

A well-formed error message should consist of the following components:

- **Error Code:** A machine-readable error code that uniquely identifies the specific error condition. This allows developers to programmatically handle different types of errors.

- **Error Message:** A human-readable message that provides a clear and detailed explanation of the encountered error. This helps API consumers understand the issue at hand.

- **Error Context:** Additional information related to the error, such as the request ID, the specific request parameters that triggered the error, or the field(s) in the request causing the issue. Providing contextual data aids in debugging and troubleshooting.

- **Error Links:** URLs to resources or documentation that offer further insights into the error and potential resolutions. These links guide API consumers in resolving the problem efficiently.

- **Timestamp:** The time when the error occurred, enabling developers to identify the exact timing of the issue.

**Example:**

```json
{
  "errorCode": "40001",
  "errorMessage": "Invalid input: Missing 'email' field in the request.",
  "errorContext": {
    "requestId": "123456789",
    "requestParameters": {
      "name": "John Doe",
      "age": 30
    }
  },
  "errorLinks": [
    "https://example.com/docs/errors/40001",
    "https://example.com/support/contact"
  ],
  "timestamp": "2023-07-19T15:30:45Z"
}
```

In this example, the structured JSON error message provides clear information about the encountered error, including an error code, a detailed error message, relevant context data, links for further assistance, and the timestamp of the occurrence. By consistently using such error messages, API developers can greatly improve the error handling experience for consumers.

### 4. Use Status Codes in Error Handling

In API development, employing appropriate HTTP status codes in your responses is crucial for clear and effective communication with API consumers. Status codes provide essential information about the outcome of a request, indicating whether it was successful, encountered an error, or requires redirection. Below are different HTTP status code ranges and their respective meanings:

- **1XX (Informational Responses):** These are informational responses indicating that the server has received the request and is continuing to process it. An example is 102, which signifies that the resource is being processed.

- **3XX (Redirects):** These status codes indicate that further action needs to be taken to complete the request. For instance, 301 indicates that the requested resource has permanently moved to a new location.

- **4XX (Client-side Errors):** Status codes in this range indicate that there was an issue with the client's request. For example, 400 represents a bad request, while 404 indicates that the requested resource was not found.

- **5XX (Server-side Errors):** Status codes in this range indicate that an error occurred on the server while processing the request. For instance, 500 signifies an internal server error.

**Example:**

If a client makes an API request to retrieve a user profile and encounters an error due to an invalid user ID, the server may respond with a 404 status code and a corresponding error message like this:

```json
{
  "statusCode": 404,
  "message": "User not found. Please provide a valid user ID."
}
```

Using proper status codes enhances the clarity of API responses and enables API consumers to understand the outcome of their requests accurately. It's essential to use these status codes consistently to ensure effective error handling and communication with API users.

Reources :

- [API Best Practices: Response Handling](http://blogs.mulesoft.com/api-best-practices-response-handling/)
- [Error handling considerations and best practices](http://soabits.blogspot.ru/2013/05/error-handling-considerations-and-best.html)

## 15. Apply Rate Limit for API Calls

Rate limiting is a vital mechanism to control the number of API requests a client can make within a specified time frame. By implementing rate limits, you can ensure fair usage of your API's resources and protect it from abuse or overloading. Here are key considerations for applying rate limits:

1. **Set Rate Limit Information in API Response:**

   When a client makes a request, include rate limit information in the API response. This typically includes details like the total number of requests allowed within a specific time window, the remaining requests available, and the time period until the limits reset.

2. **Use "429 Too Many Requests" Status Code:**

   To indicate that a client has exceeded its rate limit, return the "429 Too Many Requests" HTTP status code. This informs the client that further requests are temporarily blocked.

3. **Utilize "Retry-After" Header:**

   Include the "Retry-After" header in the response to specify the time duration the client should wait before making additional requests. This helps the client to adjust its behavior and avoid overloading the API.

4. **Consider "Retry-Remaining" Header:**

   Optionally, use the "Retry-Remaining" header to indicate the count of remaining calls available to the client within the given time frame. This can help the client keep track of its usage and plan accordingly.

Rate limiting is a crucial aspect of API management, ensuring a balanced and fair distribution of resources among all users. It helps maintain API stability, reliability, and performance, providing a positive experience for all consumers.

**[⬆ Back to Top](#table-of-contents)**

## 5. Do not use verbs in the URI

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

## 6. Use Plural nouns

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

## 7. Use Lowercase letters

URIs should start with a letter and use only lowercase letters.

Here are a few examples to show how the endpoints should look like,

| Do's       | Don'ts           |
| ---------- | ---------------- |
| GET /users | GET /getAllUsers |
| GET /users | GET /GetAllUsers |
| GET /users | GET /USERS       |

**[⬆ Back to Top](#table-of-contents)**

## 8. Use hyphens (-) to separate words or segments in the URI path

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

## 9. Use Underscore (\_) separate query strings in the URI path

literals or expressions in the query strings are separated using underscores (\_) to improve readability and maintain consistency in URI formatting

Here are a few examples to show how the endpoints should look like,

| Do's                                  | Don'ts                              |
| ------------------------------------- | ----------------------------------- |
| /api/users?sort_by=firstName_desc     | /api/users?sortBy=firstName_desc    |
| /api/users?filter_by=active           | /api/users?filterBy=active          |
| /api/users?page_size=10&page_number=2 | /api/users?pageSize=10&pageNumber=2 |
| /api/users?search_query=john          | /api/users?searchQuery=john         |

**[⬆ Back to Top](#table-of-contents)**

## 10. Use Nesting on Endpoints to Show Relationships

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

## 11. Limit the nesting of resources to a reasonable level by using top-level resources

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

## 12. Use forward slashes (/) for hierarchy but not trailing forward slash (/)

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

## 13. Use Query Component for Filtering, Sorting, Paging, and Field Selection

As your database grows, managing data retrieval can become challenging, especially when you need to retrieve specific data without exposing the entire database. REST APIs provide four types of filtering options: filtering, sorting, paging, and field selection, enabling efficient data retrieval without compromising security or overwhelming the client's bandwidth.

### Filtering

Filtering allows you to retrieve results that meet specific conditions using search parameters such as country, creation date, and more.

Example queries:

- `GET /users?country=UK`
- `GET /users?creation_date=2021-10-11`
- `GET /users?name=John&age=30`

### Sorting

Sorting lets you order results in ascending or descending order based on a specified field.

Example queries:

- `GET /users?sort=birthdate:asc`
- `GET /users?sort=creation_date:desc`

### Paging

Paging helps narrow down results by specifying the number of items to display and the offset to skip.

Example queries:

- `GET /users?limit=50`
- `GET /users?limit=20&offset=40`

### Field Selection

Field selection allows you to request specific fields of an object in the API response, especially when querying objects with many fields.

Example queries:

- For a specific user:
  `GET /users/123?fields=name,email`
- For a list of users:
  `GET /users?fields=name,email`

By utilizing these query options, your API becomes more flexible and user-friendly, enabling clients to retrieve precisely the data they need with minimal overhead. It's essential to document these query parameters to guide API consumers effectively.

**[⬆ Back to Top](#table-of-contents)**

## 14. Version Your APIs

Versioning your APIs is crucial for providing a smooth upgrade path and maintaining backward compatibility when making changes. It ensures that clients can adapt to new features and improvements without disrupting existing functionality. Here are some best practices for versioning your APIs:

1. **Use URL Versioning:**

   Incorporate the API version directly into the URL to distinguish different versions. For example:

   - `http://api.example.com/v1/store/employees/{emp-id}`
   - `http://api.example.com/v1/store/items/{item-id}`
   - `http://api.example.com/v2/store/employees/{emp-id}/address`

2. **API Documentation:**

   Clearly document each API version, specifying the changes, additions, and deprecations introduced in each version. This helps users understand the differences and plan for migration.

3. **Semantic Versioning:**

   Consider adopting Semantic Versioning (SemVer) to indicate the extent of changes in each API version. SemVer follows the format of `MAJOR.MINOR.PATCH`, where:

   - `MAJOR` version is incremented for incompatible changes.
   - `MINOR` version is incremented for backward-compatible additions.
   - `PATCH` version is incremented for backward-compatible bug fixes.

4. **Deprecation Policy:**

   Clearly communicate the deprecation policy for older API versions, informing users when a version will no longer be supported. This allows clients to plan their migration to the latest version.

By following these versioning practices, you can provide a stable and reliable API experience for your users while continuously improving and evolving your API without disrupting their existing integrations.

**[⬆ Back to Top](#table-of-contents)**

## 16. References

Many articles were followed and among them, certain articles proved to be highly valuable. These articles provided great insight and served as inspiration for writing this article from my own perspective.

- [medium](https://medium.com/@nadinCodeHat/rest-api-naming-conventions-and-best-practices-1c4e781eb6a5)
- [freecodecamp](https://www.freecodecamp.org/news/rest-api-best-practices-rest-endpoint-design-examples/)
- [josipmisko](https://josipmisko.com/posts/rest-api-best-practices)
- [hevodata](https://hevodata.com/learn/rest-api-best-practices/)
- [partech](https://www.partech.nl/nl/publicaties/2020/07/9-trending-best-practices-for-rest-api-development#)

**[⬆ Back to Top](#table-of-contents)**

## Good Practices

- [stackoverflow](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)
- [Microsoft REST API Guidelines](https://github.com/Microsoft/api-guidelines/)
- [Learn REST: A RESTful Tutorial](http://www.restapitutorial.com/)
- [How to design a REST API](http://blog.octo.com/en/design-a-rest-api/)
- [Best Practices for Designing a Pragmatic RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
- [White House Web API Standards](https://github.com/WhiteHouse/api-standards)

## API Documentation Examples

- [twitter](https://dev.twitter.com/rest/public)
- [github](https://docs.github.com/en)
- [instagram](https://instagram.com/developer/endpoints/)
- [facebook](https://developers.facebook.com/docs/graph-api/using-graph-api/)
- [pinterest](https://developers.pinterest.com/docs/api/overview/)

## API Documentation and Testing Tools

- [Swagger Framework for APIs](http://swagger.io/)
- [apiDoc](http://apidocjs.com/)
- [postman](https://www.postman.com/)

## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
