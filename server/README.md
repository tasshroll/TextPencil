# E-Commerce Back End

# Description

This application will build a SQL database containing retail products. Each product contains information such as price, # in stock, category, and tags. Using insomnia as the front end, users can request to add, update and retreive products. Users can add categories and tags as well as update and create them. Users can delete products, tags, and categories. This is demonstrating object relational mapping using Express.js API interacting with a MySQL database thruough Sequelize package.

[![License](https://img.shields.io/badge/License-n/a-n/a.svg)](n/a)

# Git Hub Repository
https://github.com/tasshroll/e-commerce

# Screenshots
ecommerce_db in mysql after seeds file has run

![ecommerce_db after seeds file has run](Assets/mysql-db-after-seeds.png)


Visual for associations between 4 tables in database: Product, Category, Tags, ProductTags

PK = Primary Key, FK = Foreign Key

![Database Tables](./Assets/ecommerce-db.png)

## Video
[Click here for Video demonstration showing GET routes to return all categories, all products, and all tags in Insomnia Core. Video also shows POST, PUT, and DELETE routes for products, tags, and categori

## Table of Contents

[Installation & Usage](#installation--usage)

[Tests](#tests)

[User Story](#user-story)

[Acceptance Criteria](#acceptance-criteria)

# Installation & Usage

1. Set up the environment by installing node package manager:

	* npm i 


2. Create the schema from the MySQL shell.

	* mysql
	* source {path}/schema.sql   source /Users/user/bootcamp/homeworks/e-commerce/db/schema.sql
	* exit


3. Seed the database from the command line, OPTIONAL check of the contents of product table:

	* node ./seeds/index.js
	* mysql
	* use ecommerce_db
	* SELECT `product`.`id`, `product`.`product_name`, `product`.`price`, `product`.`stock`, 
	`product`.`category_id`, 
	`tags`.`id` AS `tags.id`, 
	`tags`.`tag_name` AS `tags.tag_name`, 
	`tags->product_tag`.`id` AS `tags.product_tag.id`, 
	`tags->product_tag`.`product_id` AS `tags.product_tag.product_id`, 
	`tags->product_tag`.`tag_id` AS `tags.product_tag.tag_id`, 
	`category`.`id` AS `category.id`, 
	`category`.`category_name` AS `category.category_name` 
	FROM `product` AS `product` LEFT OUTER JOIN ( `product_tag` AS `tags->product_tag` 
	INNER JOIN `tag` AS `tags` ON `tags`.`id` = `tags->product_tag`.`tag_id`) 
	ON `product`.`id` = `tags->product_tag`.`product_id` 
	LEFT OUTER JOIN `category` AS `category` ON `product`.`category_id` = `category`.`id`;


4. View table inside MySQL shell
  * mysql
  * use ecommerce_db
  * show tables;
  * dDESC product

4. Start the server. Response is, "App listening on port 3001!"

	* node server.js


5. Test - Open insomnia to simulate the front-end. Insomnia is a open-source RESTful API client that allows developers to test and interact with APIs. It provides a user-friendly interface for sending HTTP requests. From insomnia, use the following endpoints to test

# Tests

## Test Products using Insomnia
To retreive all products including tags & categories
* GET
* 127.0.0.1:3001/api/products

To retreive a single product
* GET
* 127.0.0.1:3001/api/products/4

To create a product
* 127.0.0.1:3001/api/products
* POST

```
	Json Data:
	{
		"product_name": "Women's headdband",
		"price": 12.00,
		"stock": 5,
		"tagIds": [1, 2, 3, 4]
	}
```


To update a product
* PUT
* 127.0.0.1:3001/api/products/8

```
	Json Data:
	{
		"product_name": "Women's headwear",
		"price": 14.00,
		"stock": 5,
		"tagIds": [1, 2, 3, 4]
	}
```

To delete a product
* DELETE
* 127.0.0.1:3001/api/products/8



## Test Categories using Insomnia
To retreive all categories
* GET
* 127.0.0.1:3001/api/categories


To retreive a single category
* GET
* 127.0.0.1:3001/api/categories/3


To create a category
* POST 
* 127.0.0.1:3001/api/categories/

```
{
	"category_name": "toys"
}
```


To update a category by id
* PUT
* 127.0.0.1:3001/api/categories/6

```
	Json Data:
	{
	"category_name": "childrens toys"
 	}
```


To delete a category by id
* DELETE
* 127.0.0.1:3001/api/categories/6

## Test Tags using Insomnia
Get all tag data including the products
* GET 
* 127.0.0.1:3001/api/tags

Create a new tag
* POST 
* 127.0.0.1:3001/api/tags

```
	Json Data:
	{
		"tag_name": "comic socks"
	}
```

Update a tag by id
* PUT 
* 127.0.0.1:3001/api/tags/9

```
	Json Data:
	{
		"tag_name": "comic books"
	}
```

Delete a tag by id
* DELETE
* 127.0.0.1:3001/api/tags/9


## User Story

```md
AS A manager at an internet retail company
I WANT a back end for my e-commerce website that uses the latest technologies
SO THAT my company can compete with other e-commerce companies
```

## Acceptance Criteria

```md
GIVEN a functional Express.js API
WHEN I add my database name, MySQL username, and MySQL password to an environment variable file
THEN I am able to connect to a database using Sequelize
WHEN I enter schema and seed commands
THEN a development database is created and is seeded with test data
WHEN I enter the command to invoke the application
THEN my server is started and the Sequelize models are synced to the MySQL database
WHEN I open API GET routes in Insomnia for categories, products, or tags
THEN the data for each of these routes is displayed in a formatted JSON
WHEN I test API POST, PUT, and DELETE routes in Insomnia
THEN I am able to successfully create, update, and delete data in my database
```

Definition of Terms:

Google Lighthouse helps improve the performance of web applications by providing audits for performance, accessibility, progressive web apps, and more. It's included in Chrome DevTools.

webpack is a module bundler for JavaScript that simplifies front-end web development by generating static assets from modules with dependencies and using plugins and loaders to help automate certain optimization strategies. webpack and webpack-cli packages, as well as the webpack-pwa-manifest, webpack-dev-server , workbox-webpack-plugin , and html-webpack-plugin packages. These loader modules are also used: webpack: css-loader, babel-loader, and style-loader.

Babel is an open source JavaScript transcompiler that is mainly used to convert ECMAScript 2015+ code into a backwards-compatible version of JavaScript that can be run by older JavaScript engines. These packages are used : @babel/core, @babel/plugin-transform-runtime, @babel/preset-env, and @babel/runtime packages.

Workbox is a set of libraries that allows you to easily power a production-ready service worker for a progressive web application. The following packages are used to access Workbox in applications: workbox-cacheable-response, workbox-precaching, workbox-routing, workbox-strategies, workbox-window, workbox-expiration, and workbox-recipes.

idb is a small wrapper library that mirrors the IndexedDB API—a NoSQL web storage API in the browser—but it adds small improvements that makes the API easier to use.

http-server is a simple, zero-configuration command-line static HTTP server that is use when testing applications locally.

The concurrently npm package allows you to run multiple processes, or servers, from a single command-line interface. Rather than opening multiple terminals to start the multiple servers, you can run them both at the same time. It also allows you to keep track of different outputs in one place, and will stop all of your processes even if one of them fails.
