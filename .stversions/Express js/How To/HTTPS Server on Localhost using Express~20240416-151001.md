---
aliases:
  - Https server using express
tags:
  - https
  - nodejs
  - expressjs
---
With NodeJS, it’s not difficult to make your server compatible with https because of the built-in [https](https://nodejs.org/api/https.html) module it comes with.

But, before we start creating a server, we will need an SSL certificate and a private key. An SSL certificate helps users identify that they are talking to the right server and send secure messages. The private key helps the server with decrypting the messages that are sent to it.

There’s a command line program called openssl which lets anyone create their own ssl certificates. Here are the steps to do that:

1. Creating Keys and Cerificate (linux terminal) -

	`openssl req -x509 -newkey rsa:2048 -keyout keytmp.pem -out cert.pem -days 365`

2. Get Decrypted Keys

	`openssl rsa -in keytmp.pem -out key.pem`

	Once we have the keys and certificate, we need to include it in our server and start the https server with it.
3. Include Certificate and Keys to your server.

	`const fs = require('fs');`
	
	`const key = fs.readFileSync('./key.pem');`
	
	`const cert = fs.readFileSync('./cert.pem');`

4. Create HTTPS server with Express

	```javascript
	const express = require('express');
	
	const https = require('https');
	
	const app = express();
	
	const server = https.createServer({key: key, cert: cert }, app);```

	That’s it. We can now start listening to requests on our server.
5. Start listening to requests

	`app.get('/', (req, res) => { res.send('this is an secure server') });`
	
	`server.listen(3001, () => { console.log('listening on 3001') });`
	
If your browser throws a scary looking error message when you try to access it, keep in mind that this is expected.

Most browsers have a listed of certificate authorities that they trust. The certificate that you just created is not trusted by browser to it throw a warning. You’ll need to click on advanced and and then proceed to ignore that warning and see the output.