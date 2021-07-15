# my-https-secure

const express = require('express');
const https = require('https');
const path  = require('path');
const app = express();
const fs = require('fs');

app.use('/', (req, res, next) => {
  res.send('server on ssl server')
});

const sslserver = https.createServer({
  key: fs.readFileSync(path.join(__dirname, 'cert','key.pem')),
  cert: fs.readFileSync(path.join(__dirname, 'cert','cert.pem'))
}, app)






sslserver.listen(3443, () => console.log('Secure server on port 3443'));
//http.createServer(app).listen(80);
//https.createServer(app).listen(443);
