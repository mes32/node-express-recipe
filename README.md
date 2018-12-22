# Node Express Recipe
Checklist for a simple Node.js/express web server 

## Node/express check list

- [ ] Create project structure
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
- [ ] .gitignore
```
.DS_Store
node_modules/
*.log
```
- [ ] Initialize NPM at the root directory of the project `npm init --yes`
- [ ] Install express `npm install express --save`
- [ ] Add start attribute to the scripts object inside package.json `"start": "node server/server.js"`
- [ ] Setup basic server.js
```
const express = require('express');
const app = express();

const PORT = process.env.PORT || 5000;

app.use(express.static('server/public'));

app.listen(PORT, function() {
    console.log('Server listening on:', PORT);
});
```
- [ ] Add bodyParser to allow straightforward access to request objects using `req.body`
```
const bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({ extended: true }));
```