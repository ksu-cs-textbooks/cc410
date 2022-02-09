---
title: "Documenting Web APIs"
weight: 20
pre: "4. "
---

Web APIs are very useful parts of the internet today, but their usefulness can be limited if they aren't properly documented. Thankfully, there are many standards available for documenting how to use and interact with RESTful web APIs. 

## RESTful API Description Languages

Wikipedia has a list of [RESTful API Description Lanuages](https://en.wikipedia.org/wiki/Overview_of_RESTful_API_Description_Languages), or DLs, that are meant to provide a formal way for documenting the structure and usage of a web API. This is very similar to the standard format we use for documentation comments in our code - if they are structured correctly, we can use other tools such as `javadoc` or `pdoc` to generate additional resources for us, such as developer documentation.

These DLs follow a similar concept - by standardizing the structure of the documentation for the web API, we can build additional tools that use that information for a variety of different uses. For example, it could generate a website containing all of the documentation required to interact with the library, just like we are able to do with our existing source code comments.

However, another great use of these tools would be to build software libraries that can be used to interface directly with the web API itself. The library would include functions that match each API endpoint, including the expected parameters and values. Then, when we call the functions in our code, the library would handle constructing the request, sending it to the API endpoint, and receiving and even parsing the response for us. This would allow us to even quickly develop libraries that can interact with our API in a variety of programming languages.

## OpenAPI

One of the most common RESTful API DLs used today is the [OpenAPI Specification](https://www.openapis.org/). It is supported by a large number of both open-source and enterprise tools for constructing the document itself, as well code generators for a variety of languages.

Let's look at the structure of a single endpoint to see what it looks like in the OpenAPI Specification. This example comes from their [Getting Started](https://oai.github.io/Documentation/specification-paths.html) document.

![Path Object](/images/18/paths-object.svg)[^1]

[^1]: https://oai.github.io/Documentation/specification-paths.html

This diagram shows how the OpenAPI Specification follows a hierarchical structure for each API endpoint, called a "path" in OpenAPI, is documented. Each path can have multiple operations defined, such as GET, PUT, POST, DELETE, which easily correspond to various HTTP methods. Each of those operations contains additional information about the data expected in the request and possible HTTP responses that could be returned.

For example, here is a short snippet of an OpenAPI Specification document for a web API for playing the classic [Tic Tac Toe](https://en.wikipedia.org/wiki/Tic-tac-toe) game:

```yaml
openapi: 3.1.0
info:
  title: Tic Tac Toe
  description: |
    This API allows writing down marks on a Tic Tac Toe board
    and requesting the state of the board or of individual squares.
  version: 1.0.0
paths:
  # Whole board operations
  /board:
    get:
      summary: Get the whole board
      description: Retrieves the current state of the board and the winner.
      responses:
        "200":
          description: "OK"
          content:
            $ref: "#/components/schemas/status"
```

So, this API contains an endpoint with the URL ending in `/board`, which can be used to get the whole board. Further in the document, it describes what that status message could contain:

```yaml
  schemas:
    ...
    status:
      type: object
      properties:
        winner:
          $ref: "#/components/schemas/winner"
        board:
          $ref: "#/components/schemas/board"
```

So, we know that the status message would contain the winner of the game, if any, as well as the board. Those two objects are described as:

```yaml
  schemas:
    ...
    board:
      type: array
      maxItems: 3
      minItems: 3
      items:
        type: array
        maxItems: 3
        minItems: 3
        items:
          $ref: "#/components/schemas/mark"
    winner:
      type: string
      enum: [".", "X", "O"]
      description: Winner of the game. `.` means nobody has won yet.
      example: "."
```

So, the board is just a 3 by 3 array, and the winner message is the character of the winning player. 

As we can see, this document clearly describes everything a developer would need to know about the `/board` enpoint, including how to use it and what type of response would be returned. 

The full [Tic Tac Toe](https://oai.github.io/Documentation/examples/tictactoe.yaml) example is full of additional information about the entire API itself. 
