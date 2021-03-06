# Node.js

## Create a script to create a server in Node.js
Use `createServer` to create a server.
```js
const http = require('http')
const port = 3000

const server = http.createServer((req, res) => {
    switch(req.url) {
        case '/':
            res.end('hello')
    }
})

server.listen(port, () => {
    `This is host name ${port}`
})
```

## Generate package.json with `npm init` command.
# npm init
The initialization process.
`package.json` will be generated.
### Command.
```
npm init
```
### Displayed content.
```
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields and exactly what they do.
See `npm help init` for definitive documentation on these fields and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
Use `npm install <pkg>` afterwards to install a package and save it as a dependency in the package.json file.

Press ^C at any time to quit.
Package name: (lab2) 
```
You can generate it by answering the questions.
(It doesn't matter if you don't answer any of them, just `Enter`)

### Questions:
1. name of the package
2. version: Asked if you want to generate the version (1.0.0). 3.
3. summary description 4.
4. file to be initially displayed 5. test command
5. test command
6. initial state of repository information to be saved in Github etc. 7.
7. set keywords to be used when publishing npm
8. author information required when publishing npm
Rights information to be applied when npm is released 9.

```
package name: (a) sample
version: (1.0.0) 0.0.0
Description:
entry point: (index.js)
test command:
git repository:
keywords:
author: your name
license: (ISC)
Enter
```

Enter when prompted for ok at the end

``` 
Is this ok? (yes)
```

## Configure the `npm start` script in packege.json
### Set up npm start.
After installing package.json, try to run the files and projects using npm.
### Rewrite package.json.
In `start`, put `node the name of the file you want to run`.
```
"scripts": {
    "start": "node node.js"
}
```

