# Making the first HTTP request in Postman
Since we have installed the Postman app successfully, it is now time to start testing the API with Postman by making the first-ever HTTP request to the server.

# Testing GET Requests
Let’s now jump directly to test those API. Suppose we have an API that fetches the user information of a particular application. To test this we will have to use a GET request. The GET request is explained below:

For sample requests, visit https://reqres.in

#### For making the first HTTP request(GET):
        

- Make a collection in Postman — To make a collection in Postman, click on New->Collection->CollectionDemo(Any Collection Name you wish)->Create
- Make a Request — To make a request, click on New->Request->GetUser(Any request name you wish)->Select the Collection you wish to save request in(Present in the bottom of the dialog box)->Save to Collection Demo
- By now, we have created our first request, now we need to pass different parameters in the request to get the expected response.
- In the “Enter Request URL” text box type: https://reqres.in/api/users?page=1
- Click on the “Send” Button
- You should be able to see the below response in the Body section:
- You should be delighted you have successfully tested your first API request.
- Also, check for the correct status code, in this case, you should get: ‘Status:201 Created’

# Testing POST Requests

Now, suppose we need to create a user into an application that means we are sending data or feeding data to an application. For these types of requests, we use POST requests. In POST requests we send data/parameters in the body of the request, and in response to that, API returns some data to us which validates the user has been created. The response can either be a success message or the id of the new user-created and the time when the user was created.

#### For making the first HTTP request(POST):

**POST Request —** To make a POST request, click on 
    
    New->Request->CreateUser(Any request name you wish)
    ->Select the Collection you wish to save request in(Present in the bottom of the dialog box)
    ->Save to Collection Demo

- From the Dropdown select POST
- In the “Enter Request URL” text box, type: https://reqres.in/api/users
- Click on Body Tab and select the “Raw” radio button
- In the text box, paste :
```bash
{
    "name": "morpheus",
    "job": "leader"
}
```
- Click on the Send button
- User should see the below response:
 
- Also, check for the correct status code, in this case, you should get: ‘Status:201 Created’
 
You have successfully tested your POST request too, similarly, you can try your hands with PUT, PATCH, DELETE, etc.

- Check for the expected response.
- Check for the correct status code.
- Check for Time (Response Time), it should be acceptable as per business.
- Always perform negative tests to verify that the API doesn’t respond if data tampering.



*__Happy Testing!!__*

Testing the Postman API following points should be considered:

- Check the expected result
- Check for the correct status code
- Check for response time
- Negative test to perform that API doesn’t respond if data has tampered.

Postman allows running the collection containing a group of APIs using the feature called “Collection runner” and shows the result with the count of Pass and Fail test.
A postman is a great tool when trying to dissect RESTful APIs made by others or test ones you have made yourself. It offers a sleek user interface with which to make HTML requests, without the hassle of writing a bunch of code just to test an API's functionality.
 

# Why Use a Postman?
With more than 4 million clients these days, Postman Software has turned into an instrument of decision for the accompanying reasons:

**Availability -** To utilize the Postman instrument, one would simply have to sign in to their own records making it simple to get to documents whenever anyplace up to a Postman application is introduced on the PC.

**The utilization of Collections -**  Postman allows clients to make assortments for their Postman API calls. Every assortment can make subfolders and different solicitations. This aids in getting sorted out your test suites.

**Cooperation -** Collections and conditions can be imported or traded making it simple to share documents. An immediate connection can likewise be utilized to share assortments.
 
**Establishing Environments -** Having numerous conditions supports less redundancy of tests as one can utilize a similar assortment yet for an alternate climate. This is the place where definition will happen which we will examine in additional illustrations.

**Formation of Tests -** Test designated spots, for example, checking for fruitful HTTP reaction status can be added to every Postman API call which guarantees test inclusion.

**Automation Testing -** Through the utilization of the Collection Runner or Newman, tests can be run in different emphases saving time for redundant tests.
 
**Troubleshooting/Debugging -** Postman console assists with checking what information has been recovered making it simple to investigate tests.
 
**Persistent Integration -** With its capacity to help constant mix, advancement rehearses are kept up with.
