# order-taking-microservice

This application is built on the principle of microservice architecture.

* **product-catalog-microservice **  - store and controls public information about the products and packages that are available in the company's offerings.

* **customer-details-microservice ** - store and controls the information of customers

* **order-taiking-microservice  ** - controls the processing and modification of orders. Consumes the other two microservices.  He also have responsible for authentication and authorization.
This microservice accepts the order based on the order fulfillment request, which consists of a list of selected products and their individually selected package.
Based on such a request, it finds selected products, their packages and attributes. Using product-catalog-microservice it maps such products into an order which it then serializes and processes in RabitMq. 
Such an order is then mapped to the Entity object of the processed order and stored in a MySql database.
An order can be made for an existing user or for a new user.
If the order is executed for an already existing customer, 
it is only necessary to provide thi his contract number and the data will be automatically withdrawn from the database.


* **config-server**   - service uses Spring Cloud Config Server for running configuration server in the native mode. The configuration files are placed on the classpath/shared.

* **eureka-server**   - servce uses Spring Cloud Netflix Eureka as an embedded discovery server.

* **gateway-service** - service uses Spring Cloud Netflix Zuul for running Spring Boot application that acts as a proxy/gateway.It uses Ribbon as Load Balancer.


* **Swager Documentation avaible on Gateway**
http://localhost:8080/swagger-ui.html

* **For testing purposes** - some data was populated using a command line runner. Product-catalog-microservice and Customer-details-microservice  use H2 in memory database, while for order-taiking-microservice it is necessary to have MySql running. 

* **Kubernetes – deployment** - will be ready in the next few days.



