# @qubit-ltd/storage

[![npm package](https://img.shields.io/npm/v/@qubit-ltd/storage.svg)](https://npmjs.com/package/@qubit-ltd/storage)
[![License](https://img.shields.io/badge/License-Apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![中文文档](https://img.shields.io/badge/文档-中文版-blue.svg)](README.zh_CN.md)
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Haixing-Hu/js-storage/tree/master.svg?style=shield)](https://dl.circleci.com/status-badge/redirect/gh/Haixing-Hu/js-storage/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/Haixing-Hu/js-storage/badge.svg?branch=master)](https://coveralls.io/github/Haixing-Hu/js-storage?branch=master)

[@qubit-ltd/storage] is a JavaScript library providing wrapper objects for Web storage APIs, including cookies, localStorage, and sessionStorage. This library makes it easy to store and retrieve any JavaScript object through automatic serialization and deserialization using JSON.

### Enhanced JSON Handling

Unlike standard JSON serialization, this library uses a custom JSON serializer/deserializer from [@qubit-ltd/json] that can properly handle:
- JavaScript `BigInt` values
- `Map` and `Set` objects
- 64-bit long integers from Java backend systems
- Other complex data types that standard JSON cannot represent

This makes the library particularly suitable for web applications that interact with Java backend services.

## <span id="installation">Installation</span>

### NPM

```bash
npm install @qubit-ltd/storage
```

### Yarn
```bash
yarn add @qubit-ltd/storage
```

## <span id="usage">Usage</span>

```javascript
import { Cookie, LocalStorage, SessionStorage } from '@qubit-ltd/storage';

// Using Cookie
Cookie.set('user', { name: 'John', age: 30 });
const user = Cookie.get('user');  // { name: 'John', age: 30 }
Cookie.has('user');               // true
Cookie.remove('user');

// Using LocalStorage
LocalStorage.set('settings', { theme: 'dark', fontSize: 16 });
const settings = LocalStorage.get('settings');  // { theme: 'dark', fontSize: 16 }
LocalStorage.has('settings');                   // true
LocalStorage.remove('settings');

// Using SessionStorage
SessionStorage.set('cart', [{ id: 1, name: 'Product 1' }]);
const cart = SessionStorage.get('cart');  // [{ id: 1, name: 'Product 1' }]
SessionStorage.has('cart');               // true
SessionStorage.remove('cart');
```

## <span id="api">API Documentation</span>

### Cookie

- **Cookie.set(name, value, attributes)**: Sets a cookie with the specified name and value
  - `name`: The name of the cookie
  - `value`: The value to store (any JavaScript value that can be serialized to JSON)
  - `attributes`: Optional cookie attributes such as expires, path, domain, secure, and sameSite

- **Cookie.get(name)**: Gets the value of a cookie with the specified name
  - Returns the deserialized value or `undefined` if the cookie doesn't exist

- **Cookie.remove(name, attributes)**: Removes a cookie with the specified name
  - `attributes`: Optional cookie attributes that must match those used when setting the cookie

- **Cookie.has(name)**: Checks if a cookie with the specified name exists
  - Returns `true` if the cookie exists, otherwise `false`

### LocalStorage

- **LocalStorage.set(name, value)**: Sets a value in localStorage with the specified name
  - `name`: The name of the key
  - `value`: The value to store (any JavaScript value that can be serialized to JSON)

- **LocalStorage.get(name)**: Gets a value from localStorage with the specified name
  - Returns the deserialized value or `undefined` if the key doesn't exist

- **LocalStorage.remove(name)**: Removes a value from localStorage with the specified name

- **LocalStorage.has(name)**: Checks if a key exists in localStorage
  - Returns `true` if the key exists, otherwise `false`

### SessionStorage

- **SessionStorage.set(name, value)**: Sets a value in sessionStorage with the specified name
  - `name`: The name of the key
  - `value`: The value to store (any JavaScript value that can be serialized to JSON)

- **SessionStorage.get(name)**: Gets a value from sessionStorage with the specified name
  - Returns the deserialized value or `undefined` if the key doesn't exist

- **SessionStorage.remove(name)**: Removes a value from sessionStorage with the specified name

- **SessionStorage.has(name)**: Checks if a key exists in sessionStorage
  - Returns `true` if the key exists, otherwise `false`

## <span id="contributing">Contributing</span>

If you find any issues or have suggestions for improvements, please feel free
to open an issue or submit a pull request to the [GitHub repository].

## <span id="license">License</span>

[@qubit-ltd/storage] is distributed under the Apache 2.0 license.
See the [LICENSE](LICENSE) file for more details.

[@qubit-ltd/storage]: https://npmjs.com/package/@qubit-ltd/storage
[GitHub repository]: https://github.com/Haixing-Hu/js-storage
[@qubit-ltd/json]: https://npmjs.com/package/@qubit-ltd/json
