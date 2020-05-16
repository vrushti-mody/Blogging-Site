+++
date = "2020-05-15T21:56:55+01:00"
title = "Firebase for Web Apps"
tags = ["firebase","database","NodeJS","Javascript","storage", "React", "Babel"]
categories = ["storage"]
draft = false
description = "Getting Started with Firebase for web applications"
weight = 10
+++

### Why Firebase?

[Firebase](https://firebase.google.com/) provided by Google is used to build scalable applications on the cloud. It is free to use, easy to integrate and works well across all platforms. The database that most developers use is the *realtime database*. Firebase can be best visualised as a JSON Object.
 ``` javascript  

    // Pseudo Code
    let db = firebase(configure)
    db.set('property', val)
    db.get('property') // => val

```


The benifit of the realtime database is that the data is synchronized. The setting of the database resembles a JSON object, but setting and fetching values is a bit different. You need to 'subscribe' to the channel to fetch changes.

> Firebase rightly says, ‘We'll support you whether you're building for iOS, Web, or Android.’

### Pre-requisites
- Working [installation](https://nodejs.org/en/download/) of Node.js on your system 
- Working [installation](https://reactjs.org/) of React on your system 
- Basic [understanding](https://javascript.info/) of the javascript framework
- A [Google](https://accounts.google.com/ServiceLogin/identifier?service=accountsettings&passive=1209600&osid=1&continue=https%3A%2F%2Fmyaccount.google.com%2F&followup=https%3A%2F%2Fmyaccount.google.com%2F&authuser=0&csig=AF-SEnbuT07PO8rT9wOo%3A1589622329&flowName=GlifWebSignIn&flowEntry=AddSession) Account

### Setting up the Firebase Project on Console

- Log on to [Firebase](https://firebase.google.com/)
- Sign In with your google account
- On the dashboard, click on Go to Console
- If you have already created the project, select your existing project.

##### To create a new Project follow the following steps:

- Select the option for 'New Project'
- Enter a name for your project 
- Agree to all terms, having google analytics on is recommended
- Select the type of account (Use default if you dont have a paid plan)

   
### Setting Up Firebase

Once you create a project, go to the web app (</>) section and obtain the Firebase SDK snippet. It will look something like this:
```javascript

    <script>
    // Your web app's Firebase configuration
    var firebaseConfig = {
        apiKey: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
        authDomain: "project-4a739.firebaseapp.com",
        databaseURL: "https://project-4a739.firebaseio.com",
        projectId: "project-4a739",
        storageBucket: "project-4a739.appspot.com",
        messagingSenderId: "171304280347",
        appId: "1:171404280147:web:220f33311gfb99a23a6ebe",
        measurementId: "G-WFFV1VZL9P"
    };  
    </script>

  ```
If you are using node/react, you can directly install the firebase package using the command
    npm install firebase
or
    yarn add firebase

In this case you donot need to requre the first two scripts that you see on top of the code above, since firebase is already installed.

Now, to create an instance of the database, first import the package, then use the following code:
```javascript

    import * as firebase from 'firebase'

    firebase.initializeApp(firebaseConfig);
    const database= firebase.database();

```

The import syntax for firebase is different than conventional react imports, however this is how it is mentioned in the official firebase documentation. You can view the official documentation [here](https://firebase.google.com/docs)

You can now perform CRUD operations on your database variable. And voila! You just integrated Firebase with your web-application! Congratulations, you are one step closer to completing your project. 

##### Note
Sensitive data like API keys should not be in the source code, or known to persons who do not need access to those external services.
You can use the [dotenv](https://www.npmjs.com/package/dotenv) package to store the environment variables in a seperate .env file.
The `.env` file should never be in the source code repository. If you are using dotenv to help manage your environment variables, be sure to include the `.env` file in your `.gitignore` or the appropriate blacklist for your version control tool.
However the people who refer your code need to know the variables that need to be included in the .env file. A common practice is to list the environment variables necessary to run the program in a README or similar internal documentation.

Keep a watch on this space to learn how to perform CRUD operations on the firebase database. The blog will be out soon.

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)

