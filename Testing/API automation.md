## 🔹 Stage 1: Fundamentals (Beginner)

**What to Learn**
---
***What is an API? Types: REST, SOAP, GraphQL, gRPC.**

REST (Representational State Transfer):
REST is an architectural style for designing networked applications.
It operates over HTTP and uses standard HTTP methods (GET, POST, PUT, DELETE) to perform operations on resources, which are identified by URLs.
REST APIs are stateless, meaning each request from a client to the server contains all the information needed to understand the request.
They typically exchange data in formats like JSON or XML.

GraphQL:
GraphQL is a query language for APIs and a server-side runtime for executing queries using a type system defined for your data. 
It allows clients to request exactly the data they need, preventing over-fetching or under-fetching of data.
GraphQL APIs typically expose a single endpoint, and clients send queries to retrieve specific data, mutations to modify data, and subscriptions for real-time updates.

Main Characteristics:

Strongly Typed: GraphQL APIs are strongly typed, which means that each field has a specific data type. This makes it easier to validate and handle data on the client and server sides.

Query Language: GraphQL has its own query language that allows clients to specify exactly what data they need. This reduces over-fetching of data and improves performance.

Single Endpoint: GraphQL APIs have a single endpoint, which means that clients can fetch all the data they need from a single request.

Declarative: GraphQL APIs are declarative, which means that clients specify what they want, not how to get it. This allows for more efficient and flexible data fetching.

Schema-Driven: GraphQL APIs are schema-driven, which means that the schema defines the structure of the data and the available queries and mutations. This makes it easier for developers to understand and work with the API.

https://dev.to/pragativerma18/a-guide-to-the-most-popular-types-of-apis-rest-soap-graphql-and-grpc-4ail

---
***Key concepts: Request/Response, Endpoints, Resources, Methods (GET, POST, PUT, DELETE, PATCH).**

🔑 1. Request & Response

* **Request**: What the client (you, browser, Postman, automation script) sends to the server.

  * Includes **method** (GET, POST, etc.), **URL/endpoint**, **headers**, and **body** (if needed).
    
* **Response**: What the server sends back.

  * Includes **status code**, **headers**, and **body** (data).

**Example**

* Request:

  ```
  GET https://api.example.com/users/123
  ```
* Response:

  ```json
  {
    "id": 123,
    "name": "John Doe",
    "email": "john@example.com"
  }
  ```

---

🔑 2. Endpoints

* An **endpoint** is a specific URL where an API can be accessed.
* Think of it like an “address” to reach a resource.

**Example**

* `https://api.example.com/users` → endpoint to manage users.
* `https://api.example.com/orders` → endpoint to manage orders.

---

🔑 3. Resources

* A **resource** is the data object you’re interacting with (usually nouns: users, products, orders).
* REST APIs treat resources like **entities** that you can manipulate with HTTP methods.

**Example**

* Resource: `user`
* Endpoint: `/users`
* A specific user resource: `/users/123`

---

🔑 4. Methods (CRUD Operations)

HTTP methods define **what action** you want to perform on a resource.
They often map to **CRUD** (Create, Read, Update, Delete).

* **GET** → Retrieve data.
  Example:

  ```
  GET /users/123
  ```

  → fetches user with id 123.

* **POST** → Create new data.
  Example:

  ```
  POST /users
  Body: { "name": "John", "email": "john@example.com" }
  ```

  → creates a new user.

* **PUT** → Update **entire resource** (replace).
  Example:

  ```
  PUT /users/123
  Body: { "name": "John Smith", "email": "john.smith@example.com" }
  ```

  → replaces user 123 with new details.

* **PATCH** → Update **partial resource** (modify).
  Example:

  ```
  PATCH /users/123
  Body: { "email": "john.new@example.com" }
  ```

  → only updates the email.

* **DELETE** → Remove resource.
  Example:

  ```
  DELETE /users/123
  ```

  → deletes user 123.

