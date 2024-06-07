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

