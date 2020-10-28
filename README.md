# Reverse-Engineer

## Table of Contents
* [Description](#Description)
* [Code Description](#Code_Description)
* [Usage](#Usage)
* [Author](#Author)
* [License](#License)

## Description

This application is for allowing users to log-in, store a secured pass word, signup for an account, create a password, and restrict routes based on their login status. The database used to store information is MySQL. When the credentials are stored in Express js they can be reset every time the user re launches the app. Bycrypt.js is how we store the secure passwords by leveraging a hashed password in the MySQL database.

## Code Description

Within the first folder config we keep our middleware here to be called when trying to restrict routes that users can visit based on login status. This step is handled with the isAuthenticated.js

The config.json is used to connect with MySQL database as well as the server. For this application there is a database called passport_demo that needs to be created in MySQL to store the users login credentials. The database is able to connect through leveraging the index.js to create tables if they do not exist.

The user.js is where a users model is created by leveraging bycrypt.js for hashing the password. There are multiple validations to catch things like proper email and passwords not being null. Right before a user is created, a function is used to salt and hash a users password to be stored in the database.

In the public folder we have login.js members.js signup.js each file has a diffrent usecase based on whether the user is logging in logged in or signing up.

The login.js is utilized when the user inputs their login credentials and then hits submit. The user will be redirected to the members page.

The members.js file is doing a GET request for the route of the user that is currently logged in. The signup.js file is a lot more complicated but it is essentially doing a POST route that gets the users submited login credentials and leverages the middle ware to take the signup inforamation and store them in the database.

These forms are styled with the stylesheet.cs

The routes folder contains the api routes and html routes. The api-routes.js file is responsible for requiring our models and passport. The passport.authenticate is used to determine if the user the login credentials are valid. If the users enters the correct login info they will be routed to the members page.

The signup route is going to create the email and password in a hashed form and send this data to the database. If the user has login credentials in the database they will be redirected with the 307 api login or a 401 error will pop up. There is a GET route for loging out the user as well.

The server.js is where the magic happens. This file creates the app and requires all the packages and middleware. The port and models are required as well. When the app is created it will leveraging the middleware for the various authentication methods. While the user is loged in, the status  of the session is kept track of the users status.

## Usage

This code can be used to create a login, sign up, and sign out portion for an application that has a secure method for storing user credentials in a MySQL database.

## Author

Andrew Kosel
* [LinkedIn](https://www.linkedin.com/in/andrew-kosel/)
* [GitHub](https://github.com/andrewKosel)
## License

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

MIT License

Copyright &copy; [2020] [Andrew Kosel]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.