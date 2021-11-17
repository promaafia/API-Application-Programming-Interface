# Terminologies of  Postman
#### API
Application Programming Interface (API) is software that acts as an intermediary for two apps to communicate with each other. We use APIs whenever we use an application like Twitter, Facebook, sending text messages, or checking the weather over the phone.
#### HTTP
HTTP (Hypertext Transfer Protocol) is the collection of rules for the transmission of data on the World Wide Web, like graphic images, text, video, sound, and other multimedia data. The Web users implicitly make use of HTTP as soon as they open their Web browser.
API Response code
 
#### There are five values for the first digit:
- **1xx (Informational):** The request is received and continues to be processed
- **2xx (Successful):** The request is successfully received, understood, and accepted
- **3xx (Redirection):** Further action needs to be taken to complete the request
- **4xx (Client Error):** The request contains the wrong syntax or cannot be fulfilled
- **5xx (Server Error):** The server fails to fulfill an apparently valid request

However, the actual response status code of an API is specified by the development team that built the API. So as a tester, you need to verify whether:
- The code follows global standard classes
- The code is specified in the requirement.

# Positive Test
Verify that the API receives input and returns the expected output as specified in the requirement.
Verify that the response status code is returned as specified in the requirement, whether it returns a 2xx or error code.
Specify input with minimum required fields and with maximum fields.

# Negative Test
Verify that the API returns an appropriate response when the expected output does not exist.
Perform input validation test.
Verify the API’s behaviors with different levels of authorization.

**HTTP** defines a set of request methods to indicate the desired action to be performed for a given resource. Although they can also be nouns, these request methods are sometimes referred to as HTTP verbs. Each of them implements a different semantic, but some common features are shared by a group of them: e.g. a request method can be safe, idempotent, or cacheable.
### GET
The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.
### HEAD
The HEAD method asks for a response identical to a GET request, but without the response body.
### POST
The POST method submits an entity to the specified resource, often causing a change in state or side effects on the server.
### PUT
The PUT method replaces all current representations of the target resource with the request payload.
### DELETE
The DELETE method deletes the specified resource.
### CONNECT
The CONNECT method establishes a tunnel to the server identified by the target resource.
### OPTIONS
The OPTIONS method describes the communication options for the target resource.
### TRACE
The TRACE method performs a message loop-back test along the path to the target resource.
### PATCH
The PATCH method applies partial modifications to a resource.

# GET
GET requests are the most common and widely used method in APIs and websites. Simply put, the GET method is used to retrieve data from a server at the specified resource. For example, say you have an API with a /users endpoint. Making a GET request to that endpoint should return a list of all available users.
Since a GET request is only requesting data and not modifying any resources, it's considered a safe and idempotent method.
### Testing an API with GET Requests
When you're creating tests for an API, the GET method will likely be the most frequent type of request made by consumers of the service, so it's important to check every known endpoint with a GET request.

At a basic level, these things should be validated:
- Check that a valid GET request returns a 200 status code.
- Ensure that a GET request to a specific resource returns the correct data. For example, GET /users return a list of users.
GET is often the default method in HTTP clients, so creating tests for these resources should be simple with any tool you choose.

# POST
In web services, POST requests are used to send data to the API server to create or update a resource. The data sent to the server is stored in the request body of the HTTP request.

