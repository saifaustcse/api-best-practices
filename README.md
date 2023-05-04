## Software Design Patterns

> Though there are 1000’s of articles about **Software Design Patterns**, I have written this article is in order to document with simple C# realworld example with short and easy description. I have also created another repository regarding [Software Design principles](https://github.com/saifaustcse/software-design-patterns) which can be helpful as well.

## Give a Star! :star:

> If you like or are using this project to learn or start your solution, please give it a star. Thanks!

## Find me

> Find me if you wish [@Saif(https://www.linkedin.com/in/saif-aust-cse/).

### Table of Contents

| No. | Topic                                                               |
| --- | ------------------------------------------------------------------- |
| 1   | [What are Design Patterns?](#What-are-Design-Patterns)              |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)                   |


1.  ### Use JSON as the Format for Sending and Receiving Data

    In modern API development, JSON (JavaScript Object Notation) has become the standard format for sending and receiving data. It has largely replaced XML and HTML due to its simplicity and widespread support.

    JSON is widely supported by programming languages such as JavaScript, Python, and PHP. These languages provide built-in methods for parsing and manipulating JSON data. For example, Python has json.loads() and json.dumps() for working with JSON.

    When sending JSON data in an API response, it's important to set the Content-Type header to `application/json`. This ensures that the client interprets the data correctly.

    In server-side frameworks like Express, setting the Content-Type header is often handled automatically. Express provides the express.json() middleware specifically for parsing JSON data in the request body. Alternatively, the body-parser NPM package can be used for the same purpose.

    By using JSON as the data format and setting the appropriate Content-Type header, API developers can ensure efficient and reliable data transmission between clients and servers.

    The rewritten information focuses on the benefits of using JSON, highlights the support in various programming languages, and explains the importance of setting the Content-Type header. It also provides specific examples for working with JSON in Python and mentions popular server-side frameworks like Express.


    **[⬆ Back to Top](#table-of-contents)**


2.  ### Use Nouns Instead of Verbs in Endpoints

    When you're designing a REST API, you should not use verbs in the endpoint paths. The endpoints should use nouns, signifying what each of them does.

    This is because HTTP methods such as GET, POST, PUT, PATCH, and DELETE are already in verb form for performing basic CRUD (Create, Read, Update, Delete) operations.

    GET, POST, PUT, PATCH, and DELETE are the commonest HTTP verbs. There are also others such as COPY, PURGE, LINK, UNLINK, and so on.

    So, for example, an endpoint should not look like this:

    https://mysite.com/getPosts or https://mysite.com/createPost

    Instead, it should be something like this: https://mysite.com/posts

    In short, you should let the HTTP verbs handle what the endpoints do. So GET would retrieve data, POST will create data, PUT will update data, and DELETE will get rid of the data.


    **[⬆ Back to Top](#table-of-contents)**



4.  ### Abstract Factory Design Pattern

    Intent

    > Encapsulate a group of individual factories that have a common theme without specifying their concrete classes.

    In simple words we can say, the Abstract Factory is a super factory that creates other factories. This Factory is also called Factory of Factories.

    Advantages

    - Abstract Factory Pattern isolates the client code from concrete (implementation) classes.
    - It eases the exchanging of object families.
    - It promotes consistency among objects.

    We need to choose the Abstract Factory Design Pattern, when

    - The system needs to be independent of how its object are created, composed, and represented.
    - The family of related objects has to be used together, then this constraint needs to be enforced.
    - We want to provide a library of objects that does not show implementations and only reveals interfaces.
    - The system needs to be configured with one of a multiple family of objects.

    <br>
    <details>
    <summary><b>Abstract Factory Design Pattern realword example ()</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace AbsFactoryMethodDesignPattern
        {

        }

    </details>

    <details>
    <summary><b>Abstract Factory Design Pattern realword example ()</b></summary>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FactoryDesignPattern
        {
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**


16. ### References

    I have followed many articles but among them, the following articles are really helpful. Those articles helped me a lot and also encourage me to write this article according to my understanding.

    - [dotnettutorials](https://dotnettutorials.net/course/dot-net-design-patterns/) Design Patterns in C# With Real-Time Examples


    **[⬆ Back to Top](#table-of-contents)**


## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
