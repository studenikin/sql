## Explain solution:
Basically the solution provides developers with a set of models of the e-commerce domain along with persistence layer and the Web Api service on top of it.
The solution is grouped into several projects:
* Azamon.Api -  essentially a Web Api service that provides basic CRUD operations over the Basket model. It also allows logged users to get baskets belonging to them.
* Azamon.Core - defines models and business rules for the e-commerce domain.
* Azamon.Persistence.Sql  - provides persistence infrastructure for the Basket model. By implementing the IRepository interface it stores Basket data in relational database (EF is used).
* Azamon.Tests - unit tests for models and controllers.

## What could be done differently:
* I think the Repository should have methods for the "eager" basket (containing items); otherwise JavaScript consumers (who consume the Web Api implementation) won’t be able to retrieve any data except basket id.
* I would rename methods in BasketRepository in accordance to the Repository patter, e.g.: Get, Remove, and Add. You don't have to specify the Basket prefix explicitly (e.g. AddBasket) since it's already in the class name.
* The repository is untestable. There are approaches out there which allow to mock Entity Framework for unit testing. It requires slightly different implementation of repository though.
* Other than that the code looks very structured and easy to read.
