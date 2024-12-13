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

<h1> DATABASES </h1>