---

###Putting it all together:###

* **Resource** = `users`
* **Endpoint** = `https://api.example.com/users`
* **Request/Response** = communication between client & server
* **Methods** = actions you can take (GET, POST, PUT, PATCH, DELETE)

---

**Idempotent** 
means that making the same API call multiple times leaves the system in the same state as making it once.
In HTTP: GET, PUT, DELETE are idempotent. POST is not. PATCH can be idempotent depending on implementation.

---
***HTTP basics: Headers, Status Codes, Query Params, Path Params, Body, Authentication.**

**Status Codes**
1xx → Informational
100 Continue

2xx → Success
200 OK – request succeeded
201 Created – new resource created
204 No Content – success but no body returned

3xx → Redirection
301 Moved Permanently, 302 Found

4xx → Client Error
400 Bad Request – invalid input
401 Unauthorized – no/invalid credentials
403 Forbidden – not allowed
404 Not Found – resource doesn’t exist

5xx → Server Error
500 Internal Server Error
503 Service Unavailable

---
***JSON vs XML payloads.**

🔹 JSON (JavaScript Object Notation)

* **Lightweight** data format, human-readable.
* Uses **key-value pairs** with `{ }` and `[ ]`.
* Most modern REST APIs use JSON.
* Easy to parse in any programming language.

**Example JSON payload**

```
json
{
  "id": 123,
  "name": "John Doe",
  "email": "john@example.com",
  "roles": ["admin", "editor"],
  "address": {
    "city": "San Francisco",
    "zip": "94107"
  }
}
```

---

🔹 XML (eXtensible Markup Language)

* **Older, heavier** format (used in SOAP APIs, legacy systems).
* Uses **tags** `<tag>value</tag>` to represent data.
* More verbose than JSON.
* Supports schemas (XSD) for strict validation.

**Example XML payload**

```xml
<User>
  <Id>123</Id>
  <Name>John Doe</Name>
  <Email>john@example.com</Email>
  <Roles>
    <Role>admin</Role>
    <Role>editor</Role>
  </Roles>
  <Address>
    <City>San Francisco</City>
    <Zip>94107</Zip>
  </Address>
</User>
```


---
***Tools: Postman (manual testing), curl (CLI).**

```
https://www.youtube.com/watch?app=desktop&v=VywxIQ2ZXw4&t=186s
```



---

**Questions to Ask Yourself**

* What’s the difference between REST and SOAP APIs?
* How do I test a GET vs POST request?
* What happens if I don’t provide required headers or parameters?
* How do I validate response codes and payloads?

---

## 🔹 Stage 2: Intermediate – Testing Approaches

**What to Learn**

* Types of API testing:

  * Functional testing
  * Negative testing
  * Data-driven testing
  * Performance/load testing
  * Security testing (basic auth, OAuth2, JWT).
 
Functional Testing → Valid user creation (201 Created).

Negative Testing → Invalid email returns 400 Bad Request.

Data-Driven Testing → Reuse same test with multiple datasets using test.each().

Performance/Load Testing → Multiple parallel requests using Promise.all.

Security Testing → Login returns JWT → use token in Authorization header → verify access.


7.1 Validation Testing
Validation testing ensures that the API returns the correct data in the right format.
```
test('User email is valid', async () => {
    const response = await axios.get('https://jsonplaceholder.typicode.com/users/1');
    expect(response.data.email).toMatch(/\S+@\S+\.\S+/);
});
```
7.2 Functional Testing
Functional testing verifies that the API works as expected and all the endpoint interactions are functioning correctly.

test('Create a new post', async () => {
    const post = {
        title: 'foo',
        body: 'bar',
        userId: 1
    };
    const response = await axios.post('https://jsonplaceholder.typicode.com/posts', post);
    expect(response.data.title).toBe('foo');
    expect(response.data.body).toBe('bar');
    expect(response.data.userId).toBe(1);
});
7.3 Security Testing
Security testing validates that your API is secure from attacks and vulnerabilities.

