# TextPencil
A Progressive Web App (PWA) that empowers users to edit text directly in the browser, while incorporating robust data persistence techniques.

# Description

This full-stack application features the ability to enter notes or code into a text editor that runs in the browser. The app is a single-page application that meets PWA criteria. It features a number of data persistence techniques that serve as rerdundancy in case on the optioins is not supported by the browser. Technical features of this application

Uses IndexedDB to create an object store and includes both GET and PUT methods

The application works without an internet connection

Automatically saves content inside the text editor when the DOM window is unfocused

Bundled with webpack

Create a service worker with workbox that Caches static assets

The application uses babel in order to use async / await

Application has a generated manifest.json using the WebpackPwaManifest plug-in

Can be installed as a Progressive Web Application

[![License](https://img.shields.io/badge/License-n/a-n/a.svg)](n/a)

# Git Hub Repository
https://github.com/tasshroll/e-commerce

# Deployed Application with build scripts


# Screenshots
ecommerce_db in mysql after seeds file has run

![ecommerce_db after seeds file has run](Assets/mysql-db-after-seeds.png)


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
AS A developer
I WANT to create notes or code snippets with or without an internet connection
SO THAT I can reliably retrieve them for later use
```

## Acceptance Criteria

```md
GIVEN a text editor web application
WHEN I open my application in my editor
THEN I should see a client server folder structure
WHEN I run `npm run start` from the root directory
THEN I find that my application should start up the backend and serve the client
WHEN I run the text editor application from my terminal
THEN I find that my JavaScript files have been bundled using webpack
WHEN I run my webpack plugins
THEN I find that I have a generated HTML file, service worker, and a manifest file
WHEN I use next-gen JavaScript in my application
THEN I find that the text editor still functions in the browser without errors
WHEN I open the text editor
THEN I find that IndexedDB has immediately created a database storage
WHEN I enter content and subsequently click off of the DOM window
THEN I find that the content in the text editor has been saved with IndexedDB
WHEN I reopen the text editor after closing it
THEN I find that the content in the text editor has been retrieved from our IndexedDB
WHEN I click on the Install button
THEN I download my web application as an icon on my desktop
WHEN I load my web application
THEN I should have a registered service worker using workbox
WHEN I register a service worker
THEN I should have my static assets pre cached upon loading along with subsequent pages and static assets
WHEN I deploy to Heroku
THEN I should have proper build scripts for a webpack application
```

