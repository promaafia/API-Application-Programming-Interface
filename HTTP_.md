# What is HTTP?
The Hypertext Transfer Protocol (HTTP) is designed to enable communications between clients and servers. HTTP works as a request-response protocol between a client and server. A web browser may be the client, and an application on a computer that hosts a website may be the server.

#### Example: 
A client (browser) submits an HTTP request to the server; then the server returns a response to the client. The response contains status information about the request and may also contain the requested content.

# Most Common HTTP Methods
- **GET:** The GET method is used to retrieve information from the given server using a given URI. Requests using GET should only retrieve data and should have no other effect on the data.
- **POST:** A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms.
- **PUT:** PUT is used to send data to a server to create/update a resource. Replaces all the current representations of the target resource with the uploaded content.
- **PATCH:** PATCH is used to update partial resources. For instance, when you only need to update one field of the resource, PUTting a complete resource representation might be cumbersome and utilize more bandwidth.
- **HEAD:** HEAD is almost identical to GET but without the response body. HEAD transfers the status line and the header section only.
- **DELETE:** The DELETE method deletes the specified resource.
- **OPTIONS:** The OPTIONS method describes the communication options for the target resource.