test('Cannot access secured endpoint without token', async () => {
    try {
        await axios.get('https://myapi/secure');
    } catch (error) {
        expect(error.response.status).toBe(401);
    }
});
7.4 Error Detection
Error detection checks how the API handles failures. Does it crash? Does it return meaningful error messages?

test('Non-existent endpoint returns 404', async () => {
    try {
        await axios.get('https://jsonplaceholder.typicode.com/nonexistent');
    } catch (error) {
        expect(error.response.status).toBe(404);
    }
});

**Contract testing **
Contract testing ensures API consumer and provider stick to agreed request/response format.

Can be done via:
Schema validation (SuperTest + Ajv).
AJV ? 
 
Ajv → more powerful, supports JSON Schema draft-07+, custom keywords, better performance for big schemas.
```
// Initialize JSON Schema validator
const ajv = new Ajv({ allErrors: true });
addFormats(ajv); // supports formats like "email", "uri", "date-time"

const app = "https://api.example.com"; // Replace with real API base URL

describe("Contract Testing - User API", () => {
  it("GET /users/:id should match User schema", async () => {
    const res = await request(app).get("/users/1").expect(200);

    const validate = ajv.compile(userSchema);
    const valid = validate(res.body);
    ```

```
const request = require("supertest");
const Ajv = require("ajv");  // JSON schema validator
const ajv = new Ajv();
const app = "https://api.example.com";

// Define the contract
const userSchema = {
  type: "object",
  required: ["id", "name", "email", "isActive"],
  properties: {
    id: { type: "number" },
    name: { type: "string" },
    email: { type: "string", format: "email" },
    isActive: { type: "boolean" }
  },
  additionalProperties: false
};

describe("Contract Testing with JSON Schema", () => {
  it("response must follow user schema", async () => {
    const res = await request(app).get("/users/1").expect(200);

    const validate = ajv.compile(userSchema);
    const valid = validate(res.body);

    expect(valid).toBe(true); // contract holds
  });
});
```

Consumer-driven testing tools (Pact, Spring Cloud Contract).
Tools like Pact let consumers (frontend/microservices) define the expected contract.
The provider (API) is then verified against that contract.

Real-world benefit: Prevents breaking changes in microservices or frontend-backend integration.


Fuzz testing - sql injection 



GRAPHQL: https://www.freecodecamp.org/news/building-consuming-and-documenting-a-graphql-api/

* Writing test cases for APIs.
* Automation basics: using Java (RestAssured), Python (Requests, PyTest), or JS (SuperTest, Playwright).

In javascript -> using AXIOS as A promise-based HTTP client for Node.js and browsers, JEST as test runner 
https://medium.com/@waleedmousa975/a-comprehensive-tutorial-on-api-testing-with-javascript-ddee3192bac5

SUPERTEST with JEST

// Jest syntax
describe("API Tests", () => {
  it("should return 200 for GET /users", async () => {
    const res = await request(app).get("/users/1");  // SuperTest call
    expect(res.status).toBe(200);                   // Jest assertion
  });
});


PLAYWRIGHT API TESTS
JAVA - REST ASSURED


* API mocking/stubbing (WireMock, Postman mock server).

API mocking and stubbing helps us test independently of backend availability. We use WireMock when we need a local controllable stub (simulate latency, 500 errors, etc.), and Postman mock servers when we want quick mocks for frontend or QA teams. This allows parallel development, better test coverage, and stable CI pipelines

nock (most common in Node.js testing)

Jest allows you to easily mock modules in your tests. Here’s an example of mocking axios get response:
```
jest.mock('axios');

axios.get.mockResolvedValue({
    data: {
        id: 1,
        name: 'Leanne Graham'
    }
});

test('Get user with ID 1', async () => {
    const response = await axios.get('https://jsonplaceholder.typicode.com/users/1');
    expect(response.data.name).toBe('Leanne Graham');
});
```
* API documentation tools: Swagger/OpenAPI.

