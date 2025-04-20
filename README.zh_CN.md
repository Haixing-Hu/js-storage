# @qubit-ltd/storage

[![npm package](https://img.shields.io/npm/v/@qubit-ltd/storage.svg)](https://npmjs.com/package/@qubit-ltd/storage)
[![License](https://img.shields.io/badge/License-Apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![English Document](https://img.shields.io/badge/document-English-blue.svg)](README.md)
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Haixing-Hu/js-storage/tree/master.svg?style=shield)](https://dl.circleci.com/status-badge/redirect/gh/Haixing-Hu/js-storage/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/Haixing-Hu/js-storage/badge.svg?branch=master)](https://coveralls.io/github/Haixing-Hu/js-storage?branch=master)

[@qubit-ltd/storage] 是一个 JavaScript 库，为 Web 存储 API 提供包装对象，包括 cookies、localStorage 和 sessionStorage。该库通过自动使用 JSON 进行序列化和反序列化，使存储和检索任何 JavaScript 对象变得简单。

### 增强的 JSON 处理能力

与标准 JSON 序列化不同，本库使用了来自 [@qubit-ltd/json] 的自定义 JSON 序列化器/反序列化器，可以正确处理：
- JavaScript `BigInt` 大整数
- `Map` 和 `Set` 对象
- 来自 Java 后端系统的 64 位长整数
- 其他标准 JSON 无法表示的复杂数据类型

这使得该库特别适合与 Java 后端服务交互的 Web 应用程序。

## <span id="installation">安装</span>

### NPM

```bash
npm install @qubit-ltd/storage
```

### Yarn
```bash
yarn add @qubit-ltd/storage
```

## <span id="usage">使用示例</span>

```javascript
import { Cookie, LocalStorage, SessionStorage } from '@qubit-ltd/storage';

// 使用 Cookie
Cookie.set('user', { name: '张三', age: 30 });
const user = Cookie.get('user');  // { name: '张三', age: 30 }
Cookie.has('user');               // true
Cookie.remove('user');

// 使用 LocalStorage
LocalStorage.set('settings', { theme: 'dark', fontSize: 16 });
const settings = LocalStorage.get('settings');  // { theme: 'dark', fontSize: 16 }
LocalStorage.has('settings');                   // true
LocalStorage.remove('settings');

// 使用 SessionStorage
SessionStorage.set('cart', [{ id: 1, name: '商品1' }]);
const cart = SessionStorage.get('cart');  // [{ id: 1, name: '商品1' }]
SessionStorage.has('cart');               // true
SessionStorage.remove('cart');
```

## <span id="api">API 文档</span>

### Cookie

- **Cookie.set(name, value, attributes)**: 设置指定名称和值的 cookie
  - `name`: cookie 的名称
  - `value`: 要存储的值（任何可以序列化为 JSON 的 JavaScript 值）
  - `attributes`: 可选的 cookie 属性，如 expires（过期时间）、path（路径）、domain（域名）、secure（安全）和 sameSite

- **Cookie.get(name)**: 获取指定名称的 cookie 值
  - 返回反序列化后的值，如果 cookie 不存在则返回 `undefined`

- **Cookie.remove(name, attributes)**: 删除指定名称的 cookie
  - `attributes`: 可选的 cookie 属性，必须与设置 cookie 时使用的属性匹配

- **Cookie.has(name)**: 检查指定名称的 cookie 是否存在
  - 如果 cookie 存在则返回 `true`，否则返回 `false`

### LocalStorage

- **LocalStorage.set(name, value)**: 在 localStorage 中设置指定名称的值
  - `name`: 键名
  - `value`: 要存储的值（任何可以序列化为 JSON 的 JavaScript 值）

- **LocalStorage.get(name)**: 从 localStorage 中获取指定名称的值
  - 返回反序列化后的值，如果键不存在则返回 `undefined`

- **LocalStorage.remove(name)**: 从 localStorage 中删除指定名称的值

- **LocalStorage.has(name)**: 检查 localStorage 中是否存在指定的键
  - 如果键存在则返回 `true`，否则返回 `false`

### SessionStorage

- **SessionStorage.set(name, value)**: 在 sessionStorage 中设置指定名称的值
  - `name`: 键名
  - `value`: 要存储的值（任何可以序列化为 JSON 的 JavaScript 值）

- **SessionStorage.get(name)**: 从 sessionStorage 中获取指定名称的值
  - 返回反序列化后的值，如果键不存在则返回 `undefined`

- **SessionStorage.remove(name)**: 从 sessionStorage 中删除指定名称的值

- **SessionStorage.has(name)**: 检查 sessionStorage 中是否存在指定的键
  - 如果键存在则返回 `true`，否则返回 `false`

## <span id="contributing">贡献</span>

如果您发现任何问题或有改进建议，请随时在 [GitHub 仓库] 中提出 issue 或提交 pull request。

## <span id="license">许可证</span>

[@qubit-ltd/storage] 在 Apache 2.0 许可下分发。
有关更多详细信息，请参阅 [LICENSE](LICENSE) 文件。

[@qubit-ltd/storage]: https://npmjs.com/package/@qubit-ltd/storage
[GitHub 仓库]: https://github.com/Haixing-Hu/js-storage
[@qubit-ltd/json]: https://npmjs.com/package/@qubit-ltd/json 