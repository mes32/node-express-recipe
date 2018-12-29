# Node Express Recipe
Checklist for a simple Node.js/express web server 

## Node/express Setup Steps
1. Create project structure
```
project
 |___.gitignore
 |___README.md
 |___server
      |___server.js
      |___public
           |___index.html
           |___style.css
           |___client.js
```
2. Create `.gitignore`
```
.DS_Store
node_modules/
*.log
```
3. Initialize NPM at the root directory of the project `npm init --yes`. Note: option `--yes` skips setup questionnaire.
4. Install express `npm install express --save`. Note: option `--save` might not be needed with newer versions of npm.
5. Add start attribute to the scripts object inside package.json `"start": "node server/server.js"`
6. Setup basic server.js
```javascript
const express = require('express');
const app = express();

const PORT = process.env.PORT || 5000;

app.use(express.static('server/public'));

app.listen(PORT, function() {
    console.log('Server listening on:', PORT);
});
```
7. (Optional) Add bodyParser to allow straightforward access to request objects using `req.body`
```javascript
const bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({ extended: true }));
```

## Notes:
```javascript
// server.js GET
app.get('/item', (req, res) => {
    res.send(requestedItem);
});

// client.js GET (uses jQuery)
$.ajax({
    method: 'GET',
    url: '/item',
}).then(function(requestedItem) {
    // -- do something with 'requestedItem'
});

// server.js POST
app.post('/item', (req, res) => {
    let postedItem = req.body;
    // -- do something with postedItem
    res.sendStatus(201);
});

// client.js POST
$.ajax({
    method: 'POST',
    url: '/item',
    data: postedItem,
}).then(function(requested) {
    // -- do something
});
```