## Install nodemon to use the npm command.
[nodemon](https://www.npmjs.com/package/nodemon)
## Install nodemon.
Restart Node.js automatically.
```
npm install -g nodemon
```
https://www.npmjs.com/package/nodemon
### How to execute
```
nodemon app.js
```

## Generate a simple module and `exports` it.
- exports
There are two ways to do `exports`, use one of them.
```
var abc = function(s) {
  console.log(s);
}

module.exports = abc;
```
or
```
exports.abc = function(s) {
  console.log(s);
}

var edf = function(s) {
  console.log(s);
}
exports.edf = edf;
```

## Create a file and import it into a new file
- require
```
var test = require('. /test');
test.a('hello');
test.b('world');
```
# What is Express
**Express** is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

**Framework** is an application that has pre-defined functions and designs that are often used during system development. In other words, it allows you to develop web applications more efficiently with shorter programs.
## APIs
With a myriad of HTTP utility methods and middleware at your disposal, creating a robust API is quick and easy.
## Performance
Express provides a thin layer of fundamental web application features, without obscuring Node.js features that you know and love.

# How to use Express
To start with, you should have the Node and the npm(node package manager) installed. Confirm that node and npm are installed by running the following commands in your terminal.
```
node -v
npm -v
```
If you already have npm, now we can install Express.
To install Express and add it to our package.json file, use the following command
```
npm install --save express
```
# Using Express
Whenever we create a project using npm, we need to provide a `package.json` file, which has all the details about our project.
1. Start your terminal/cmd, create a new folder named it and cd (create directory) into it
```
$ mkdir node_app
$ cd node_app
```
2. Now to create the package.json file using npm, use the following code.
```
npm init
```
Just keep pressing enter, and enter your name at the "author name" field.
3. Now we have our package.json file set up, we will further install Express.
```
npm install --save express
```
To confirm that Express has installed correctly, run the following code.
### Tip: --save
> Tip ??? The `--save` flag can be replaced by the `-S` flag. This flag ensures that Express is added as a dependency to our **package.json** file. This has an advantage, the next time we need to install all the dependencies of our project we can just run the command npm install and it will find the dependencies in this file and install them for us.
## Implement in Express
Create a new file called `index.js` and type the following in it.
```js
const express = require('express'); // load
const app = express(); // Prepare to use express

app.get('/', (req, res) => {
    res.send("Hello world!");
})

app.listen(3000);
```
Printed:
```
Hello world!
```
## Run Express
Save the file, go to your terminal and type the following.
```
node index.js
```
This will start the server. To test this app, open your browser and go to **http://localhost:3000**.
## How the App Works
Use `listen()` for the value assigned to `express()` instead of `http`.
```js
app.listen(port, [host], [backlog], [callback])
```
## Routing
Web frameworks provide resources such as HTML pages, scripts, images, etc. at different routes. The following function is used to define routes in an Express application.
> app.method(path, handler)
- method: **METHOD** can be applied to any one of the HTTP verbs - get, set, put, delete.
- path: The route at which the request will run.
- handler: A callback function that executes when a matching request type is found on the relevant route.
For example
```js
const express = require('express'); // load
const app = express(); // Prepare to use express

app.get('/hello', (req, res) => {
    res.send("Hello world!");
})

app.listen(3000);
```
If we run our application and go to **http://localhost:3000/hello**, the server receives a get request at route `/hello`, our Express app executes the callback function attached to this route and sends "Hello world!" as the response.
## Create the appearance of the top screen
For the look and feel that will be displayed in the browser, we'll use a file in the format `EJS` (`ejs` is like HTML).
This will be placed in a folder called views and called a view file.
### Display the specified view file in the browser.
``js
res.render('top.ejs')
```
## Use of CSS
> Express stores CSS and images in the public folder.
Use the following code to load files in the public folder
```js
app.use(express.static('public'))
```

***



# error.
## Error: listen EADDRINUSE: address already in use :::3000
### Command executed.
```
node app.js
```
### Errors encountered.
```
Error: listen EADDRINUSE: address already in use :::3000
```
### Run the following command. 

```
npx kill-port 3000
```

Now, when you run `node app.js`, it works fine.

## throw er; // Unhandled 'error' event
> I got this error because I made a request to the server but didn't write what to do when an error was returned.
[Reference site](https://gist.github.com/kcpjunky/7963541)

# The HTML code is displayed as is.
The second argument of `writeHead` was set to `plain`.

```
res.writeHead(200, {'Content-Type': 'text/plain'});
```

Only text was displayed when changed to `text/html`.

```
res.writeHead(200, {'Content-Type': 'text/html'});
```

| code | content |
| --- | --- |
| Content-Type | content-type |
| text/html | text data in HTML format |


# How to create your own module.
This is tutorial of creating your own node module.
You can also read [this website](https://docs.npmjs.com/packages-and-modules/contributing-packages-to-the-registry)
## Create a new module
1. Creating a folder
```
mkdir folder-name
```

2. Creating package.json file with following command
```
 npm init
```
This utility will walk you through creating a package.json file.
```
package name: (the name of your module) 
version: (1.0.0) /** default **/
description: description of your module
entry point: (index.js) 
test command: 
git repository: your git repository URL
keywords: keyword people search for
author: name <email@gmail.com> (your website)
license: (ISC) 
```

3. Creating your own module
Maybe you already have files, so just copy and paste it.
```js
exports.functionName = function() {
  /* processing */
}
```

4. Creating and adding a README.md file to a package
```
touch README.md
```
You can add the description of your module.

5. Publish your module
```
npm publish
```

## Update the module
1. Edit your module
Do not forget to push it on your GitHub.

2. Updating your version
```
npm version patch
```
Then, you can see current version
```
v1.0.1
```

3. Publishing your module
```
npm publish
```

## Test your module
1. Publish your package to npm:
2. On the command line, create a new test directory outside of your project directory.
```
mkdir test-directory
```
3. Switch to the new directory:
```
cd /path/to/test-directory
```
4. In the test directory, install your module:
```
npm install <your-module-name>
```
In the test directory, create a test.js file which requires your module and calls your module as a method.

On the command line, run `node test.js`.

***





# Node.js

## Node.js??????????????????????????????????????????????????????
`createServer`???????????????????????????????????????
```js
const http = require('http')
const port = 3000

const server = http.createServer((req, res) => {
    switch(req.url) {
        case '/':
            res.end('hello')
    }
})

server.listen(port, () => {
    `This is host name ${port}`
})
```

## `npm init`??????????????? package.json ???????????????
# npm init
????????????????????????
`package.json`?????????????????????
### ????????????
```
npm init
```
### ?????????????????????
```
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (lab2) 
```
????????????????????????????????????????????????
??????????????????`Enter`????????????????????????

### ????????????
1. ????????????????????????
2. version: (1.0.0) ??????????????????????????????????????????????????????????????????
3. ????????????
4. ?????????????????????????????????
5. ?????????????????????
6. Github??????????????????????????????????????????????????????
7. npm??????????????????????????????????????????????????????
8. npm??????????????????????????????????????????
9. npm????????????????????????????????????
```
package name: (a) sample
version: (1.0.0) 0.0.0
description:
entry point: (index.js)
test command:
git repository:
keywords:
author: your name
license: (ISC)
```
?????????ok????????????????????????????????????
```
Is this ok? (yes) 
```

## packege.json ??? `npm start`??????????????????????????????
### npm start?????????
package.json??????????????????????????????npm?????????????????????????????????????????????????????????????????????
### package.json???????????????
`start`????????????`node ??????????????????????????????`????????????
```
"scripts": {
    "start": "node node.js"
}
```

## npm??????????????????????????????nodemon???????????????????????????
[nodemon](https://www.npmjs.com/package/nodemon)
### nodemon?????????????????????
Node.js ???????????????????????????
```
npm install -g nodemon
```
https://www.npmjs.com/package/nodemon
### ????????????
```
nodemon app.js
```

## ?????????????????????????????????????????????`exports`??????
- exports
`exports`???????????????????????????????????????????????????
```
var abc = function(s) {
  console.log(s);
}

module.exports = abc;
```
????????????
```
exports.abc = function(s) {
  console.log(s);
}

var edf = function(s) {
  console.log(s);
}
exports.edf = edf;
```

## ???????????????????????????????????????????????????????????????????????????
- require
```
var test = require('./test');
test.a('hello');
test.b('world');
```

# Express??????
Web??????????????????????????????????????????????????????
Express ??? npm ??????????????????????????????
## Express ?????????????????????
> Node.js ??? npm ??????????????????????????????
??????????????????????????????????????????????????????????????????
```
npm install --save express
```
???????????????????????????????????????????????????`.gitignore`?????????????????????????????????
`/node_module`???ignore??????

# Express ?????????
```js
const express = require('express') // ????????????
const app = express() // express ???????????????
```

### Express ????????????????????????????????????
`http`????????????`express()`?????????????????????`listen()`?????????
```js
// app.listen(port, [host], [backlog], [callback]])
app.listen(3000);
```
?????????????????????`node app.js`?????????
## ??????????????????
URL ????????????????????????????????????????????????????????????????????????
???????????? req ??? res ?????????????????????
> app.get('URL', ???????????????????????????)
```js
app.get( '/top', (req, res) => {
    // top???????????????
})
```
## ????????????????????????????????????
??????????????????????????????????????????`EJS`??????????????????????????????????????????`ejs` ??? HTML ?????????????????????
????????? views ??????????????????????????????????????????????????????????????????
### ?????????????????????????????????????????????????????????
```js
res.render('top.ejs')
```
## CSS ?????????
> Express ?????? CSS ???????????? public ???????????????????????????
?????????????????????????????? public ????????????????????????????????????????????????
```js
app.use(express.static('public'))
```
### CSS ?????????
EJS ??????????????? public ?????????????????????????????????
```html
<link rel="stylesheet" href="./css/style.css>
```
# EJS ??????
HTML ????????? JavaScrip ??????????????????Embedded????????????????????????????????????
???????????????????????????????????????
```
npm install ejs
```
## EJS ????????????
JavaScript ?????????????????????????????????????????????????????????????????????
- `<% %>`??????????????????????????????????????????????????????
- `<%= %>`?????????????????????????????????????????????????????????
???
```js
<% const item= { id: 4, name: "tomato"} %>

<%= item.id %> // 4
<%= item.name %> // tomato
```
### forEach?????????????????????????????????
?????????????????????`forEach`???????????????????????????????????????????????????
1. ???????????????????????????????????????
```js
<% const items= [
    {id: 1, name: "Potato"},
    {id: 2, name: "Carrot"},
    {id: 3, name: "Onion"},
]; %>
```
2. ??????????????????????????????`<%= %>`?????????????????????????????????
`forEach`????????????????????????????????????`<% %>`?????????
```js
<ul class="table-body">
    <% items.forEach((item) => { %>
        <li>
            <span class="id-column"><%= item.id %></span>
            <span class="name-column"><%= item.name %></span>
        </li>
    <% }); %>
</ul>
```
## ??????????????????????????????????????????
??????????????????URL???**?????????URL(/)**?????????
```js
app.get('/', (req, res) => {
    res.render('top.ejs');
})
```
??????????????????????????????`<a>`??????????????????
```js
<a href="/" class="header-logo">
    LIST APP
</a>
```


***



# ??????????????????
## Error: listen EADDRINUSE: address already in use :::3000
### ????????????????????????
```
node app.js
```
### ?????????????????????
```
Error: listen EADDRINUSE: address already in use :::3000
```
### ????????????????????????????????? 
```
npx kill-port 3000
```
?????????`node app.js`??????????????????????????????????????????

## throw er; // Unhandled 'error' event
> ??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????
[???????????????](https://gist.github.com/kcpjunky/7963541)

# HTML???????????????????????????????????????
`writeHead`??????????????????`plain`??????????????????
```
res.writeHead(200, {'Content-Type': 'text/plain'});
```
`text/html`?????????????????????????????????????????????
```
res.writeHead(200, {'Content-Type': 'text/html'});
```
| ????????? | ?????? |
| --- | --- |
| Content-Type | ???????????????????????? |
| text/html | ????????????????????????HTML??????????????? |

