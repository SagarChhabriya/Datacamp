![image](https://github.com/user-attachments/assets/206cd019-4e14-4ff9-bffb-d6a103040151)# Table of Contents

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

1. **What is an API?**<br><br>
The abbreviation stands for Application Programming Interface. An API defines a set of rules and abilities for two systems to communicate with each other. Through an API, systems can interact with eachother to exchange or manipulate data. As users, we are rarely directly exposed to APIs; we use a User Interface or UI to interact with software applications. But at a basic level, all computer systems are built with APIs, and we use them all the time without knowing. For example, clicking the "send" button will make our email application use an API to tell the email server to send an email to the recipient.
<br><br>
<p><img src="https://github.com/user-attachments/assets/82c3b609-60f5-412e-8270-393843a752a0" width="700"></p>

2. Web APIs, clients and servers
APIs come in many different styles and flavors, but for the purpose of this course, we will be focusing on Web APIs. Web APIs are used to enable communication between two software applications over a network or the internet. This communication uses the HTTP protocol, the same protocol our browser uses to retrieve webpages from the internet. In practice, this means a client sends a message over the internet to a server; the server, in turn, responds by sending a message back to the client.
<br><br>
![image](https://github.com/user-attachments/assets/98ca49ea-6f2f-4e37-a581-7087e40d8c0e)

3. Types of Web APIs
Let's discuss the three most common types of Web APIs. SOAP, takes a very formal approach and is most often used in enterprise applications where robustness and strict protocols are required. REST, the most popular and most common type, is known for its simplicity, scalability, and ease of integration. GraphQL takes a more sophisticated approach, focusing on precise and flexible data retrieval, minimizing data transfer, and optimizing for performance. In this course, we will work with REST APIs, as it is the most common.
![image](https://github.com/user-attachments/assets/da1f8c33-195b-4ce5-80f4-3f2bc33a8382)

4. Working with APIs in Python
Let's discuss two well-known Python libraries for integrating Web APIs, urllib and requests. Urllib comes bundled with Python and is a very powerful module, but that goes at the cost of simplicity. Here we are making a request to the music catalog Web API to get a list of music albums. To print the data we requested, we first need to use the urlopen function to send a request, then use the "read()" function on the response object to get the response data. After that, we call the "decode()" function on the response data to extract the raw data, and then we can finally print the data we received from the API. Luckily, the requests package simplifies things a lot. Requests offers many built-in features which urllib needs additional steps or packages for. In this example, we achieve the same result with a lot less code using the `requests.get()` function. Requests takes care of reading and decoding the response; all we need to do is print the text attribute of the response object.
![image](https://github.com/user-attachments/assets/cd14305f-8ba1-498e-b2cc-d9b1be039298)

### Exercises
![image](https://github.com/user-attachments/assets/d1ed1ba7-806a-40cd-a237-c0a2757f30f4)
![image](https://github.com/user-attachments/assets/1c3d5932-1586-493c-a7a9-9ed8ca693774)


## The Basic Anatomy of an API Request
Explanation of the key components of an API request, including the endpoint, method, and parameters.
1. The basic anatomy of an API request
Fetching data from an API is straightforward; now, let's learn how we can use the requests package to give more detailed instructions to an API.

2. What are URLs?
URLs are a fundamental concept in Web APIs. A URL is a structured address pointing to a specific resource. Via a URL, we can specify what resource we want to interact with. For this example we'll compare a REST API to an office building; each office unit is a unique resource. The URL is the address of a single unit in the building. It contains all the information needed to navigate to that specific unit.
![image](https://github.com/user-attachments/assets/9d945819-a60b-4451-8f11-54afbdf2f617)

3. Dissecting the URL
Let's break URLs down into its five main components. First is the protocol. This determines the transportation to use when navigating to the destination, walking or driving, for example. The second component is the domain, it is like the street address of the office building. It uniquely identifies the location of the API server on the internet. Third is the port, the gateway or entrance into the office building. When traveling by car, we enter through the garage. Common default ports are 80 and 443. The path component determines the specific office unit in the building. With APIs, each resource has a unique location on the server, defined by its path. The last component is the query, which contains additional instructions. It specifies instructions like "take the elevator" for example. By constructing a URL with a path and parameters, we can control where to send our API requests to.
![image](https://github.com/user-attachments/assets/90c0380f-e907-40a1-adec-e5c74c43894e)

4. Adding query parameters with requests
Adding a query parameter using the requests package is very easy. We might want to just append the query parameter to the URL string, which works fine, but there is a better way. Each HTTP method from the requests package, such as get, accepts an additional argument called `params` which accepts a dictionary with key/value pairs, one for each query parameter. See how much easier that code is?
![image](https://github.com/user-attachments/assets/2394bc3d-da65-45d2-815c-21b3baad27a1)


5. HTTP Verbs
Let's send a package to the DataCamp office! Using the URL, we have constructed the destination of our package: the mailbox of unit 243 in the Empire State building. But how do we now define what to do with the package when we arrive at our destination? This is where HTTP verbs come in. Every request uses one of 9 HTTP verbs, let's learn the four most important ones. GET is used to read a resource. It's like checking the contents of the mailbox without taking anything out. POST is creating a resource, like dropping a new package in the mailbox. PUT updates a resource, like replacing a package that was already in the mailbox. And DELETE removes all packages from the mailbox, leaving it empty.
![image](https://github.com/user-attachments/assets/43b58fe6-9b9a-4f85-9482-dd98b3a5e092)

6. Sending data via POST and PUT
With the requests package, we have easy access to all HTTP verbs as functions; we already saw the `requests.get()` function. For POST and PUT requests, we need to add data to create or update our resources. Similar to how we can pass a `params` argument to set query parameters, we can also pass a `data` argument to specify the data we want to send along with the request. Making a DELETE request is even simpler. Just use the delete instead of the get function.
![image](https://github.com/user-attachments/assets/b453cd21-71cc-41ef-9617-0b1bff47c94b)

### Exercises
![image](https://github.com/user-attachments/assets/3757a189-9af9-4568-b620-5e149c74349c)
![image](https://github.com/user-attachments/assets/e5cdffd0-c4d9-46b4-9c9e-7032bb1699ac)
![image](https://github.com/user-attachments/assets/7061b3cf-888e-480a-8fa3-a1095da41b19)
![image](https://github.com/user-attachments/assets/13b3ef33-481b-46e0-9600-eef14de3acbd)
![image](https://github.com/user-attachments/assets/a4e763f7-6b24-4d40-8585-b35d486f4b3c)



## Headers and Status Code
Details on the role of headers in API requests and responses, and how to interpret status codes to understand the result of an API call.
1. Headers and status codes
So far, we have only sent a request message to a server and processed the response. But what if we want to give the server extra instructions? Or check that the server properly handled our request? That is where headers and status-codes come in.

2. Request and response message anatomy
Examining a GET request and response message, we see both messages are very similar in structure and can both be split into three distinct parts.
![image](https://github.com/user-attachments/assets/5265fd61-44d2-48a0-b4dc-7d44f7810798)

3. The start-line
First, we have the start-line. In request messages, this is referred to as the request-line. It contains the request type such as `GET` or `POST`, along with the path where the message should be delivered to. In response messages, the start line is called the status-line and contains a three-digit numerical status-code and a status message.
![image](https://github.com/user-attachments/assets/62ecc5b2-9762-4253-adb4-2222651dc235)

4. Status codes
There are over 70 status codes in total, grouped into five categories as shown here. The most important ones to remember are '200 OK', which indicates the server has correctly processed the request, '404 Not Found', to indicate that the resource we are requesting doesn't exist, and `500 Internal Server Error`, which means an error occurred on the server.

1 For a full list of all response codes you can refer to the MDN page on status-codes via https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

![image](https://github.com/user-attachments/assets/8d4c8011-1f18-4758-b478-39d4c1ecaa68)

5. Headers
Headers contain information that describe the message or data being sent or received, such as the type of content we are sending or the date the requested resource was last modified. Headers are always formatted as key-value pairs separated by a colon. Each header starts with a case-insensitive key, followed by a colon, and then the value of that header.

![image](https://github.com/user-attachments/assets/4f60726c-8307-4499-b479-47fbcbc45ddf)

6. Example: Content negotiation with headers
In order to effectively communicate, client and server use message headers to agree on the language they are using to exchange information. This is called content negotiation. Here for example, the client sends the `accept` header to inform the server it can accept a response in JSON format. When the server responds, it includes the content-type header to let the client know what format it responded with.

![image](https://github.com/user-attachments/assets/ddd084d4-d12b-46f8-ad54-f4f8eba90383)

7. Headers with requests
The Python requests package allows us to add and read headers. Each request method like requests.get or requests.post accepts an additional headers parameter with key-value pairs in the form of a dictionary. Using this parameter, we can add as many headers as we want to our request. The response object has a headers attribute, which is a dictionary containing one key-value pair for every header received back in the response. We can access individual response headers by subsetting the dictionary using square brackets, or by using the .get() method on the dictionary.

![image](https://github.com/user-attachments/assets/228b0864-b51c-4a0e-abcd-54df9d96fc65)

8. Status codes with requests
Similar to working with headers, the requests package also simplifies how we get the status-code from a response. Each response object has a status-code attribute which contains the numeric value of the status-code. Remembering all the numeric values of the status codes by heart isn't easy however, that's why requests comes with an easy lookup object built-in. By chaining the status-message to the requests.codes lookup object we can easily find any status code, without the need to know the code. Like here where we use the lookup object to find the status-code for Not Found.

![image](https://github.com/user-attachments/assets/53911fce-4db6-49ad-902b-bf2767bde946)



# Chapter 2: More API Request Concepts

## API Authentication
An introduction to different methods of authenticating API requests, including API keys and OAuth.

## Working with Structured Data
How to handle and parse structured data formats like JSON and XML received from APIs.

## Error Handling
Techniques for managing and responding to errors that occur during API requests, including retries and error messages.




