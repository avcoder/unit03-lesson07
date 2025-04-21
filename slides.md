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

# MongoDB
Back-End Development - part 7/12
- [ ] SQL vs No-SQL
- [ ] Install Mongo Shell
- [ ] Perform basic CRUD shell operations

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
(10 min)

- CRUD stands for?
- What HTTP method goes with each CRUD operation?
- What is middleware? 
   - an array of functions stacked together, and it won't go to next function until `next()` is called
   - ex: create middleware: `app.use((req, res, next) => console.log('1st middleware'))`
- every app.use runs in sequence, so request runs thru 1st middleware, then 2nd etc.
- so it runs top most app.use statements first, then runs our routes 
- web architecture; databases persist data
   - compare database tools (sql workbench vs mongodb compass)

<!--
-->

---
transition: slide-left
---

# SQL vs NoSQL
(10 min)

- See [comparison chart](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49823) in LMS
- What is SQL? (Structured Query Language)
   - analogy: it's like a spreadsheet – neat columns, clearly labeled, and you know exactly what kind of data goes in each cell.
   - use when you need structured data, relationships between tables matter (e.g., customers & orders), and you need strong data consistency and integrity
   - ask chatGPT: what is database normalization?
- What is No-SQL? (Not only SQL)
   - analogy: it's like a folder of documents – each one might have similar info but with different structures, more flexible
   - use when you have lots of varied or rapidly changing data, need to scale quickly (ex: web apps with millions of users), or you’re working with flexible or hierarchical data like JSON

<!--
- we use NoSQL as a better use of the time in this bootcamp: flexibility, and scalability. Also since SQL is a mature technology, there are more resources available and community support. 
- Intro MongoDB - one of the options for NoSQL.

-->

---
transition: slide-left
---

# Exercise: Setup MongoDB
(30 min) How does MongoDB work?  What is BSON?

- https://www.mongodb.com/resources/languages/bson
- Sign up/in to mongodb.com
   - Create a free Cluster, name it whatever, select a region closest to you, Create Deployment
   - May authenticate via username/password, Create User, select "My Local Env", Finish and Close
- Download [Compass](https://www.mongodb.com/docs/compass/current/install/#std-label-download-install)
   - [Connect to MongoDB](https://www.mongodb.com/docs/compass/current/connect/#provide-your-connection-string) > Copy the connection string
   - In Compass, click the `+` beside "Connections" to create a new connection
   - Paste connection string > Replace <db_password> with your actual password > Save & Connect
   - on left side, should see green dot beside your cluster, along with `admin`, `local`, `sample_mflix` 
- Optionally may install [MongoDB locally](https://www.mongodb.com/docs/manual/administration/install-community/)

---
transition: slide-left
---

# Exercise continued: MongoDB shell commands
(30 min) Perform queries

- in Compass, click your cluster (should have green dot) > click "Open MongoDB shell"
- it should open up a tab where you can start typing terminal commands.  Try running:
   - `show dbs` - what does this do?
   - `use foodtruck` 
   - `db.createCollection('orders')`
   - `show dbs` -- what did we just do?
- in Compass: click Cluster, click "Refresh" button (top right) -  do you see your foodtruck collection now?
- What do these basic MongoDB shell commands do?
   - `db`, `db.getName()`
   - `db.help()`, `help`, `cls`
   - `show collections`, `db.getCollectionNames()`, `db.getCollectionInfos()`
   - `db.stats()`, `db.orders.stats()`, `db.version()`
   - `db.orders.drop()`, `db.dropDatabase()`

<!--
-->

---
layout: image-right
transition: slide-left
image: /assets/moss.png
backgroundSize: 500px 90px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:
- 🏫 [MongoDB University](https://learn.mongodb.com/)
- ✌️ [MongoDB for VS Code](https://code.visualstudio.com/docs/azure/mongodb)
- 🧱 [Built with what](https://builtwith.com/)
- 🎨 [Data Modeling](https://www.mongodb.com/docs/manual/data-modeling/)

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

# Exercise: CRUD in MongoDB
(40 min) Perform queries in MongoDB

- Read [How to perform CRUD operations](https://www.mongodb.com/resources/products/fundamentals/crud#how-to-perform-crud-operations)
   - Go thru each of the 9 mongoDB CRUD operations to practice creating, reading, updating, and deleting to our `orders` collection.  For example:
      - `db.orders.insertOne({ order: ["1 taco", "1 pop"], name: "bob", isReadyForPickup: false })`
- Q: Does mongoDB let you just randomly add any new property/value when updating an existing document/object without validation? If so, discuss tradeoffs with that ability.
- Stretch goal: create a database/collection and insert just 1 document/object that:
   - emulates a social media app of your choosing (twitter, tiktok, instagram, pinterest etc) 
   - ensure your mock data takes into account all the various pieces of data involved with just one post (including text, image/video urls, date, hashtags, likes, comments, etc)

<!--
-->

---
transition: slide-left
---

# Exercise: Data Modelling
(remainder of time)

- What is data modelling and why is it important?
- 1) Analyze the Scenario:
   - You're building a simple database for a blog that will store: articles, users, comments, tags
- 2) Brainstorm the Data: 
   - Think about what info you might store for each item (ex: comment: user id, comment, date)
- 3) Decide the data model
   - Draw lines to represent relationships between:
      - users to articles, users to comments, articles to comments, articles to tags
      - decide if relationship is one-to-one (1-to-1), one-to-many (1-to-N), many-to-many (N-to-N)
      - if there is a 1-to-N or N-to-N relationship, decide if you should embed or reference which depends on *how you query your data* (what shape of JSON do you want to get back when fetched)
      - Compare your answer to this [video](https://www.youtube.com/watch?v=3GHZd0zv170#t=9m00s)


---
transition: slide-left
---

# Homework

- Practice creating new databases and collections but catered toward a different area
   - ex: movies, books, your hobby/interest, your upcoming note-taking midterm app, etc
   - prepare actual mock data that you will use for next class so that it's more  interesting to you
- Watch video: [Data Modeling with MongoDB](https://www.youtube.com/watch?v=3GHZd0zv170)
   - [research more](https://learn.mongodb.com/courses/relational-to-document-model) on Data Modeling to make your data model match your application's needs