The simplest example is a contact form on a website. When you fill out the inputs in a form and hit Send, that data is put in the response body of the request and sent to the server. This may be JSON, XML, or query parameters (there's plenty of other formats, but these are the most common).

It's worth noting that a POST request is non-idempotent. It mutates data on the backend server (by creating or updating a resource), as opposed to a GET request which does not change any data.

### Testing an API with POST Requests
The second most common HTTP method you'll encounter in your API tests is POST. As mentioned above, POST requests are used to send data to the API server and create or update a resource. Since POST requests modify data, it's important to have API tests for all of your POST methods.

Here are some tips for testing POST requests:
- Create a resource with a POST request and ensure a 200 status code is returned.
- Next, make a GET request for that resource and ensure the data was saved correctly.
- Add tests that ensure POST requests fail with incorrect or ill-formatted data.

# PUT

Similar to POST, PUT requests are used to send data to the API to update or create a resource. The difference is that PUT requests are idempotent. That is, calling the same PUT request multiple times will always produce the same result. In contrast, calling a POST request repeatedly has the side effects of creating the same resource multiple times.

Generally, when a PUT request creates a resource the server will respond with a 201 (Created), and if the request modifies existing resource the server will return a 200 (OK) or 204 (No Content).

### Testing an API with PUT Requests

Testing an APIs PUT method is very similar to testing POST requests. But now that we know the difference between the two (idempotency), we can create API tests to confirm this behavior.

Check for these things when testing PUT requests:
- Repeatedly calling a PUT request always returns the same result (idempotent).
- The proper status code is returned when creating and updating a resource (eg, 201 or 200/204).
- After updating a resource with a PUT request, a GET request for that resource should return the correct data.
- PUT requests should fail if invalid data is supplied in the request **-- nothing should be updated.**

# PATCH

A PATCH request is one of the lesser-known HTTP methods, but I'm including it this high in the list since it is similar to POST and PUT. The difference with PATCH is that you only apply partial modifications to the resource.

The difference between PATCH and PUT is that a PATCH request is non-idempotent (like a POST request).

To expand on partial modification, say your API has a /users/{{userid}} endpoint, and a user has a username. With a PATCH request, **you may only need to send the updated username** in the request body - as opposed to POST and PUT which require the full user entity.

### Testing an API with PATCH Requests

Since the PATCH method is so similar to POST and PUT, many of the same testing techniques apply. It's still important to validate the behavior of any API endpoints that accept this method.

What to look for when testing PATCH requests:
- A successful PATCH request should return a 2xx status code.
- PATCH requests should fail if invalid data is supplied in the request -- nothing should be updated.

*The semantics of PATCH requests will largely depend on the specific API you're testing.*

# DELETE

The DELETE method is exactly as it sounds: **delete the resource at the specified URL.** This method is one of the more common in RESTful APIs so it's good to know how it works.

If a new user is created with a POST request to /users, and it can be retrieved with a GET request to /users/{{userid}}, then making a DELETE request to /users/{{userid}} will completely remove that user.

### Testing an API with DELETE Requests

DELETE requests should be heavily tested since they generally remove data from a database. Be careful when testing DELETE methods, make sure you're using the correct credentials and not testing with real user data.

A **typical test case for a DELETE request** would look like this:
- Create a new user with a POST request to /users
- With the user id returned from the POST, make a DELETE request to /users/{{userid}}
- A subsequent GET request to /users/{{userid}} should return a 404 not found status code.

In addition, sending a DELETE request to an unknown resource should return **a non-200 status code.**

# HEAD

The HEAD method is almost identical to GET, except without the response body. In other words, if GET /users return a list of users, then HEAD /users will make the same request but won't get back the list of users.

HEAD requests are useful for checking what a GET request will return before actually making a GET request -- like before downloading a large file or response body.

*It's worth pointing out that not every endpoint that supports GET will support HEAD - it completely depends on the API you're testing.*

### Testing an API with HEAD Requests

Making API requests with HEAD methods is actually an effective way of simply verifying that a resource is available. It is good practice to have a test for HEAD requests everywhere you have a test for GET requests (as long as the API supports it).

Check these things when testing an API with HEAD requests:
- Verify and check HTTP headers returned from a HEAD request
- Make assertions against the status code of HEAD requests
- Test requests with various query parameters to ensure the API response

Another useful case for HEAD requests is API smoke testing - **make a HEAD request against every API endpoint** to ensure they're available.

# OPTIONS
Last but not least we have OPTIONS requests. OPTIONS requests are one of my favorites, though not as widely used as the other HTTP methods. In a nutshell, an OPTIONS request should **return data describing what other methods and operations the server supports** at the given URL.

OPTIONS requests are more loosely defined and used than the others, making them a good candidate to test for fatal API errors. If an API isn't expecting an OPTIONS request, it's good to put a test case in a place that verifies failing behavior.

### Testing an API with OPTIONS Requests

Testing an OPTIONS request is dependent on the web service; whether or not it supports that and what is supposed to return will **define how you should test it.**

How to validate an endpoint using OPTIONS:
- Primarily, check the response headers and status code of the request
- Test endpoints that don't support OPTIONS, and ensure they fail appropriately

# More Resources
What I've discussed above is just a starting point for digging into HTTP methods and testing various resources of an API. It also assumes a most ideal case - in the real world, APIs are not as structured as the examples above. This makes testing various methods against an API an effective way to find unexpected bugs.


| HTTP Verb | CRUD | Entire Collection (e.g. /customers) | Specific Item (e.g. /customers/{id}) |
| --------- | ---- | ----------------------------------- | ------------------------------------ | 
| POST | Create| 201 (Created), 'Location' header with link to /customers/{id} containing new ID. | 404 (Not Found), 409 (Conflict) if the resource already exists. |
| GET | Read | 200 (OK), list of customers. Use pagination, sorting, and filtering to navigate big lists. | 200 (OK), the single customer. 404 (Not Found), if ID not found or invalid. |
| PUT | Update/Replace | 405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| PATCH | Update/Modify | 405 (Method Not Allowed), unless you want to modify the collection itself. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| DELETE | Delete | 405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable. | 200 (OK). 404 (Not Found), if ID not found or invalid. |

# Summary
- API Testing using Postman: Postman is an application for testing APIs. Postman is one of the most popular tools used in API testing by sending requests to the webserver and getting the response back
- Accessibility, Use of Collections, Collaboration, Continuous Integration, are some of the key features to learn in Postman
- It’s recommended you create an account in Postman, so your collections are available online
- You can parameterize requests in Postman
- You can create Tests to verify a postman request
- Collections can be run using Newman or Collection Runner
 

