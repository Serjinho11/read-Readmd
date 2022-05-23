# Web API Service

## 1. API endpoints for Product

### Requirements

Our client requires a web API in order to expose the products to a third-party application. That application will be created later by another company.

The Web API application must be able to use the same database as the console application. This means that the same DataAccess and Domain entities from the console application can be reused here.

For details about the needed endpoints see the document:

- [Product Endpoint](product-endpoints.md)

### Suggestions

Use the Postman application to help testing the created endpoints.

- https://www.postman.com/

## 2. API endpoints for Sale (Optional)

Additional endpoints should be created for the Sale entity, to expose information about the products that have been sold.

For details about the needed endpoints see the document:

- [Sale Endpoint](sale-endpoints.md)