**Questions to Ask**

* How do I write a test case for an API?
* How do I test an API that isn’t ready yet (mocking)?
* How do I validate nested JSON responses?
* What’s the difference between functional and integration API tests?
* How do I handle dynamic data in API responses?



---

# 🔹 1. How do I validate nested JSON responses?

👉 If an API returns **complex/nested JSON**, you need to assert **deep object properties**.
Example response:

```json
{
  "id": 1,
  "name": "Alice",
  "address": {
    "street": "123 Main St",
    "city": "Irvine",
    "geo": {
      "lat": 33.6846,
      "lng": -117.8265
    }
  }
}
```

### ✅ Jest + SuperTest Example:

```js
test("should validate nested JSON fields", async () => {
  const res = await request(app).get("/users/1");

  expect(res.statusCode).toBe(200);
  expect(res.body.address.city).toBe("Irvine");      // nested property
  expect(res.body.address.geo.lat).toBe(33.6846);    // deep nested property
});
```



---

# 🔹 2. What’s the difference between **functional** and **integration** API tests?

| Type                     | Scope                                                                                                   | Example                                                                                              |
| ------------------------ | ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Functional API Test**  | Tests a **single API endpoint** in isolation, verifying its input/output behavior matches requirements. | Test `GET /users/1` returns correct status code & JSON fields.                                       |
| **Integration API Test** | Tests how **multiple APIs/services work together**, including DB, authentication, external services.    | Test `POST /order` creates an order, then `GET /order/:id` retrieves it correctly (end-to-end flow). |

👉 In short:

* **Functional** = “Does this API work as per spec?”
* **Integration** = “Do APIs + services work correctly together in a workflow?”



# 🔹 3. How do I handle dynamic data in API responses?

Many APIs return values that **change every run** (timestamps, IDs, tokens, UUIDs). If you assert exact values, tests will fail.

### ✅ Strategies:

1. **Partial Validation**
   Only check the fields you care about.

   ```js
   expect(res.body).toEqual(
     expect.objectContaining({
       id: expect.any(Number),  // dynamic but type validated
       name: "Alice"
     })
   );
   ```

2. **Regex/Pattern Matching**

   ```js
   expect(res.body.token).toMatch(/^eyJ/); // JWT starts with eyJ
   ```

3. **Schema Validation** (Ajv, jsonschema)

   ```js
   const schema = {
     type: "object",
     properties: {
       id: { type: "number" },
       createdAt: { type: "string", format: "date-time" }
     },
     required: ["id", "createdAt"]
   };
   expect(validator.validate(schema, res.body)).toBe(true);
   ```

4. **Store Dynamic Data for Next Requests**
   Example: Login API returns a JWT → store it → use it in headers for subsequent tests.

   ```js
   let token;
   test("login returns token", async () => {
     const res = await request(app).post("/login").send({ user: "alice", pass: "123" });
     token = res.body.token;
     expect(token).toBeDefined();
   });

   test("access protected resource", async () => {
     const res = await request(app).get("/profile").set("Authorization", `Bearer ${token}`);
     expect(res.statusCode).toBe(200);
   });
   ```


---

## 🔹 Stage 3: Advanced – Automation & Frameworks

**What to Learn**

* API automation frameworks:
  * Java + RestAssured + TestNG/JUnit + Maven/Gradle
  * JavaScript + Jest/SuperTest
* BDD with Cucumber + API steps.
* Assertions: JSONPath, XMLPath.
* Parameterization (data-driven tests from CSV/Excel/DB).
* CI/CD Integration (Jenkins, GitHub Actions).
* API versioning & backward compatibility testing.
* Contract testing with Pact.
* Performance testing with JMeter/Gatling/Locust.

jmeter with java
https://medium.com/javarevisited/rest-api-load-performance-testing-using-apache-jmeter-63605572e862

