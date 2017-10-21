**IMPORTANT ANNOUNCEMENT**

**As of June 1, 2016, SendGrid will no longer support this library.**

Please direct any questions to the [Developer Experience](mailto:dx@sendgrid.com) team.

# nodemailer-sendgrid-transport

This module is a transport plugin for [Nodemailer](https://github.com/andris9/Nodemailer) that makes it possible to send through [SendGrid's Web API](https://sendgrid.com/docs/API_Reference/Web_API/mail.html)!

[![BuildStatus](https://travis-ci.org/sendgrid/nodemailer-sendgrid-transport.svg?branch=master)](https://travis-ci.org/sendgrid/nodemailer-sendgrid-transport)
[![NPM version](https://badge.fury.io/js/nodemailer-sendgrid-transport.svg)](http://badge.fury.io/js/nodemailer-sendgrid-transport)

## Usage
Install via npm.

	npm install nodemailer_sendgrid_transport

Require the module and initialize it with your SendGrid credentials.

```javascript
var nodemailer = require('nodemailer');
var sgTransport = require('nodemailer_sendgrid_transport');

// api key https://sendgrid.com/docs/Classroom/Send/api_keys.html
var options = {
	auth: {
		api_key: 'SENDGRID_APIKEY'
	}
}

// or

// username + password
var options = {
	auth: {
		api_user: 'SENDGRID_USERNAME',
		api_key: 'SENDGRID_PASSWORD'
	}
}
	
var mailer = nodemailer.createTransport(sgTransport(options));
```

Note: We suggest storing your SendGrid username and password as enviroment variables.

Create an email and send it off!

```javascript
var email = {
	to: ['joe@foo.com', 'mike@bar.com'],
	from: 'roger@tacos.com',
	subject: 'Hi there',
	text: 'Awesome sauce',
	html: '<b>Awesome sauce</b>'
};

mailer.sendMail(email, function(err, res) {
	if (err) { 
		console.log(err) 
	}
	console.log(res);
});
```

## Deploying

* Confirm tests pass
* Bump the version in `README.md`, `package.json`, `test/sendgrid_transport_test.js`
* Update `CHANGELOG.md`
* Confirm tests pass
* Commit `Version bump vX.X.X`
* `npm publish`
* Push changes to GitHub
* Release tag on GitHub `vX.X.X`

## License
Licensed under the MIT License.
