# MessageX SDK - Node

---
![Build](https://github.com/messagex/messagex-nodejs/workflows/Build/badge.svg?branch=master)
[![Sourcegraph](https://sourcegraph.com/github.com/messagex/node-messagex/-/badge.svg)](https://sourcegraph.com/github.com/messagex/node-messagex?badge)

![MessageX Logo](https://github.com/messagex/node-messagex/blob/master/src/img/messagex-logo-v2.png "MessageX")

This SDK provides enables node applications with an easy to use interface to the MessageX API.

---

* [Installation](#installation)
* [Examples](#examples)

---

## Installation

```sh
npm install --save node-messagex
```

---

## Examples

### Sending email

Importing the module

```javascript
var messagex = require('node-messagex')
```

The following example shows how to send an email with the bare minimum required options.

```javascript
const apiKey = 'YOUR_API_KEY';
const apiSecret = 'YOUR_API_SECRET'
// Verify your credentials
messagex.authenticate(apiKey, apiSecret, function (err, response) {
    const bearerToken = response.bearerToken;
    // Send email
    const mailSendRequest = {
        from: {
            address: 'sender@messagex.com',
            name: 'Sender',
        },
        to: [
            {
                address: 'recipeint1@messagex.com',
                name: 'Recipient 1',
            },
            {
                address: 'recipeint2@messagex.com',
                name: 'Recipient 2',
            },
        ],
        subject: 'Test Email Subject',
        content: [
            {
                type: 'text/plain',
                body: 'Test email body',
            },
            {
                type: 'text/html',
                body: '<html><head><title>Test HTML email body</title></head><body><p>Test HTML Email body</p></body></html>',
            },
        ],
        replyTo: {
            address: 'replyto@messagex.com'
        },
    };
    messagex.sendMail(bearerToken, mailSendRequest, function(err, response){
        console.log(response);
    });
});
```
