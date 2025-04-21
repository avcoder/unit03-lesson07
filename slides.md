---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Node.js - part 6/12
Back-End Development
- [ ] Web Infrastructure
- [ ] Purpose of Databases
- [ ] Intro to Agile/Scrum

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->

---
transition: slide-left
---

# Recap
(15 min)

- Dynamic routes `app.get('/order/:id', () => { console.log(req.???.??) })`
- What is middleware?
- Show [steps](https://github.com/avcoder/express-steps/blob/main/ExpressSteps.md) in creating express app so far
- https://reqres.in/
- Demo redirect
  ```js
  app.get('/redirect-with-query', (req, res) => {
    res.redirect('/new-path?status=success');
  });
  ```
- Demo morgan package
  ```js
  const morgan = require('morgan');
  const app = express();
  app.use(morgan('dev'));  
  // create a GET endpoint, goto it, view terminal
  ```

<!--
- middleware examples: body-parser, cors
-->

---
transition: slide-left
---

# Databases Intro
(15 min)

- What are some different ways you've stored data? (List examples)
   - Did you experience any limitations especially when you had to add more info or retrieve specific info?
- What is a database?
  - A database is a system that stores and organizes data so it can be accessed and updated efficiently. 
  - Demo Airtable 
- Why do we need databases? (think scalability, consistency and real-time data access)
- CRUD operations = Create, Read, Update, Delete

<!--
- Demo Airtable: Create book table and author table, relationship, then filter it
- basic examples of storing data: JSON, csv files, spreadsheets
- filter title contains bourne && year = 1986
-->

---
transition: slide-left
---

# Exercise: GET / POST and CRUD operations
(20 min) Explore how real websites use these operations by inspecting network traffic

1. Each person selects a website
2. Inspect DevTools > Network tab
3. Find one example of a GET request (perhaps on page load, clicking a button)
4. Find one example of a POST request (perhaps logging in, adding a shopping cart item)
5. Find one example of another kind of request if possible (PUT, DELETE)
6. Write down the following information you were able to obtain via the Network tab
   - Record the URL
   - What method was used
   - What did that action do (ex: it fetched a list of books, it submitted login form)
   - in your opinion, which CRUD operation was performed 
   - If it was a POST request, can you find the data that was sent (see Payload tab)
7. Each person presents to their group what they found

Prepare to share with the rest of the class any curiosity questions

---
transition: slide-left
---

# Relational Databases
(5 min)

- SQL (Relational): When you need structured data with relationships, transactional integrity (ACID properties), and powerful querying capabilities.
- Examples of relational databases: mySQL, PostgreSQL, SQLite
- Ask ChatGPT: "list companies that use sql relational databases"

<!--
- ask students to lookup each letter of ACID
-->

---
transition: slide-left
---

# Non-relational (noSQL) Databases
(5 min)

- NoSQL (Non-relational / Not Only SQL): When you need flexibility, scalability, fast read/write operations, or to handle unstructured or semi-structured data (e.g., documents, key-value pairs, graphs).
- Examples of noSQL databases: MongoDB, Firebase, Redis
- Ask ChatGPT: "list companies that use nosql databases"

---
transition: slide-left
---

# Exercise 2 : Databases and Web Architecture
(20 min) Explain how databases fit into the structure of the web

Imagine your group is building a simple login form app.  You must work together to reconstruct and explain how the Client, Server, and Database interact in your app when a user wants to sign in.

1. Take 5 to 10 minutes where each member of the group attempts to [draw](https://excalidraw.com/) a simple diagram showing the interaction between Client (browser/user), Server (where logic lives), and Database (Where data is stored) when a user logs in.
2. Label your diagram with arrows to show the direction of communication
3. Each member then takes 2 minutes to present their own diagram to the group, until everyone has had their turn.
4. Pick one diagram from the group and be prepared to present it to the class when we come back together. (Feel free to edit this diagram to incorporate any gaps that may have been uncovered as you were presenting to each other)
5. Ask ChatGPT: "List full-stack web development stacks." (then guess which one we'll be learning)

<!--
- https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49821
- Demo Canadian Tire login > Network tab
-->

---
layout: image-right
transition: slide-left
image: /assets/dodds.png
backgroundSize: 500px 140px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:
- 💻 [Relational vs Nonrelational DBs](https://www.freecodecamp.org/news/relational-vs-nonrelational-databases-difference-between-sql-db-and-nosql-db/)
- ☁️ [7 Database Paradigms](https://www.youtube.com/watch?v=W2Z7fbCLSTw)
- ▶️ [Intro to Scrum](https://www.youtube.com/watch?v=9TycLR0TqFA&t=5s)
- 📔 [Guide to Agile Methodology](https://www.freecodecamp.org/news/complete-guide-to-agile-methodology/)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

<!-- 
- take attendance
-->

---
transition: slide-left
---

# Agile Theory - Collaborate in Software Deelopment
(20 min) What is Agile and Scrum?

- Watch (7 mins) https://www.youtube.com/watch?v=9TycLR0TqFA&t=5s
- Look thru [Agile Manifesto](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49824)
- [Watch](https://www.youtube.com/watch?v=BVbfNiRbgjU) Scrum Card Game
- What's a sprint?
- How do teams organize work and to-dos in software development?
- See Github "Projects" option
- Challenge: Use GitHub projects to create a mock board for your midterm project

---
transition: slide-left
---

# Exercise: Routers
(remainder of time)

- Refer to [Routers](https://www.theodinproject.com/lessons/nodejs-routes#routers)
- refactor our [food truck](https://github.com/avcoder/food-truck-express/blob/main/index.js) app to use routers for better organization and prepare us for the next class (to use controllers)

---
transition: slide-left
---

# Homework

- Download MongoDB's [compass](https://www.mongodb.com/products/tools/compass) and also sign up to create an account
