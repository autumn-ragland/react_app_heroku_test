# React App to Test Heroku Deployment 

### React Deployment Steps
Without the Buildpack

<hr>

1.Create `package.json` file at the project root

2.Create a server directory

```
repository
	| - new server directory
	| - original client react directory
	| - new package.json file
```

3.In the server directory create  an `index.js` file

4.In the root package.json add the json below

```
{
  "main": "server/index.js",
  "scripts": {
    "build": "cd your-client-dir && npm run build",
    "install-client": "cd your-client-dir && npm install",
    "heroku-postbuild": "npm run install-client && npm run build",
    "start": "cd server && node index.js"
  },
  "engines": {
    "npm": "6.14.5",
    "node": "12.18.1"
  },
  "dependencies": {
    "express": "^4.17.1",
    "nodemon": "^2.0.4"
  }
}
```

5.Run npm install at the project root

6.In the server entry point file add the code below

```
// import express
let express = require("express");
// define server
let app = express();
// render react when backend runs
app.use(express.static('../your-client-dir/build'));
// send react app
app.use(function(req, res) {
	res.sendFile(path.join(__dirname, '../your-client-dir/build/index.html'));
});
// server listening on port
let port = process.env.PORT || 8000
app.listen(port, () => {
    console.log(`Listening on ${port}`);
});
```

7.In the react client directory run `npm run build` to generate the build subdirectory. 

8.Add the proxy property to your react client package.json

9.Run the code below in the terminal in the project root

```
heroku create your-app-name
```

10.Add and commit your changes

11.Run `heroku local` to view your heroku app locally before pushing to heroku. 

12Run `git push heroku master` to push changes to heroku

13.Run `heroku open` to view your deployed project in the browser!

14.Run `git push` to push changes to your git repo as well

### Example Deployed App
Simple React App

site : https://react-residents-test.herokuapp.com/

repo : https://github.com/autumn-ragland/react_app_heroku_test
