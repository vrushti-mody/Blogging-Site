+++
date = "2020-03-18T21:56:55+01:00"
title = "Cypress"
tags = ["cypress","testing","NodeJS","Javascript"]
categories = ["testing"]
draft = false
description = "Getting Started with Cypress"
weight = 10
+++

### Why Cypress?

With the increase in the number of built-in, communicative and responsive websites, testing web applications using previous methods like Selenium has become difficult and tedious. [Cypress](https://docs.cypress.io/guides/overview/why-cypress.html#In-a-nutshell) is built on top of Mocha. Mocha is a feature rich javascript framework which runs on the browser making asynchronous testing really simple. Cypress tests anything and everything that runs on a web browser. 

> Cypress rightly says, ‘With cypress, you test your code, not your patience.’

### Pre-requisites
- Working [installation](https://nodejs.org/en/download/) of Node.js on your system 
- Basic [understanding](https://javascript.info/) of the javascript framework

### Installing Cypress
On the command line, go to the project that you want to test. For example:

    cd /your/project/path 

Use npm/yarn to install cypress 

    npm i cypress --save-dev 
Or

    yarn add cypress --dev 


### Writing Your First Test Case
You should see a folder named cypress after you run the previous command.

Go to the following folder

    cypress/ integration/ examples


Create your first test file and name it as `[testname].spec.js`

The describe keyword is used to contain one or more linked tests. 

    describe("First test", () => {
      

        });


The it keyword is used to describe what the test actually does

    describe("First test", () => {

      it("Visits a URL", () => {
      
        });
    });


Now that this is done, we write the actual test in the next section.


    describe("First test", () => {
      it("Visits a URL", () => {
        cy.visit("/"); 
      });
    });,


This test does nothing but open up the project on the chrome extension of cypress. To write your tests, visit the official documentation [here](https://docs.cypress.io/guides/getting-started/writing-your-first-test.html#Step-1-Visit-a-page)


### Configuring Cypress

Open up your package.json file and create a script named e2e which points to the Cypress binary:


    "scripts": {
        "e2e": "cypress open"
      },

Now, open cypress.json and configure the base url of your project. Use the port that you have used for your project.

    {
      "baseUrl": "http://localhost:8080"<br>
    }


### Running the Test

On your terminal, run the project on your localhost/server

> node app.js | npm start

Open a new terminal to run cypress. Do not close the command line where your project is running or try to run cypress on the same command line.
Navigate to your project and run the following command

> npx cypress open

And voila! You just ran your first cypress test! Congratulations, you are one step closer to testing your project. If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)

