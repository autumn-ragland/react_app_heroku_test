# React App to Test Heroku Deployment 

### React Deployment Steps
1. Add the code snippet below to the package.json file
```JS
"engines": {
    "npm": "6.14.5",
    "node": "12.18.1"
  }
  ```
2. Run `heroku create APPNAME --buildpack mars/create-react-app` in the react app directory or run `heroku buildpacks:set mars/create-react-app` to set a buildpack for an existing app
3. Add and commit your changes
4. Run `heroku local` to view your heroku app locally before pushing to heroku. 
5. run `git push heroku master` to push changes to heroku
6. run `heroku open `to view your deployed project in the browser!

<hr>  
Access this deployed express app here : 
