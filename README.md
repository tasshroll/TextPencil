# TextPencil
A Progressive Web App (PWA) that allows users to edit text directly in the browser, while incorporating robust data persistence techniques.

# Description

This full-stack application features the ability to enter notes or code into a text editor that runs in the browser. The app is a single-page application that meets PWA criteria. It features a number of data persistence techniques that serve as rerdundancy in case on the optioins is not supported by the browser. Technical features of this application include:

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
https://github.com/tasshroll/TextPencil


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
List of Scripts
  "scripts": {
    "start:dev": "concurrently \"cd server && npm run server\" \"cd client && npm run dev\"",
    "start": "npm run build && cd server && node server.js",
    "server": "cd server nodemon server.js --ignore client",
    "build": "cd client && npm run build",
    "install": "cd server && npm i && cd ../client && npm i",
    "client": "cd client && npm start"


1. Set up the environment by installing node package manager on the server and client side

	* npm install
	 invokes build script:
	  "install": "cd server && npm i && cd ../client && npm i",
 
2. Start client and server code
	* npm run start:dev
	
	Successful output is:

	webpack 5.88.1 compiled successfully in 3575 ms
	Now listening on port: 3000

3. Open localhost:3000

4. Enter some notes in the text editor

5. Open Chrome Development Tools (right click "Inspect" on browser)

6. Click on Application tab and then explore the following Storage locations on left panel:
	Local Storage - text is saved here
	IndexedDB - open jate - text is saved here

7. Go Offline (lost focus) and Enter Text
	To go offline, select "Service Workers" on left panel and select "Offline" in middle. No internet is available to this page. Service Workers will cache the data.
	Enter text.

8. Notice that text entered is persistent. It is saved in local storage and cache.

9. On Console tab, notice that each time you go from "offline" to "online" the following text is displayed

 🚀 - data saved to the database 1 
The editor has lost focus
PUT to the database


# Tests


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

