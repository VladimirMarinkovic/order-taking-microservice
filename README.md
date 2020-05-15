# order-taking-microservice

This application is built on the principle of microservice architecture.

* **product-catalog-microservice**  - store and controls public information about the products and packages that are available in the company's offerings.

* **customer-details-microservice** - store and controls the information of customers

* **order-taiking-microservice** - controls the processing and modification of orders. Consumes the other two microservices.  He also have responsible for authentication and authorization.
This microservice accepts the order based on the order  request, which consists of a list of selected products(just names of products) and their individually selected package(name of package).
Based on such a request, it finds selected products, their packages and attributes. Using product-catalog-microservice it maps such products (with all details of packages and their atributes) into an order which it then serializes and publish as a message in RabitMq. 
Such an order is then mapped to the Entity object of the processed order and stored in a MySql database.
An order can be made for an existing customer or for a new customer.
If the order is executed for an already existing customer, 
it is only necessary to provide thi his contract number and the data about him will be automatically withdrawn from the database.
This service has the possibility of registering a new user.
Authentication and Authorisation is realized via JWT tokens. 
  * Login credentials  - ( data filled in when starting the application)   userName: admin  password: 1234



* **config-server**   - service uses Spring Cloud Config Server for running configuration server in the native mode. The configuration files are placed on the classpath/shared.

* **eureka-server**   - servce uses Spring Cloud Netflix Eureka as an embedded discovery server.

* **gateway-service** - service uses Spring Cloud Netflix Zuul for running Spring Boot application that acts as a proxy/gateway.


* **Swager Documentation available on Gateway**
http://localhost:8080/swagger-ui.html

* **For testing purposes** - some data was populated using a command line runner. Product-catalog-microservice and Customer-details-microservice  use H2 in memory database, while for order-taiking-microservice it is necessary to have MySql running. 

* **Kubernetes – deployment** - will be ready in the next few days.



