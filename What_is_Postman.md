# What is Postman?
- Postman is an API (application programming interface) testing tool that helps to build, test, and modify APIs.
- It goes about as a client while testing the application created in a RESTful state.
- You can establish an environment, write test cases, share APIs, and so forth.

# When is It Used?
- At whatever point you wish to test the conduct of your application for a specific API endpoint, in the wake of being mentioned by the customer.
- To see a reaction the server returns after requesting the API endpoint.
- Customizing the requests made to the server, and testing the server's reaction in various conditions.

# Who Uses It?
- __Engineer -__ While making any application, you want to test the endpoints. What ought to be the reaction and the configuration wherein the customer end gets the reaction after being requested?
- __Analyzer/Tester -__ They can set the different conditions in Postman and test the conduct of the application under particular conditions.

# Why Should We Use Postman?
Postman is an essential GUI for sending HTTP requests and overview responses. It depends on a wide course of action of power gadgets, which are incomprehensibly easy to use. Postman helps you with playing out a combination of limits going from:
- A postman is a free tool.
- Postman can make different kinds of HTTP requests(GET, POST, PUT, PATCH), save conditions for some time in the future, changing the API over to code for different languages(like JavaScript, Python).
- Putting together request into collection and folders
- Offering normal qualities across requests with environment variables
- Prearranging tests with the implicit node.js based runtime
- Automate utilizing Postmans own special CLI Newman.
- Postman deals with the start to finish API lifecycle, from configuration, mocking, testing, and sending, right to support and expostulation.
- Postman can be handily incorporated with CI/CD apparatuses like Jenkins.
- Postman gives broad documentation and is generally upheld by the local area.

# What are the different types of variable scopes available in Postman?

Postman provides the following environment variable scopes:
- **Global Variables:** It allows you to access data between collections, requests, test scripts, and environments. Global variables are available throughout a workspace.
- **Environment Variables:** It allows you to tailor your processing to different environments, for example, local development vs testing or production.
- **Local Variables:** They are temporary and only accessible in your request scripts. Local variable values are scoped to a single request or collection run and are no longer available when the run is complete.
- **Collection Variables:** are available throughout the requests in a collection and are independent of environments, so do not change based on the selected environment.
- **Data Variables:** come from external CSV and JSON files to define data sets you can use when running collections via Newman or the Collection Runner.

# What is the order of preference scope for each Postman variable?

If a variable with the same name is declared in two different scopes, the value stored in the variable with the narrowest scope will be used. Below is the preference of the variables in descending order 
    
    Local Variables -> Data Variables -> Environment Variables -> Collection Variables -> Global Variables
    
# How can you log the variable value in Postman?

Variable values can be logged in the Postman console by using the following command: 
    
    console.log(pm.variables.get(“variable_key”));
    
# What is a dynamic variable and how can you use it in Postman?

Postman provides more than 100 dynamic variables which can generate unique random values. Some of the examples are:
    
    {{$guid}}: A v4 style guide
    
    {{$timestamp}}: The current timestamp (Unix timestamp in seconds)
    
    {{$randomInt}}: A random integer between 0 and 1000
    
We can use dynamic variables in pre-request scripts or test scripts using the following script:

    pm.variables.replaceIn(‘{{$randomEmail}}’);
    
# What are the different authorization options available in Postman?

API Requests can be authorized using the following options:
    
- API Key
- Bearer Token
- Basic auth
- Digest auth
- Oauth 1.0
- Oauth 2.0
- Hawk Authentication
- AWS Signature
- NTLM Authentication

# How can you reuse your authentication token for different requests?

We can create a Collection and add all the requests to that collection. We can add the authorization token in the collection and then we can select the “Inherit auth from parent” option as authorization for every request.
    
# What are the types of API Requests which is supported by Postman?

- GET
- POST
- PUT
- PATCH
- DELETE
- COPY
- HEAD
- OPTIONS
- LINK
- UNLINK
- PURGE
- LOCK
- UNLOCK
- PROPFIND and 
- VIEW
    
# What is the difference between Query parameters and Path Variables?

Path Variables is used to identify a specific resource or resources whereas Query Parameter is used to sort/filter those resources.
    
