# Library catalogue

## Functional and Non-Functional Requirements

**Functional:**

- Manage books, authors, and categories.
- Filter books by title, author, category, and availability.
- Support pagination.
- User authentication.
- Return meaningful status codes.
- Follow RESTful principles (Richardson maturity model).

**Non-Functional:**

-  Fast response time (optimized endpoints).
- Use caching where data changes rarely (e.g., categories).
- Scalable and secure architecture.
- Proper API versioning (e.g., /api/v1/...).

## 1. Describe what entities:

| Entity      | Fields                                                                                       |
|-------------|----------------------------------------------------------------------------------------------|
| Book        | <br/> id <br/> title <br/> authorId <br/> categoryId <br/> publishingYear <br/> availability |
| Author      | id<br/>name<br/>birthYear                                                                    |
| Category    | id<br/>name                                                                                  |


## 2. API functions:


| Entity   | Fields                                                                                                                                                                                                                                                                                             |
|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Book     | Create author (POST localhost:8080/catalogue) <br/> Get author by id (GET localhost:8080/catalogue/id) <br/> Get all authors (GET localhost:8080/catalogue) <br/> Get all books from author (GET localhost:8080/catalogue/id/books) <br/> Delete author (DELETE localhost:8080/catalogue/id)       |                                                                |
| Author   | Create author (POST localhost:8080/authors) <br/> Get author by id (GET localhost:8080/authors/id) <br/> Get all authors (GET localhost:8080/authors) <br/> Get all books from author (GET localhost:8080/authors/id/books) <br/> Delete author (DELETE localhost:8080/authors/id)                 |
| Category | Create author (POST localhost:8080/categories) <br/> Get author by id (GET localhost:8080/categories/id) <br/> Get all authors (GET localhost:8080/categories) <br/> Get all books from author (GET localhost:8080/categories/id/books) <br/> Delete author (DELETE localhost:8080/categories/id)  |


## 3. Status codes


| Code  | Meaning                          |
|-------|----------------------------------|
| 200   | OK                               |
| 201   | Created                          |
| 204   | No content                       |
| 400   | Bad Request                      |
| 401   | Unauthorized                     |
| 403   | Forbidden (auth but not allowed) |
| 404   | Not found                        |
| 422   | Unprocessable Entity             |
| 500   | Internal Server Error            |

## 4. Richardson Maturity Model

| Level   | Feature                       | Included                                  |
|---------|-------------------------------|-------------------------------------------|
| 0       | Single endpoint               | false (/catalogue, /authors, /categories) | 
| 1       | Resources                     | true                                      | 
| 2       | HTTP methods                  | true                                      |
| 3       | Hypermedia                    | false                                     |

## 5. Authentication

- OAuth 2.0. Endpoints requiring auth: POST, PUT, DELETE

## 6. Caching to reduce unnecessary load on static data:

- **GET /categories** — use Cache-Control: public, max-age=86400
- **GET /authors** — use Cache-Control: public, max-age=86400
- **GET /catalogue** — use Cache-Control: public, max-age=86400
