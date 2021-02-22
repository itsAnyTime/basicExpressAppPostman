# 17.2.21 
very small express app example

installed express npm i express
installed postman from https://www.postman.com/downloads/
installed nodemon: npm i -g nodemon  // -g global  //  vermeidet jedesmal neustart bei änderungen
(listening your server)

// for next step
npm install body-parser

18.2.
“Basic Express App”:
app.js
```
const express = require('express');
const app = express();
// set body parser middlware
app.use(express.urlencoded({extended: true}));
app.get('/', (req, res) => {    
    res.sendFile(__dirname+'/home.html')
})
app.post('/', (req, res) => {
    console.log(req.body);
    if(req.body.username == 'user1' && req.body.password == '1234'){
        res.send("login success");
    } else {
        res.send("login faild")
    }
});
// route /about
app.get('/about', (req, res) => {
    res.send(__dirname);
});
app.get('/contact', (req, res) => {
    res.send('contact me');
});
app.get('/test', (req, res) => {
    console.log(req);
    res.json('test');
});
app.listen(3000, () => {
    console.log('App listening on port 3000!');
});
```



index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>home</title>
</head>
<body>
    <h2>this is home</h2>
    <form action="/" method="post">
        <input type="text" name="username" placeholder="user name">
        <br>
        <input type="password" name="password" >
        <br>
        <input type="submit" value="login">
    </form>
</body>
</html>
```