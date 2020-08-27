# SpringCloud-BootStrap
5 microservice applications are built. There is a main config file, discovery server(eureka discovery), gateway(act as a reverse proxy shuttling requests from clients to our back end servers, it also allows all responses to originate from a single host), a book-service application and rating service application.

CONFIG SERVER

The config folder is a single application that manages a configuration for all our applications.
The most significant setting for the config server is the git.uri parameter. This is currently set to a relative file path. This property points to a Git repository where the property files for all the other applications are stored. It can also be set to an absolute file path if necessary.
Initialize a Git repository where we can store files and track their changes.

BOOTSTRAP SERVER
In the subsequent servers, we're going to want their application properties managed by this config server.
Each one of these apps is going to have a file called bootstrap.properties.
A parent Spring ApplicationContext loads the bootstrap.properties first. This is critical so that Config Server can start managing the properties in application.properties.

DISCOVERY SERVER
In this app we will setup the eureka discovery server.
When a new server is provisioned it will communicate with the discovery server and register its address so that others can communicate with it. This way other applications can consume this information as they make requests.

GATEWAY
A gateway server is an excellent application in microservice architecture as it allows all responses to originate from a single host. This will eliminate the need for CORS and give us a convenient place to handle common problems like authentication.

BOOK-SERVICE 
A small application that is built for testing purpose.

RATING-SERVICE
Another small application that is built for testing purpose.

The config server should be started first, then the discovery server. 
Once the discovery server is up, the connection is established between the config and discovery and any applications can be registered.
The gateway server should be run next to allow all responses to originate from a single source.
Then the book-service application should be started, and look for this url. 
http://localhost:8080/book-service/books
Then the rating service should be started, and the url.
http://localhost:8080/rating-service/ratings/all

