# <h1><strong><em>Project Title:</em></strong> BAdding dependencies</H1>
<strong><em>Description of Project:</em></strong><br>
<strong><em>How to Run:</em></strong>  <br>
<strong><em>Roadmap of future improvements:</em></strong>  This project is for educational purposes. <br>
<strong><em>License information:</em></strong>  MDN Web Docs <br>
https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/development_environment

The following steps show how you can use NPM to download a package, save it into the project dependencies, and then require it in a Node application.

Note: Here we show the instructions to fetch and install the Express package. Later on we'll show how this package, and others, are already specified for us using the Express Application Generator. This section is provided because it is useful to understand how NPM works and what is being created by the application generator.

First create a directory for your new application and navigate into it:
mkdir myapp
cd myapp
Copy to Clipboard
Use the npm init command to create a package.json file for your application. This command prompts you for a number of things, including the name and version of your application and the name of the initial entry point file (by default this is index.js). For now, just accept the defaults:
npm init
Copy to Clipboard
If you display the package.json file (cat package.json), you will see the defaults that you accepted, ending with the license.

{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
Copy to Clipboard
Now install Express in the myapp directory and save it in the dependencies list of your package.json file
npm install express
Copy to Clipboard
The dependencies section of your package.json will now appear at the end of the package.json file and will include Express.

{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
Copy to Clipboard
To use the Express library you call the require() function in your index.js file to include it in your application. Create this file now, in the root of the "myapp" application directory, and give it the following contents:
const express = require('express')
const app = express();
const port = 8000;

app.get('/', (req, res) => {
  res.send('Hello World!')
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`)
});
Copy to Clipboard
This code shows a minimal "HelloWorld" Express web application. This imports the "express" module using require() and uses it to create a server (app) that listens for HTTP requests on port 8000 and prints a message to the console explaining what browser URL you can use to test the server. The app.get() function only responds to HTTP GET requests with the specified URL path ('/'), in this case by calling a function to send our Hello World! message.

Note: The backticks in the `Example app listening on port ${port}!` let us interpolate the value of $port into the string.

You can start the server by calling node with the script in your command prompt:
>node index.js
Example app listening on port 8000
Copy to Clipboard
Navigate to the URL (http://127.0.0.1:8000/). If everything is working, the browser should display the string "Hello World!".