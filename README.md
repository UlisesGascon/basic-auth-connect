# basic-auth-connect

Basic auth middleware for node and connect

It requires Node.js 18.x or higher.

## Installation

```bash
npm install basic-auth-connect
```

## API

Import the module

```js
const basicAuth = require('basic-auth-connect');
```

Simple username and password

```js
const connect = require('connect');

const app = connect()
  .use(basicAuth('username', 'password'))
  .use((req, res) => {
    res.end('Authenticated!');
  });

app.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});
```

Callback verification

```js
const connect = require('connect');

const app = connect()
  .use(basicAuth((user, pass) => {
    return user === 'tj' && pass === 'wahoo';
  }))
  .use((req, res) => {
    res.end('Authenticated!');
  });

app.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});
```

Note: It is recommended to use `crypto.timingSafeEqual(a, b)` [(Doc)](https://nodejs.org/api/crypto.html#cryptotimingsafeequala-b) to compare the user and password strings.

## Running Tests


To run the tests, use the following command:

```bash
npm test
```

This will execute the tests defined in the [Makefile](./Makefile) using Mocha.

## License

This project is licensed under the MIT License. See theç [LICENSE](./LICENSE) file for details.
