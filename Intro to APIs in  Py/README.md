# Introduction to APIs in Python (RESTful)

## Chapter 1: Making API Requests with Python
1. [Introduction to APIs](#introduction-to-apis)
2. [The Basic Anatomy of an API Request](#the-basic-anatomy-of-an-api-request)
3. [Headers and Status Code](#headers-and-status-code)

## Chapter 2: More API Request Concepts
1. [API Authentication](#api-authentication)
2. [Working with Structured Data](#working-with-structured-data)
3. [Error Handling](#error-handling)

---

# Chapter 1: Making API Requests with Python

## Introduction to APIs
A brief overview of what APIs are and how they enable communication between software components.


1. **Web APIs**<br><br>
   APIs come in many different styles and flavors, but for the purpose of this course, we will be focusing on Web APIs. Web APIs are used to enable communication between two software applications over a network or the internet. This communication uses the HTTP protocol, the same protocol our browser uses to retrieve webpages from the internet. In practice, this means a client sends a message over the internet to a server; the server, in turn, responds by sending a message back to the client.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/98ca49ea-6f2f-4e37-a581-7087e40d8c0e" width="700"></p>

2. **Types of Web APIs**<br><br>
   Let's discuss the three most common types of Web APIs. SOAP takes a very formal approach and is most often used in enterprise applications where robustness and strict protocols are required. REST, the most popular and most common type, is known for its simplicity, scalability, and ease of integration. GraphQL takes a more sophisticated approach, focusing on precise and flexible data retrieval, minimizing data transfer, and optimizing for performance. In this course, we will work with REST APIs, as it is the most common.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/da1f8c33-195b-4ce5-80f4-3f2bc33a8382" width="700"></p>

3. **Working with APIs in Python**<br><br>
   Let's discuss two well-known Python libraries for integrating Web APIs, `urllib` and `requests`. Urllib comes bundled with Python and is a very powerful module, but that goes at the cost of simplicity. Here we are making a request to the music catalog Web API to get a list of music albums. To print the data we requested, we first need to use the `urlopen` function to send a request, then use the `read()` function on the response object to get the response data. After that, we call the `decode()` function on the response data to extract the raw data, and then we can finally print the data we received from the API. Luckily, the requests package simplifies things a lot. Requests offers many built-in features which urllib needs additional steps or packages for. In this example, we achieve the same result with a lot less code using the `requests.get()` function. Requests takes care of reading and decoding the response; all we need to do is print the text attribute of the response object.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/cd14305f-8ba1-498e-b2cc-d9b1be039298" width="700"></p>

### Exercises
   <p align="center"><img src="https://github.com/user-attachments/assets/d1ed1ba7-806a-40cd-a237-c0a2757f30f4" width="1000"></p>
   <p align="center"><img src="https://github.com/user-attachments/assets/1c3d5932-1586-493c-a7a9-9ed8ca693774" width="1000"></p>

## The Basic Anatomy of an API Request

1. **The Basic Anatomy of an API Request**<br><br>
   Fetching data from an API is straightforward; now, let's learn how we can use the requests package to give more detailed instructions to an API.

2. **What are URLs?**<br><br>
   URLs are a fundamental concept in Web APIs. A URL is a structured address pointing to a specific resource. Via a URL, we can specify what resource we want to interact with. For this example, we'll compare a REST API to an office building; each office unit is a unique resource. The URL is the address of a single unit in the building. It contains all the information needed to navigate to that specific unit.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/9d945819-a60b-4451-8f11-54afbdf2f617" width="700"></p>

3. **Dissecting the URL**<br><br>
   Let's break URLs down into its five main components. First is the protocol. This determines the transportation to use when navigating to the destination, walking or driving, for example. The second component is the domain; it is like the street address of the office building. It uniquely identifies the location of the API server on the internet. Third is the port, the gateway or entrance into the office building. When traveling by car, we enter through the garage. Common default ports are 80 and 443. The path component determines the specific office unit in the building. With APIs, each resource has a unique location on the server, defined by its path. The last component is the query, which contains additional instructions. It specifies instructions like "take the elevator," for example. By constructing a URL with a path and parameters, we can control where to send our API requests to.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/90c0380f-e907-40a1-adec-e5c74c43894e" width="700"></p>

4. **Adding Query Parameters with Requests**<br><br>
   Adding a query parameter using the requests package is very easy. We might want to just append the query parameter to the URL string, which works fine, but there is a better way. Each HTTP method from the requests package, such as `get`, accepts an additional argument called `params` which accepts a dictionary with key/value pairs, one for each query parameter. See how much easier that code is?<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/2394bc3d-da65-45d2-815c-21b3baad27a1" width="700"></p>

5. **HTTP Verbs**<br><br>
   Let's send a package to the DataCamp office! Using the URL, we have constructed the destination of our package: the mailbox of unit 243 in the Empire State building. But how do we now define what to do with the package when we arrive at our destination? This is where HTTP verbs come in. Every request uses one of 9 HTTP verbs; let's learn the four most important ones. GET is used to read a resource. It's like checking the contents of the mailbox without taking anything out. POST is creating a resource, like dropping a new package in the mailbox. PUT updates a resource, like replacing a package that was already in the mailbox. And DELETE removes all packages from the mailbox, leaving it empty.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/43b58fe6-9b9a-4f85-9482-dd98b3a5e092" width="700"></p>

6. **Sending Data via POST and PUT**<br><br>
   With the requests package, we have easy access to all HTTP verbs as functions; we already saw the `requests.get()` function. For POST and PUT requests, we need to add data to create or update our resources. Similar to how we can pass a `params` argument to set query parameters, we can also pass a `data` argument to specify the data we want to send along with the request. Making a DELETE request is even simpler. Just use the `delete` function instead of the `get` function.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/b453cd21-71cc-41ef-9617-0b1bff47c94b" width="700"></p>

### Exercises
   <p align="center"><img src="https://github.com/user-attachments/assets/3757a189-9af9-4568-b620-5e149c74349c" width="1000"></p>
   <p align="center"><img src="https://github.com/user-attachments/assets/e5cdffd0-c4d9-46b4-9c9e-7032bb1699ac" width="1000"></p>
   <p align="center"><img src="https://github.com/user-attachments/assets/7061b3cf-888e-480a-8fa3-a1095da41b19" width="1000"></p>
   <p align="center"><img src="https://github.com/user-attachments/assets/13b3ef33-481b-46e0-9600-eef14de3acbd" width="1000"></p>
   <p align="center"><img src="https://github.com/user-attachments/assets/a4e763f7-6b24-4d40-8585-b35d486f4b3c" width="1000"></p>

## Headers and Status Code

1. **Headers and Status Codes**<br><br>
   So far, we have only sent a request message to a server and processed the response. But what if we want to give the server extra instructions? Or check that the server properly handled our request? That is where headers and status codes come in.

2. **Request and Response Message Anatomy**<br><br>
   Examining a GET request and response message, we see both messages are very similar in structure and can both be split into three distinct parts.<br><br>
   <p align="center"><img src="https://github.com/user-attachments/assets/5265fd61-44d2-48a0-b4dc-7d44f7810798" width="700"></p>

3. **The Start-Line**<br><br>
   First, we have the start-line. In request messages, this is referred to as the request-line. It contains the request type such as `GET` or `POST`, along with the path where the message should be delivered to. In response messages, the start line is called the status-line and contains a three-digit numerical status code and a status message.<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/62ecc5b2-9762-4253-adb4-2222651dc235" width="700"></p>

4. **Status Codes**<br><br>
   There are over 70 status codes in total, grouped into five categories as shown here. The most important ones to remember are '200 OK', which indicates the server has correctly processed the request, '404 Not Found', to indicate that the resource we are requesting doesn't exist, and '500 Internal Server Error', which means an error occurred on the server.<br><br>
   1. For a full list of all response codes you can refer to the MDN page on status codes via [MDN Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/8d4c8011-1f18-4758-b478-39d4c1ecaa68" width="700"></p>

5. **Headers**<br><br>
   Headers contain information that describes the message or data being sent or received, such as the type of content we are sending or the date the requested resource was last modified. Headers are always formatted as key-value pairs separated by a colon. Each header starts with a case-insensitive key, followed by a colon, and then the value of that header.<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/4f60726c-8307-4499-b479-47fbcbc45ddf" width="700"></p>

6. **Example: Content Negotiation with Headers**<br><br>
   In order to effectively communicate, client and server use message headers to agree on the language they are using to exchange information. This is called content negotiation. Here for example, the client sends the `accept` header to inform the server it can accept a response in JSON format. When the server responds, it includes the content-type header to let the client know what format it responded with.<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/ddd084d4-d12b-46f8-ad54-f4f8eba90383" width="700"></p>

7. **Headers with Requests**<br><br>
   The Python requests package allows us to add and read headers. Each request method like `requests.get` or `requests.post` accepts an additional `headers` parameter with key-value pairs in the form of a dictionary. Using this parameter, we can add as many headers as we want to our request. The response object has a `headers` attribute, which is a dictionary containing one key-value pair for every header received back in the response. We can access individual response headers by subsetting the dictionary using square brackets, or by using the `.get()` method on the dictionary.<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/228b0864-b51c-4a0e-abcd-54df9d96fc65" width="700"></p>

8. **Status Codes with Requests**<br><br>
   Similar to working with headers, the requests package also simplifies how we get the status code from a response. Each response object has a `status_code` attribute which contains the numeric value of the status code. Remembering all the numeric values of the status codes by heart isn't easy, however, that's why requests come with an easy lookup object built-in. By chaining the status message to the `requests.codes` lookup object we can easily find any status code, without the need to know the code. Like here where we use the lookup object to find the status code for Not Found.<br><br>
   <p  align="center"><img src="https://github.com/user-attachments/assets/53911fce-4db6-49ad-902b-bf2767bde946" width="700"></p>


### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/5e4a99e0-ee7f-4490-9801-4e2a2059baf8" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/6ddfbbcf-5135-4abe-beba-9b91da823148" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/28c856be-ffa5-4680-a532-402eb20c2a4f" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/ed5ead2d-85c8-4526-b173-d356a4f11dc9" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/b538f2e8-bc83-4915-a2b0-922109817e9e" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/68cd14c7-df3c-42e4-a185-379ce65d7eec" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/a92a5f54-743b-462e-958a-fdc5f4124e7d" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/de57fc0b-6a1f-4d96-a03c-995a49092169" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/c16a8649-9c71-47e7-bfdb-7ca17f70fa4b" width="1000"></p>

<!--
![image](https://github.com/user-attachments/assets/5e4a99e0-ee7f-4490-9801-4e2a2059baf8)
![image](https://github.com/user-attachments/assets/6ddfbbcf-5135-4abe-beba-9b91da823148)
![image](https://github.com/user-attachments/assets/28c856be-ffa5-4680-a532-402eb20c2a4f)
![image](https://github.com/user-attachments/assets/ed5ead2d-85c8-4526-b173-d356a4f11dc9)
![image](https://github.com/user-attachments/assets/b538f2e8-bc83-4915-a2b0-922109817e9e)
![image](https://github.com/user-attachments/assets/68cd14c7-df3c-42e4-a185-379ce65d7eec)
![image](https://github.com/user-attachments/assets/a92a5f54-743b-462e-958a-fdc5f4124e7d)
![image](https://github.com/user-attachments/assets/de57fc0b-6a1f-4d96-a03c-995a49092169)
![image](https://github.com/user-attachments/assets/c16a8649-9c71-47e7-bfdb-7ca17f70fa4b)
-->


# Chapter 2: More API Request Concepts

## API Authentication

1. **API Authentication**<br><br>
APIs we interact with frequently contain private, personal, or sensitive data. To protect this sensitive information, APIs require clients to authenticate before granting access. Let's explore how authentication works.<br><br>

2. **Accessing sensitive data**<br><br>
The album API, which contains our private album collection, requires authentication to verify the request's origin. Attempting to access this protected API without proper identification will result in a 401 error indicating that we need authorization to access this API resource.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/11b68497-0041-406f-9349-35b55c99b934" width="700"></p>


3. **Accessing sensitive data**<br><br>
When we add information to the request to identify ourselves, the server knows it's us and responds as expected, with a 200 OK status code. We have multiple options to add this information to an API request, let's learn the most common ones!<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/743d5591-fc21-4563-9cc8-0b5a2644db78" width="700"></p>

4. **Authentication methods**<br><br>
Basic Authentication is the simplest form of API authentication. It uses a username and password for authentication. This method is easy to integrate but also the least secure, as it sends your password unencrypted over the internet to the server. API Key or Token Authentication works by attaching a unique authentication key or token to each request. API keys are simple to implement but pose a security risk if compromised, as they also transmit unencrypted data. JWT or JSON Web Token Authentication is similar to API key authentication, but the main difference is that a JWT token has a limited lifespan and can contain additional encrypted data, such as user information. OAuth 2.0 is a comprehensive authentication framework that allows fine-grained access to resources without sharing any credentials. Which authentication mechanism and credentials you have to use depends on the API server, the documentation of the API you're using usually contains information on how to authenticate. Now, let’s learn how to use Basic and API Key Authentication with the requests package.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/91cb0a7c-85fb-48c4-9fe5-0caa11836175" width="700"></p>

5. **Basic authentication**<br><br>
To use basic authentication we need to add an authorization header to the request we are sending to the API. This header must contain a base64-encoded combination of our username and password. Base64 encoding is a two-way algorithm that anyone can easily decode, so unfortunately it provides no additional security. Implementing basic authentication using the requests package is easy. Instead of adding a header and doing the base64 encoding yourself, you can just pass a tuple containing your username and password using the auth function argument, requests takes care of all the encoding and adds the header.

<p align="center"><img src="https://github.com/user-attachments/assets/a90dc262-26c2-4b08-b5ac-b7d22a6f0966" width="700"></p>

6. **API key/token authentication**<br><br>
There are two common options to add the authentication token to our request. The first option is simply adding the API key to the URL as a query parameter. In this example, we add the access_token query parameter to the URL using the params function argument. The second option is by adding an authorization header. This is usually the preferred method. For this the requests packages doesn't offer an out of the box method like for Basic Authentication, so we need to add the header ourself using the headers function argument.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/15aedc66-56bd-46f0-a8e6-e9c1a014ff3d" width="700"></p>


### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/b7c0add3-ab08-4c8b-92a9-912f8f586a43" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/29d2f916-5483-487c-90f4-10bc71a868f6" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/65e01a62-e36c-4fd2-b9d3-ebae0f471e03" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/4ee65aaa-5aca-4f83-be1b-24402ef11f8d" width="1000"></p>


## Working with Structured Data

1. **Working with structured data**<br><br>
So far, we have only used simple requests, such as getting song lyrics represented as a string of text. In reality, we often need to exchange more complex data structures. Let's learn how to handle these kinds of API requests.<br><br>

2. **Complex data structures**<br><br>
The lyric API returns the entire lyric as plain, unstructured text. Complex data types, like music albums, require more structure to transmit effectively. That's because albums have multiple properties, such as an ID, title, artist, or list of tracks.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/eaa11dab-9ef2-465c-ace1-61585df9a111" width="700"></p>


3. **Complex data structures: JSON**<br><br>
Luckily, we have a few handy data formats to make working with structured data easier. In this examples we are using JSON, which stands for Javascript Object notation. It is the most common and a very lightweight format used by web APIs. JSON is natively supported by many programming languages and easily readable by both humans and machines. JSON is one of the many types we call content-types, mime-types, or media-types. These terms are used interchangably, but in this course we will use the term "content type". Other formats we might encounter are XML, CSV, and YAML.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/bdba924d-c4b4-4dae-95f0-27319c47091d" width="700"></p>


4. **From Python to JSON and back**<br><br>
In order to use a Python object with a Web API, we first need to convert it to a JSON string so we can safely transmit it with the request or response. Transforming a Python object to JSON is called encoding. Decoding is the reverse, turning a JSON string back into a Python object. In Python, the built-in `json` package can encode and decode JSON. `json.dumps()` turns a Python object into a JSON string, while `json.loads()` converts a JSON string back into a Python object.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/db19219c-6ea5-4a81-b17d-617701048733" width="700"></p>


5. **Requesting JSON data**<br><br>
Let's see how the requests Python package can help us work with APIs using JSON as data format. Using the get function, we request a lyric from the API. Without adding additional headers, the server will respond in plain text. When we add an accept header with the value `application/json`, the server will respond with JSON text. We can inspect the JSON text by just printing the response.text. Using the json() function on the response object, we can now decode the JSON text into a Python object and easily print the artist attribute.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/75f40311-c813-414b-895c-71a271ad34d7" width="700"></p>


6. **Sending JSON data**<br><br>
We've now learned how to receive JSON data, but what about sending JSON data? The requests package can also help here. When using the `json` function argument to send the playlist object, requests will automatically add the necessary content-type headers and do all of the encoding for us. Let's inspect the request object after sending the playlist object to the playlists API. Notice that the content-type header is set to `application/json` automatically. We didn't need to add any headers or encode objects to JSON strings.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/671592ba-fc24-4f09-9ec2-037e112b1046" width="700"></p>


### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/673f649b-22cf-4fa9-b45e-b9a8872d8e9b" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/bc652135-0b8a-4cf6-a227-6020882b3662" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/763ef84f-2626-47b3-808e-c3125bc70d7f" width="1000"></p>



## Error Handling

1. **Error handling**<br><br>
When integrating with a web API, it's important to consider what might go wrong. After all, we're communicating with a web API over the internet, so things can go wrong. This video will explore how to gracefully handle errors and prevent common issues. Let's dive in!<br><br>

2. **Error status codes**<br><br>
To determine if an error occurred or if the request was successful, REST APIs utilize the `status_code` in the response. A status code in the 4XX or 5XX range indicates an issue. Errors in the 400 range are client errors, indicating the request from the client could not be handled properly. These are usually caused by sending a wrong header or failing to authenticate. Typically, clients can handle or manage these errors easily by fixing the request. Errors in the 500 range indicate server problems. These errors are beyond the client's control, as the server acknowledged the request but faced difficulties handling it due to server-side issues. These are typically caused by server overload, or configuration errors. Clients cannot resolve these errors but should address them in the code to prevent unexpected behavior or bugs.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/aa09b2ae-7148-4685-9170-dd65df97e03e" width="700"></p>


3. **Error status codes: examples**<br><br>
Some common error codes in the 400 range are 401, which means we're trying to access a protected resource and need to add authentication to our request. 404 means the resource we are trying to access does not exist on the server so we are doing something wrong. 429 will be returned when we are sending more requests to the server than it's able to handle, in this case we need to implement a rate limiter to spread out our requests over a larger period of time. Common 500 error codes are 500 Internal Server Error, which is a common catch-all error code that indicates something on the server went wrong. 502 and 504 are also errors we might encounter and are related to the server infrastructure.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/710b29b2-1c44-4a2a-abcf-fe248e1baa43" width="700"></p>


4. **Handling errors**<br><br>
The simplest way to handle API errors is by checking the response status code for any codes in the 400 and 500 ranges, which indicate an error has occurred. We can then use this status code to decide how to handle the error. However, this approach is overly simplified. An error might occur even before the request reaches the server, in which case we would not receive a response containing an error code. Fortunately, the requests library raises a ConnectionError in this case, which we can check for using a try/except block. To properly check for any errors with the API request, we should combine both approaches. The requests library makes this process straightforward.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/d3381e3b-96a8-417d-ba5b-9ef3977265e1" width="700"></p>


5. **raise_for_status()**<br><br>
The requests library has a convenient feature that automatically raises errors for any responses containing an error status code. By enabling this mode using the `raise_for_status()` function immediately after sending the request, any error code returned from the API will raise an `HTTPError`. This way, after checking for Connection errors, we can easily also check for any HTTPErrors that might have occurred.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/7e68eb55-cde5-4ad9-87d0-bfb802507a41" width="700"></p>


### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/a1683e70-97b3-42f5-9221-1af6e7df337a" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/ceff49c6-e543-42d6-96b7-6d92a5fd4be0" width="1000"></p>

[Set of included Exceptions](https://requests.readthedocs.io/en/latest/user/quickstart/#errors-and-exceptions)

<p align="center"><img src="https://github.com/user-attachments/assets/a16383f9-e9be-4586-ba13-cdaed27b6257" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/0e43632b-6140-4dc9-9e7f-879b97ac1f8f" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/0eccc3c4-c57a-4795-8bf5-fe5b64111af2" width="1000"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/f882a189-f1ff-47be-99cb-d57c66dfc0e5" width="1000"></p>




## Final Thoughts

1. **API basics**<br><br>
In this course we learned all about the role APIs play in modern application development as well as how they enable data sharing over a network or the internet. We learned about the three most common types of Web APIs and explored REST APIs in depth. We explored how we can create and structure a URL with path and query parameters to allow us to use APIs more effectively. Then we looked under the hood of the request and response messages a client and a server exchange to communicate. Lastly, we learned about the different types of HTTP verbs we have available in order to read, create, update, and delete resources using an API.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/d4aa2ec1-7285-4f22-8ef2-b6710303bc1c" width="700"></p>


2. **APIs with Python**<br><br>
We explored how we can make integrating with APIs easier using the open-source requests package. We learned how to perform GET, POST, PUT, and DELETE requests and how we can pass a Python dictionary with query parameters using the params argument of any HTTP methods to add query parameters to the URL. Later, we looked at what role headers play in request and response messages and how we can use them to do "content negotiation", allowing us to request content from an API in a different format like JSON or XML. Status codes are a crucial part of API response messages as they inform us how the server responded to our API request, if an error occured or if everything went fine. We learned how we can retrieve the status code from the API response object.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/2a35d0db-67ff-46ff-b740-d78646451c2a" width="700"></p>


3. **Advanced topics**<br><br>
Diving deeper, we learned how to authenticate with APIs that contain private, sensitive, or personal data. We also learned the two most common authentication mechanisms: Basic Authentication and API key or token-based authentication. Using headers, we saw how to use both mechanisms using the requests package. We also learned how to send and retrieve data in a more structured format like JSON. This is especially important when working with complex data types, which is often the case. Using the "accept" header, we could retrieve data in a specific format, and using the json function argument, we were also able to send data to the server in the JSON format.<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/3bc3a360-5785-4431-8db4-82acdef44f53" width="700"></p>


4. **Error handling**<br><br>
At the very end, we learned how to properly handle situations where things don't go as expected. We learned of the three different types of errors, Connection errors that occur before reaching the server, 400 errors which are client errors and 500 errors which indicate something has gone wrong on the server. We explored 2 ways to handle these errors: first, looking at the response status code, and second, using the more robust "raise_for_error" function, which causes the requests package to raise an exception when something goes wrong.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/cf894d81-2dad-4efe-bcde-683921e8112a" width="700"></p>

