# SpringRestNotes
### Chapter 1: Introduction To Rest
##### What Is Rest?
- REST stands for *RE*presentational *S*tate *T*ransfer.
- Architectural stle for designing distributed network applications.
###### Six Constraints or Principles for REST:
![Screen Shot 2024-06-06 at 2 33 29 PM](https://github.com/gmojados/SpringRestNotes/assets/162353468/bad2e170-f8c8-4590-8a27-abcda770e51b)

![Screen Shot 2024-06-06 at 2 34 51 PM](https://github.com/gmojados/SpringRestNotes/assets/162353468/4c1ee762-ca69-41b5-b179-ef760b88e91c)
- Adherence to these guidelines and best practices would make an application scalable, visible, portable, reliable, and able to perform better.
- Uniform Interface in a REST application is achieved through abstractions such as resources, representations, URIs, and HTTP methods

##### Understanding Resources
- A resource is anything that can be accessed or manipulated
###### Examples of Resources:
- Videos
- Blog entries
- User profiles
- images
- persons/devices

###### Identifying Resources
- Web provides  the Uniform Resource Identifier, or URI for uniqley indentifying resources
**- The syntax is: scheme:scheme-specific-part**
- The scheme and the scheme-specific-part are separated using a semicolon.
- Examples of a scheme include http or ftp or mailto and are used to define the semantics and interpretation of the rest of the URI.
- Take the example of the URI—http://www.apress.com/9781484208427. The http portion of the example is the scheme;

![Screen Shot 2024-06-07 at 9 13 38 AM](https://github.com/gmojados/SpringRestNotes/assets/162353468/e099c5b3-b86d-4d9c-b187-3a9a527fde01)



- it is possible for a resource to have more than one URI. For example, Facebook can be accessed using URIs https://www.facebook.com and https://www.fb.com.
-The term URI aliases is used to refer to such URIs that identify the same resources. URI aliases provide flexibility and added convenience such as having to type fewer characters to get to the resource.

###### URI Templates
- For example, in a blog application, the URI http://blog.example. com/2014/posts would retrieve all the blog posts created in the year 2014. Similarly, the URIs http://blog. example.com/2013/posts, http://blog.example.com/2012/posts, and so forth would return blog posts corresponding to the years 2013, 2012, and so on. In this scenario, it would be convenient for a consuming client to know the URI structure http://blog.example.com/year/posts that describes the range of URIs rather than individual URIs.
- The standardized URI Template for that scenario : 
http://blog.example.com/{year}/posts

##### Representation
- RESTful resources are abstract entities.
- Data and metadata that make a RESTful resouce needs to be serialized into a representation before it gets sent to a client.
- Can be viewed as a snapshot of a resource's state at a given point in time.
- **EXAMPLE**
- When an online shopper uses their browser to buy a product and requests its details, the application would provide the product details as a Web page in HTML. Now, when a developer writing a native mobile application requests product details, the ecommerce application might return those details in XML or JSON format. In both scenarios, the clients didn’t interact with the actual resource—the database record-holding product details. Instead, they dealt with its representation.
- ![Screen Shot 2024-06-07 at 9 37 53 AM](https://github.com/gmojados/SpringRestNotes/assets/162353468/5cc86014-ab75-4859-8011-1b678a4315b8)

##### Safety
- Safe methods are used to retrieve resources. However, safety doesn’t mean that the method must return the same value every time. For example, a GET request to retrieve Google stock might result in a different value for each call. But as long as it didn’t alter any state, it is still considered safe.

##### Idempotency
- An operation is considered to be idempotent if it produces the same server state whether we apply it once or any number of times
-  HTTP methods such as GET, HEAD (which are also safe), PUT, and DELETE are considered to be idempotent, guaranteeing that clients can repeat a request and expect the same effect as making the request once

##### Get
- The GET method is used to retrieve a resource’s representation.
- -GET requests don’t modify server state, they are considered to be safe and idempotent.
- A hypothetical GET request to http://blog.example.com/posts/1 and the corresponding response are shown here:
_GET /posts/1 HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.5
Connection: keep-alive
Host: blog.example.com_

- The simplicity of the GET method is often abused and it is used to perform operations such as deleting or updating a resource’s representation. Such usage violates standard HTTP semantics and is highly discouraged.

##### HEAD
- The HEAD method allows a client to only retrieve the metadata associated with a resource. No resource representation gets sent to the client.
- Like GET, the HEAD method is also safe and idempotent and responses can be cached on the client.

##### Delete
- The DELETE method, as the name suggests, requests a resource to be deleted.
- On receiving the request, a server deletes the resource. For resources that might take a long time to delete, the server typically sends a confirmation that it has received the request and will work on it.
- Depending on the service implementation, the resource may or may not be physically deleted.


##### Put
- The PUT method allows a client to modify a resource state.
- A client modifies the state of a resource and sends the updated representation to the server using a PUT method. On receiving the request, the server replaces the resource’s state with the new state.
- Clients can also use PUT method to create a new resource. However, it will only be possible when the client knows the URI of the new resource.

##### POST
- The POST method is used to create resources.
-  Typically, it is used to create resources under subcollections— resource collections that exist under a parent resource.
-  For example, the POST method can be used to create a new blog entry in a blogging application
-  Unlike PUT, a POST request doesn’t need to know the URI of the resource. The server is responsible for assigning an ID to the resource and deciding the URI where the resource is going to reside.
- The POST method is very flexible and is often used when no other HTTP method seems appropriate.

##### Patch
- The PATCH method proposed as part of RFC 5789 (http://tools.ietf.org/html/ rfc5789) is used to perform partial resource updates.
-  It is neither safe nor idempotent.

##### CRUD AND HTTP VERBS
![Screen Shot 2024-06-07 at 9 13 38 AM](https://github.com/gmojados/SpringRestNotes/assets/162353468/952068d6-890a-4411-b2d6-e13e85b64804)

###### HTTP Status Code Groups/ Categories:
- Informational Codes—Status codes indicating that the server has received the request but hasn’t completed processing it. These intermediate response codes are in the 100 series.-
-  Success Codes—Status codes indicating that the request has been successfully received and processed. These codes are in the 200 series.
- direction Codes—Status codes indicating that the request has been processed, but the client must perform an additional action to complete the request. These actions typically involve redirecting to a different location to get the resource. These codes are in the 300 series.
- Client Error Codes—Status codes indicating that there was an error or a problem with client’s request. These codes are in the 400 series.
- Server Error Codes—Status codes indicating that there was an error on the server while processing the client’s request. These codes are in the 500 series.
![Screen Shot 2024-06-07 at 11 40 15 AM](https://github.com/gmojados/SpringRestNotes/assets/162353468/f32847ba-57cb-4ac1-8c85-0c4a136f0603)

##### Steps to building RESTFUL API:
1.) Identify Resources—Central to REST are resources. We start modeling different resources that are of interest to our consumers. Often, these resources can be the application’s domain or entities. However, a one-to-one mapping is not always required.
2.) Identify Endpoints—The next step is to design URIs that map resources to endpoints. In Chapter 4, we will look at best practices for designing and naming endpoints.
3.) Identify Actions—Identify the HTTP methods that can be used to perform operations on the resources.
4.) Identify Responses—Identify the supported resource representation for the request and response along with the right status codes to be returned.

### Chaper 2: SPRING WEB MVC PRIMER
##### Dependency Injection
- Constructor Injection

- Dependencies are provided through a class constructor.
Setter Injection

- Dependencies are provided through setter methods.
Field Injection

- Dependencies are provided directly to fields (less recommended due to testing difficulties).

_Configuring Dependency Injection in Spring_
XML Configuration
Define beans and their dependencies in an XML file.
