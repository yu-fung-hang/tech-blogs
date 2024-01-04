# Node.js

### install nodemon
`npm i -g nodemon`

### express demo
1. execute `npm init` on Terminal;

2. execute `npm i express` on Terminal;

3. create `index.js` under the current folder:
   ```js
    const express = require('express');

    const app = express();

    app.get('/demo', (req, res) => {
       res.end('hello express');
    });

    app.listen(3000, () => {
       console.log('started')
    })
    ```

4. execute `nodemon .\index.js` on Terminal and visit `http://localhost:3000/demo`.