difference between path parameters and query parameters code example
    
***Example 1: QUERY vs PATH parameters***
    
The path parameter is a part of the URL and takes you to the end-point/resources and gives you the result of a query from that resource.
  
The query parameter is NOT a part of the URL and they are added to the URL after the? mark, as key and value it is filtering the result of the query. the endpoint/resource is the same but it acts as a search button and filter the result and returns the response.
    
Additionally, the query parameter can be null but the path parameter can't be null. If you don't append the path parameter, you will get a 404 error. So you can use the path parameter if you want to send the data as mandatory.
    
***Example 2: query vs path parameters***
    
2 TYPES OF PARAMETERS IN REST SERVICES:
    
**1) QUERY PARAMETERS:**
    
- > is NOT part of URL and passed in key=value format those parameters must be defined by the API developer http://34.223.219.142:1212/ords/hr/employees?limit=100
- Query parameters are the most common type of parameters.
- They appear at the end of the request URL after a question mark (?), with different name=value pairs separated by ampersands (&).
- Query parameters can be required and optional.
- GET /pets/findByStatus?status=available
- GET /notes?offset=100&limit=50
    
**2) PATH PARAMETERS**
    
- Path parameters are variable parts of a URI path. They are typically used to point to a specific resource within a collection, such as a user identified by ID. A URL can have several path parameters, each denoted with curly braces { }.
- GET /users/{id}
- GET /cars/{carId}/drivers/{driverId}
- GET /report.{format}

# When to use it?

- If there is a scenario to retrieve a record based on id, for example you need to get the details of the employee whose id is 15, then you can have resources with @PathParam.

- GET /employee/{id}
    
- If there is a scenario where you need to get the details of all employees but only 10 at a time, you may use query param
    
- GET /employee?start=1&size=10 (This says that starting employee id 1 gets ten records.)
    
To summarize, use 

    @PathParam for retrieval based on id,
    and Use @QueryParam for the filter.
    
# What is a Collection in Postman?

We can group requests into collections to keep your workspace organized, collaborate with teammates, generate API documentation, test suites, and automate request runs.
    
# Write test code to check whether the response status is 200 or not?
    
    pm.test("Status code is 200", function () {
    
    pm.response.to.have.status(200);});
    
# In which type of encoding does the postman accept authorization credentials?

Postman accepts authorization in Base64 encoding only. This is provided inbuilt in Postman or else you can also refer to third-party websites to convert the credentials in base64.
    
# Can we have two global scope variables with the same name in Postman?

Since global variables have global scope i.e., without any environment, they cannot have duplicate names.
    
# What is a workspace in Postman?

Work spaces allow us to organize our Postman work and collaborate with teammates. We can group our projects together, with workspace acting as the single source of truth for related APIs, collections, environments, mocks, monitors, and other linked entities.
    
# How many types of work spaces are present in Postman?

There are 2 types of workspaces in Postman:
    
- Personal Workspace: This workspace is only visible to the account user
- Team Workspace: This workspace can be accessed and shared across the team members

# Can we import local variables in Postman Monitors?

Yes. Postman monitors allow to import of local variables but it does not allow to import of global variables.

# What is binary in the Post method in Postman?

The binary form in Postman is designed to send the information in a format that cannot be entered manually. Since everything in a computer is converted to binary, we use these options which cannot be written manually such as an image, a file, etc.
    
# What are the two types of scripts in Postman?

We can write two types of the script in Postman:
    
    - Tests script
    - Pre-request script
# How can Postman collections run through the command line?

Postman collections can be directly run from the command line using the Newman tool. Newman is a Node JS based package, which requires just a node environment to execute the collection and has full parity with the Postman collection runner i.e., the Newman collection runner supports the Postman capabilities like Running assertions, Pre-request scripts, or any other scripts that are associated with the requests that are a part of the collection.
    

To know about API, click **[here](https://github.com/promaafia/API-Application-Programming-Interface/blob/master/What%20Is%20API.md)**

[GitHub - promaafia/API-Application-Programming-Interface](https://github.com/promaafia/API-Application-Programming-Interface)
