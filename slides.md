---
theme: seriph
title: Intro To Fullstack | Abhinav
info: |
  ## Intro To Fullstack | Abhinav
  Prepared for AKCSSC 2024 - GECK December 14, 2024
class: text-center
drawings:
  persist: false
mdc: true
---

# Intro to Fullstack

<div>
  For AKCSSC'24
  <br>
  GECK, Dec 14 2024
</div>

<!--
Oi! <br>
This presentation is made using Slidev.
<br>
 [Slidev Site](https://sli.dev/)
 <br>
 [My github](https://github.com/ruralad) (nothing here)
-->

---

# About Me
<br>
<v-clicks>
  <p>Product Dev @ Envestnet</p>
  <p>Java</p>
  <p>Fullstack Javascript (mainly) & others</p>
</v-clicks>


<!--
[Envestnet ->](https://www.envestnet.com/)

[ThoughtSpot ->](https://www.thoughtspot.com/)

-->

---
transition: slide-up
level: 2
---

# What To Expect
<br>
  <p class="m-0 p-0" v-click>Fundamentals of Fullstack Web</p>
  <span class="inline-block">
    <p v-click v-mark.orange.underline="4">Writing responsible code</p>
    <p v-click="3" class="inline-block" v-mark.orange.underline="4">Getting Industry Ready</p>
  </span>



<!--
- Top level or very basic intro to key concepts
- You need to know what you are writing
- You need to know others will work on the same code
- Example - Error Handling
- Responsible code and industry ready is closely related
-->

---

# How to Follow Along

<br>
<v-clicks>
  <p>Slides + Code</p>
  <p>Ask Questions Anytime</p>
  <p>Notes?</p>
</v-clicks>

---
transition: slide-up
layout: statement
---

# The Journey of a Web Request

<br>

<v-clicks>
<p >
<img class="inline"  src="https://fonts.gstatic.com/s/e/notoemoji/latest/261d_fe0f/512.gif" alt="☝" width="32" height="32">
 User initiates action</p>
<p><img class="inline" src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f6eb/512.gif" alt="🛫" width="32" height="32">
 Request travels through network</p>
<p><img class="inline" src="https://fonts.gstatic.com/s/e/notoemoji/latest/2699_fe0f/512.gif" alt="⚙" width="32" height="32"> Servers process the request</p>

<p><img class="inline" src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f6ec/512.gif" alt="🛬" width="32" height="32"> Data transforms and travels</p>
<p><img class="inline"  src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f440/512.gif" alt="👀" width="32" height="32"> User sees the result</p>
</v-clicks>

<!--
# Google Search Example
Google responds according to our request with search param.

- Now lets draw a diagram for this
-->

---
clicks: 2
---

<img src="/request-1.png" />

<!--


This is the most basic fullstack app. We can remove the Database to make it even 'more basic'

[click]
Lets try to identify what could be problems when we deploy this

[click]
<br>
Take an example of a banking app. 
<br>

- Say we are implementing this same set up for the banking app
- User can type their mail(or mobile or any unique data point), and get their current account details, bank balance and all
- Can't anybody(even if they dont have bank account) get details of everyone by brute force?
- Isn't an invalid requested still load on server?

## We should introduce Authentication

-->

---
clicks: 3
---

<img src="/request-2.png" />

<!--

- [click] Note: Server also call the auth service for verifying the token

[click]
### Now case for Authorization
- If one person knows the email of the other person, even if the person is
authenticated, where is the logic to identify if the current user is actually asking only for their data

[click] 
## Consider URL Shortner

- Same request is made by thousands of users. 
- request -> server fires a request to check database for the shortened url -> database returns the complete url

## Other examples
- Election, new data is came in every 5 minutes
- Banking app itself, where we show like currency exchange rate( same for all users)

-->

---
clicks: 1
---

<img src="/request-3.png" />

<!--
## Why cache ?
- Faster data retrieval : cache stored in memory, significantly faster than accessing data from a hard disk, better UX
- Reduced database load, improving Scalability

[click]
## What happens when our app go viral ?
- URL Shortner goes viral. Our server is overloaded
- First, we can improve our server resources (increase cpu and ram)
- But what happens when its practically impossible? : We can introduce more servers
- Scaling is implemented. We have done VERTICAL and HORIZONTAL scaling
- How to choose which request to pass to which server? : LOAD BALANCER

-->

---

<img src="/request-4.png" />

<!--

Scaling is extremely important in the modern web as it allows websites and applications to handle increasing user traffic and data loads without experiencing performance issues or service disruptions

- We can scale db and cache, auth services as well and bring them closer to the user
- An Indian user dont have to request american db's for data, we can introduce a new server in Mumbai to provide better UX

-->

---
layout: center
---

<h1 v-mark.green.strike-through="1" class="inline-block"> Requests, Responses </h1>
<h1 v-click="2"> APIs- Application Programming Interfaces </h1>
<div v-click="3">
<p>What data can be requested or sent</p>
<p>How to make these requests (protocols)</p>
</div>

<!--

- A set of rules and protocols allowing software applications to communicate.
- Enables interaction between different software systems.

[click:3]
- **Protocols**: Standards that govern communication
  - **HTTP/HTTPS**: Most common protocols for APIs
  - Others: WebSocket, gRPC, etc.

-->

---

# RESTful APIs

### REST (Representational State Transfer)

- **Architecture style** for building APIs.
- Over http/https
- Key principles:
  1. **Client-Server**: Separation of client and server concerns.
  2. **Stateless**: Each request contains all necessary information.
  3. **Cacheable**: Responses must define cacheability.
  4. **Uniform Interface**: Standardized operations.
  5. **Layered System**: Modularity for scalability.


 <!-- Why Scalable? each request is treated independently and doesn't rely on information from previous requests, allowing for easy horizontal scaling by adding more servers to handle increased traffic without complex state management.
  -->
---

### HTTP Methods in REST

|    |                   |
|----------|------------------------------|
| **GET**  | Retrieve data                |
| **POST** | Submit data to create        |
| **PUT**  | Update existing data         |
| **DELETE**| Remove data                 |
| **PATCH**| Partially update existing data |

<!-- examples can be instagram get post, new post, update description

- PATCH is STILL RELEVANT!
 -->

---
layout: center
---

<h1> DATABASES</h1>

<v-click>

Types of Databases:
  - **Relational Databases**: Structured, uses tables (e.g., MySQL, PostgreSQL).
  - **NoSQL Databases**: Flexible schema, often for unstructured data (e.g., MongoDB, Firebase).
  - Modern databases, like vector db's, graph db's and more.
</v-click>

---

# Relational Databases and SQL

### SQL (Structured Query Language)

<br>
<v-clicks>

- **Standard language** for interacting with relational databases.
- Common SQL operations:
  - **SELECT**: Retrieve data from a table.
  - **INSERT**: Add new data to a table.
  - **UPDATE**: Modify existing data.
  - **DELETE**: Remove data from a table.
- Relational concepts:
  - **Primary Keys**: Unique identifier for records.
  - **Foreign Keys**: Links between tables.

</v-clicks>

---

### Example SQL Query

<br>
<br>

```sql {all|1|2|3|all}
SELECT name, age 
FROM users 
WHERE age > 18;
```
<br>
<br>

- Retrieves names and ages of users older than 18.

<!-- Consider a table users, with columns userId, name, age, address, etc.
This query is to get the 'name and age' of all users who are above 18 -->


---
layout: center
---

<h1>FRONTEND</h1>
<h2>The Only Thing That Actually Matters :)</h2>
<br>

<v-clicks>

  - **HTML**: structure, format, and content of a page.
  - **CSS**: layout and appearance.
  - **Javascript**: interactivity and functionality.
  - **WebAssembly**??? : run multiple languages in browser
</v-clicks>

<!-- No matter how perfect your backend is, at the end of the day, if you can't provide a good UX, your app is dead from day 1.

This includes good design, colors, animations, transitions and everything else. -->

---
layout: center
---

# Frameworks have taken over frontend

<v-click>
React, Vue, Svelte, Solid and many more...
</v-click>
<br>
<span v-click v-mark.orange.underline="3">
No Basics, No Use
</span>
<!-- 
At the end of the day, if your basics are trash, if you don't know how things work in the browser, it will be very difficult for you to understand frameworks, essentially delivering below average code -->

---

# Lets Build!

### Server first

``` {1|1-2|1-3|1-4}
- A programming language with basic networking capabilities (Almost all)
- Create a server, and listen(open) a port
- Serve endpoints (eg : / should serve 'hello', /account should serve 'hi')
- Proper error handling (responsible 🙂)
```

<div v-click="'+1'">

<br>

### Build a better server?

```
- Write API's for frontend to call from
- Database?
```
</div>

<br>
<div v-click="'+1'">

### Frontend

```
- Use HTML, CSS and JS (no frameworks!)
- Create a form
- Send request to server, HANDLE FRONTEND ERRORS!
- Display the result
```

</div>