Number of Threads (users): The number of users that JMeter will attempt to simulate.
Ramp-Up Period (in seconds): The duration of time that JMeter will distribute the start of the threads over.
Loop Count: The number of times to execute the test.

**Questions to Ask**

* How do I design a reusable API automation framework?
* How do I integrate API tests into CI/CD pipelines?
* How do I manage environment configs (dev/stage/prod)?
* How do I handle authentication in automated tests (tokens refresh, OAuth flow)?
* How do I ensure test scalability and maintainability?

-----
how do you design a framework from scratch for api testing using rest assured, tell all important librarirs to use and examples of functional, negative, data driven , contract,performance , security, load, mocking stubbing and schemavalidation kinds of testing, tell me the some of the challenges that we get and how to resolve them 


---

## 🔹 Stage 4: Expert – Real-World & Interview Prep

**What to Learn**

* Advanced security testing (SQL injection, XSS, MITM basics).
* Chaos testing/fault injection.
* API monitoring in production (Prometheus, CloudWatch).
* Logging, reporting, dashboards (Allure, Extent Reports).
* Metrics: Coverage of endpoints, critical flows, error handling.

**Interview-Focused Questions**

1. How do you design and implement an API test automation framework?
2. How do you test APIs without UI? Give a scenario.
3. How do you validate complex JSON responses?
4. How do you handle API dependencies in automation?
5. What’s the difference between functional, integration, regression, and contract testing for APIs?
6. How do you test APIs under load or stress?
7. How do you mock or stub APIs during testing?
8. Tell me about a tricky API bug you found and how you debugged it.
9. How do you test an API that uses OAuth2/JWT authentication?
10. How do you ensure your API test suite is maintainable and scalable?

HTTP Methods: RESTful APIs leverage standard HTTP methods to indicate actions on resources. Here’s a breakdown of the most common:

GET: Retrieves data from the server (e.g., getting a list of books, fetching a single book by ID).
POST: Creates a new resource on the server (e.g., adding a new book to the catalog).
PUT: Updates an existing resource on the server (e.g., editing a book’s information).
DELETE: Removes a resource from the server (e.g., deleting a book).
Status codes: The server returns HTTP status codes to convey the outcome of an API request. Understanding these codes helps you test successfully:

2xx Success: Indicates successful actions (e.g., 200 OK for a successful GET, 201 Created after a successful POST).
4xx Client Error: Signals an issue likely related to the request itself (e.g., 400 Bad Request for invalid data, 404 Not Found if a resource doesn’t exist).
5xx Server Error: Points to problems on the server side (e.g., 500 Internal Server Error).
Validation: A crucial aspect of API testing is ensuring responses from the server are valid and meet expectations. This involves:

Structure: Verify that the response adheres to the expected format, typically JSON for RESTful APIs.
Content-Type: Confirm that the Content-Type header correctly specifies the format of the response (e.g., application/json).
Data Integrity: Check that the data within the response matches your expectations, both in terms of values and their types.

Beyond the Basics
Error Handling: Include tests that deliberately trigger error scenarios (e.g., invalid input, missing resources) and ensure your API responds with appropriate error codes and messages.
Parameterization: Use PyTest’s parameterization feature to efficiently test multiple input variations within a single test function.''

------

API test automation framework how build ? what challenges you got ? how resolved?
https://medium.com/@m4manishd/building-a-robust-api-test-automation-framework-using-rest-assured-65a761751f82

Schema Validation:
Focuses on the structural integrity of data exchanged between API provider and consumer.
API Contract Testing:
A broader concept that verifies the entire agreement, or "contract," between an API provider and its consumers.
Includes schema validation to ensure syntactic conformance (data structure).
Extends beyond schema validation to cover behavioral aspects, such as:
Expected response codes for various scenarios.
Error handling mechanisms.
Business logic and expected data values under specific conditions.
Performance and latency expectations.

