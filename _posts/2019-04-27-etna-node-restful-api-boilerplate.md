---
layout: post
title: "Etna 🌋- A Nodejs boilerplate for RESTful API"
quote: "... when I wanted to try and make an API using MySQL I was rather surprised as I couldn't find a proper boilerplate that I could use comfortably and easily without much hassle. [But]..."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Dasith Kuruppu
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>

Originally published @ dasithsblog.com

![Image of mount Etna](https://cdn-images-1.medium.com/max/2000/0*KLo4v-djaADfc5KW.jpg)*Image of mount Etna*

**The background & motivation for the boilerplate**

Before I introduce [Etna](https://github.com/DasithKuruppu/etna) lets discuss a bit about what motivated me to create this boilerplate and a bit of background on how I got to the point of creating this boilerplate.I have been working with and building a lot of Nodejs related applications & API’s over the years.What I have been noticing most of the time was that most boilerplates or projects I came across rarely used SQL/relational databases as the underlying database. I think this was partly because a couple of years ago most nodejs drivers for mysql was really buggy and a bit inconsistent in performance compared to existing drivers for most to other languages and frameworks. This coupled with the undeniable trend towards NoSQL over the last few years probably had something to do with the slow adoption rate towards SQL in the nodejs community. However today most drivers are battle tested, well established and relatively consistent. Despite that fact when I wanted to try and make an API using MySQL I was rather surprised as I couldn't find a proper boilerplate that I could use comfortably and easily without much hassle. Most boilerplates included the basic [mysql](https://github.com/mysqljs/mysql) driver/npm module. Which was good enough and got the job done, but also meant that you manually had to write most of the SQL yourself.This usually ended up with most boilerplates having tight coupling between persistence layer and models/API. This lead me down a path of searching for something with a little more abstraction to the underlying database however could hardly find any that matched my needs. So I was left with no option but to try and create my own boilerplate, this I didn’t want to start from scratch or *reinvent the wheel* so I went ahead and did some searching for a bare bones boilerplate that at least had Nodejs , Typescript & a API framework used. I then came across [Matterhorn](https://medium.freecodecamp.org/announcing-matterhorn-a-node-js-api-server-boilerplate-4994759f1bf6) which is exactly that and seemed quite simple and solid. So I decided to build my boilerplate on top of it reworking some of its structure and adding more features.

## The birth of Etna 🌋 and what it offers !

Thanks to [Matterhorn 🏔️](https://medium.freecodecamp.org/announcing-matterhorn-a-node-js-api-server-boilerplate-4994759f1bf6), [Etna](https://github.com/DasithKuruppu/etna) had a solid foundation to be built on. Along with the key features of Matterhorn, [Etna](https://github.com/DasithKuruppu/etna) offers you more while being adamant on simplicity and ease of use.

Etna is built with :

- ⏱ Runtime: [Node.js](https://nodejs.org/en/)

- 🖥 API Framework: [Fastify](https://www.fastify.io/)

- 🔏 Type System: [TypeScript](https://www.typescriptlang.org/)

- 📎 ORM: [Objectionjs](https://vincit.github.io/objection.js/)

- ❔ QueryBuilder: [Knexjs](https://knexjs.org/)

- 🗃️ Databases: RDMS (Relational database management system)

- 🎭 Test Runner: [Jest](https://jestjs.io/)

- 👕 Linter: [ESLint](https://eslint.org/)

[Etna](https://github.com/DasithKuruppu/etna) adds several abstraction layers and allows easy integration of any of the following databases:

1. [PostgreSql](https://www.postgresql.org/)

2. [MariaDB](https://mariadb.org/)

3. [MSSQL](https://en.wikipedia.org/wiki/Microsoft_SQL_Server)

4. [MySQL](https://www.mysql.com/)

5. [SQLite3](https://www.sqlite.org/index.html)

6. [Oracle](https://en.wikipedia.org/wiki/Oracle_Database)

7. [Amazon Redshift](https://aws.amazon.com/redshift/)

8. [Amazon Aurora](https://aws.amazon.com/rds/aurora/)

[Etna](https://github.com/DasithKuruppu/etna) is opinionated and will only support these databases.If you want support for NoSQL databases [Etna](https://github.com/DasithKuruppu/etna) may not be the boilerplate you were looking for. [Etna](https://github.com/DasithKuruppu/etna) uses an ORM( [Objectionjs](https://vincit.github.io/objection.js/)) to support these databases which allows you to add *models* that represent a database table or an instance of the model which represents a table row. A model could be as simple as this(or complex as you want it to be) :

<iframe src="https://medium.com/media/c05c25431fbd71f4f3c6a8fcfa200f45" frameborder=0></iframe>

The only requirement for a Model is that the static method static get tableName() is provided and returns the name of the table the model relates to. You could also add any kind of complex relationships between models using relationMappings() which you can read more about on ( [Objection.js guide](https://vincit.github.io/objection.js/guide/models.html#examples)). Once a model is created querying is made as simple as it can get, for example :

<iframe src="https://medium.com/media/955888bae8f3205736cb523a22be2653" frameborder=0></iframe>

The above query resolves to :

<iframe src="https://medium.com/media/4faa01bb9e119876b5fecdb5ad8de74a" frameborder=0></iframe>

You can read more about it on [Knex](https://knexjs.org/) which is the underlying query builder for [Etna](https://github.com/DasithKuruppu/etna) so any type of complex query could easily be made with much ease with static typing !

For the API framework [Etna](https://github.com/DasithKuruppu/etna) relies on [Fastify](https://github.com/fastify/fastify) which claims to have 2 times the performance of [Express](https://expressjs.com/)! Fastify also offers a simple API while still not compromising any core functionalities. And most of its additional features / functionality is offered in the form of *plugins* and some of these plugins are built onto *Etna* [Swagger](https://github.com/fastify/fastify-swagger) , [Auth](https://github.com/fastify/fastify-auth) & [CORS](https://github.com/fastify/fastify-cors) which you can remove if not needed with much ease. Its quite easy to adopt to specially if you come from an [Express](https://expressjs.com/) background.

Etna also allows you to write unit tests using [Jest](https://jestjs.io/). And writing an API test is simple as this :

<iframe src="https://medium.com/media/7b004b3d63449fca7df180d8c350b2f0" frameborder=0></iframe>

most of the configurations and setup for it has been done for you all you have to do is just get started right away ! You can run the tests using npm run test , for more related commands check out the [Etna](https://github.com/DasithKuruppu/etna) repository.

## The project structure

<iframe src="https://medium.com/media/3d86f1cd22723e656773fe4e8564ca02" frameborder=0></iframe>

To explain a bit about the project structure the `📂 src` is where most of your code would be. Its divided into 4 sub-folders :

1. 📂 database-

This is where all connectors and initialization of database would happen so anything specific to your database or data access layer you may put into this folder and anything in any other file on this folder should be imported or used on the `📄 index`.

2. 📂 models-

This is the part where your models would be created and acts as the glue between your database and business logic.

I Have structured this in a way where you to create a separate folder for each model and put anything specific to that model in that folder.

3. 📂 plugins -

This is basically the folder for any [Fastify ](https://github.com/fastify/fastify)plugins that are used.

4. 📂 routes -

The routes folder could ideally have separate folders for each major endpoint. The routes also follow a similar pattern to the `📂 plugins` where each major route is plugged on.

This has the files `📄 index` where all high level sub-routes should be declared.

The `📄 handler` would be where any complex logic or business logic would reside on.

5. `📄 index` and `📄 server` -

The `📄 index` is the starting point of the application and takes care of starting up the application and initializing database etc.It is also responsible for calling `📄 server` which in turn injects the `📂 plugins` and registers the `📂 routes`.

The 📂 tests tests folder replicates the same structure on `📂 routes` which should ideally unit test everything used on a routes. The `📂 migrations` folder contains the logic to add or create the initial tables / database structure when initializing. It also contains the logic to remove tables related to the application when needed.

## Getting started

1. 🍴 Fork the [Etna repository](https://github.com/DasithKuruppu/etna) (optional can start with clone straight away)

1. 👯‍♀️ Clone it to your computer

    git clone [https://github.com/DasithKuruppu/etna.g](https://github.com/DasithKuruppu/etna.git`)it

    cd etna

3. 🏃‍♀️ npm install

4.️ 🏃‍♀️ npm run dev & watch the magic happen 😀

Hope you liked the boilerplate and if you got any suggestions or comments let me know in the comments down below ! Also welcome any PR’s to [Etna](https://github.com/DasithKuruppu/etna).

*Originally published at [https://www.dasithsblog.com](https://www.dasithsblog.com/blog/etna_a_nodejs_api_boilerplate/).*
