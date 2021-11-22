![cover](https://img9.doubanio.com/view/subject/s/public/s29918092.jpg)

    作者: Chris Richardson
    出版社: Manning
    副标题: With examples in Java
    出版年: 2017-9
    页数: 375
    定价: GBP 38.44
    装帧: Paperback
    ISBN: 9781617294549

- [豆瓣](https://book.douban.com/subject/26989027/)
- [oreilly](https://learning.oreilly.com/library/view/microservices-patterns/9781617294549/)

---

- [1.Escaping monolithic hell](#1escaping-monolithic-hell)
  - [1.1.The slow march toward monolithic hell](#11the-slow-march-toward-monolithic-hell)
    - [1.1.1.The architecture of the FTGO application](#111the-architecture-of-the-ftgo-application)
    - [1.1.2.The benefits of the monolithic architecture](#112the-benefits-of-the-monolithic-architecture)
    - [1.1.3.Living in monolithic hell](#113living-in-monolithic-hell)
  - [1.2.Why this book is relevant to you](#12why-this-book-is-relevant-to-you)

# 1.Escaping monolithic hell
## 1.1.The slow march toward monolithic hell
### 1.1.1.The architecture of the FTGO application
FTGO is a typical enterprise Java application. Figure 1.1 shows its architecture.

![](https://learning.oreilly.com/library/view/microservices-patterns/9781617294549/01fig01_alt.jpg)

Figure 1.1. The FTGO application has a hexagonal architecture. It consists of business logic surrounded by adapters that implement UIs and interface with external systems, such as mobile applications and cloud services for payments, messaging, and email.

The business logic consists of modules, each of which is a collection of `domain objects`. Examples of the modules include Order Management, Delivery Management, Billing, and Payments. There are several adapters that interface with the external systems. Some are `inbound` adapters, which handle requests by invoking the business logic, including the REST API and Web UI adapters. Others are `outbound` adapters, which enable the business logic to access the MySQL database and invoke cloud services such as Twilio and Stripe.

The application is an example of the widely used `monolithic` style of software architecture, which structures a system as a single executable or deployable component.

### 1.1.2.The benefits of the monolithic architecture

- Simple to develop— IDEs and other developer tools are focused on building a single application.
- Easy to make radical changes to the application— You can change the code and the database schema, build, and deploy.
- Straightforward to test— The developers wrote end-to-end tests that launched the application, invoked the REST API, and tested the UI with Selenium.
- Straightforward to deploy— All a developer had to do was copy the WAR file to a server that had Tomcat installed.
- Easy to scale— FTGO ran multiple instances of the application behind a load balancer.

### 1.1.3.Living in monolithic hell
As figure 1.2 shows, the once small, simple FTGO application has grown over the years into a monstrous monolith. Similarly, the small development team has now become multiple Scrum teams, each of which works on a particular functional area.

![](https://learning.oreilly.com/library/view/microservices-patterns/9781617294549/01fig02_alt.jpg)

Figure 1.2. A case of monolithic hell. The large FTGO developer team commits their changes to a single source code repository. The path from code commit to production is long and arduous and involves manual testing. The FTGO application is large, complex, unreliable, and difficult to maintain.

- Complexity intimidates developers
- Development is slow
- Path from commit to deployment is long and arduous
  - One problem with so many developers committing to the same code base is that the build is frequently in an unreleasable state.
  - Another reason it takes so long to get changes into production is that testing takes a long time.
- Scaling is difficult
  - The restaurant data, for example, is stored in a large, in-memory database, which is ideally deployed on servers with lots of memory. In contrast, the image processing module is CPU intensive and best deployed on servers with lots of CPU. Because these modules are part of the same application, FTGO must compromise on the server configuration.
- Delivering a reliable monolith is challenging
  - This lack of testability means bugs make their way into production. To make matters worse, the application lacks `fault isolation`, because all modules are running within the same process.
- Locked into increasingly obsolete technology stack

## 1.2.Why this book is relevant to you


























































