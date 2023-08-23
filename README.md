# Senior Backend Engineer Test

Develop a RESTful API using Node.js, Express, TypeScript, and an SQL database (preferrably PostgreSQL).

**1. Database Design & Setup**:

- Design a database with three tables: `Users`, `Posts`, and `Comments`. Users can have multiple posts, and each post can have multiple comments.
- Implement necessary indexing for anticipated query performance.

**2. API Development**:

- Endpoints to:
    - Create and retrieve users (`/users`).
    - Create a post for a user and retrieve all posts of a user (`/users/:id/posts`).
    - Add a comment to a post (`/posts/:postId/comments`).
    - **Performance Challenge**: Fetch the top 3 users with the most posts and, for each of those users, the latest comment they made. This should be achieved with efficient querying.

**3. Query Optimization Task**:

- Optimize the following SQL query related to the designed schema:
    
    ```sql
    SELECT users.id, users.name, posts.title, comments.content
    FROM users
    LEFT JOIN posts ON users.id = posts.userId
    LEFT JOIN comments ON posts.id = comments.postId
    WHERE comments.createdAt = (SELECT MAX(createdAt) FROM comments WHERE postId = posts.id)
    ORDER BY (SELECT COUNT(posts.id) FROM posts WHERE posts.userId = users.id) DESC
    LIMIT 3;
    
    ```
    

The query attempts to fetch the top 3 users with the most posts and, for each of those users, the latest comment they made. However, it's inefficient and needs optimization.

**4. Middleware & Error Handling**:

- Implement a simple token-based authentication middleware.
- Add basic validation for input data.
- Implement error handling for the main API routes.

**Evaluation Criteria**:

- **Database Design**: Structure, relationships, and indexing strategy.
- **API Design & Implementation**: RESTful practices, efficiency of the code, and especially the performance of the "Performance Challenge" endpoint.
- **Query Efficacy**: Ability to optimize the provided SQL query.
- **Code Quality**: Readability, maintainability, and use of TypeScript features.
- **Error Handling**: How robust the application is against unexpected situations or invalid input.

## Tools/Stack

- NodeJs (TypeScript & Express)
- Postgres for pure data
- Redis
- Docker
- Postman

## Tests

Unit tests are a must, submissions without tests will be ignored.


## Time Duration

3 days

## Submission

1. Your API endpoints should be well documented in POSTMAN.
2. Code should be hosted on a git repository, Github preferably.
3. The API should be hosted on a live server (e.g. https://heroku.com)
4. Your app should be `containerized` using `docker`.
5. Share with us through email the:
    - Repository
    - Hosted API URL
    - Postman Collection Public URL
