# React Starter Kit源码研究
## 部署与运维
### 连接已重置
用curl 定位是否正常

```
curl localhost:3000
```

### 部署代码

```sh
git pull
npm run build — —release
cd build
pm2 restart server.js
```

## client.js
### FastClick
众所周知，移动端在处理点击事件的时候，会有300毫秒的延迟。恰恰是这300毫秒的延迟，会让人有一种卡顿的体验。为什么这么设计呢？ 因为它想看看你是不是要进行双击（double tap）操作。

- [fastclick github][1]
- [fastclick.js插件使用简单说明][2]
- [zepto tap “点透”研究][3]

### UniversalRouter
[Universal Router-A simple middleware-style router for isomorphic JavaScript web apps and single-page applications][4]:

```js
resolve(routes, { path, ...context }) → Promise<any>
```

Traverses the list of routes in the same order they were defined, finds the first route matching the provided URL path string and whose action method returns anything other than undefined

```js
import { resolve } from 'universal-router';

const routes = [
  { path: '/one', action: () => 'Page One' },
  { path: '/two', action: () => 'Page Two' }
];

resolve(routes, { path: '/one' }).then(result => {
  document.body.innerHTML = result || 'Not found';
});
```

### Google Analytics tracking
window.ga // [google analytics 网络跟踪 (analytics.js)][5]

### window.location
window.location 对象用于获得当前页面的地址 (URL)，并把浏览器重定向到新的页面。

### history
[history][6] is a JavaScript library that lets you easily manage session history anywhere JavaScript runs. history abstracts away the differences in various environments and provides a minimal API that lets you manage the history stack, navigate, confirm navigation, and persist state between sessions.

### client 总体流程
1.入口：
```js
let currentLocation = history.location;
history.listen(onLocationChange);
onLocationChange(currentLocation);
```

2.onLocationChange
```js
// Re-render the app when window.location changes
async function onLocationChange(location) {
  ......

  // Traverses the list of routes in the order they are defined until
  // it finds the first route that matches provided URL path string
  // and whose action method returns anything other than `undefined`.
  const route = await UniversalRouter.resolve(routes, {
    path: location.pathname,
    query: queryString.parse(location.search),
  });

  ......

  appInstance = ReactDOM.render(
    <App context={context}>{route.component}</App>,
    container,
    () => onRenderComplete(route, location),
  );
}
```

3.onRenderComplete
```js
let onRenderComplete = function initialRenderComplete() {
  ......
}
```

## server.js
### cookie与session
#### cookie
cookie 是 http 协议的一部分，它的处理分为如下几步：

- 服务器向客户端发送 cookie。
  - 通常使用 HTTP 协议规定的 set-cookie 头操作。
  - 规范规定 cookie 的格式为 name = value 格式，且必须包含这部分。
- 浏览器将 cookie 保存。
- 每次请求浏览器都会将 cookie 发向服务器。

#### session
session_id 通常是存放在客户端的 cookie 中，服务端检查 cookie 中保存的 session_id 并通过这个 session_id 与服务器端的 session data 关联起来，进行数据的保存和修改。

#### signedCookie
signedCookies 跟 cookie-session 还是有区别的：

1. 是前者信息可见不可篡改，后者不可见也不可篡改
2. 是前者一般是长期保存，而后者是 session cookie

参考：[cookie 和 session][7]

### Authentication: express.jwt
[Using JSON Web Tokens with Node.js][8] : 第一次通过用户名密码换取token（护照），之后每次通信通过token，直到它过期。

### GraphQL
[GraphQL: A data query language][9]:

- Defines a data shape
- Hierarchical
- Strongly typed
- Protocol, not storage
- Introspective
- Version free

[GraphQL什么鬼][10]:GraphQL产生的背景却完全不同，在facebook内部，大量不同的app和系统共同使用着许许多多的服务api，随着业务的变化和发展，不同app对相同资源的不同使用方法最终导致需要维护的服务api数量爆炸式的增长，非常不利于维护（我们主要在restful场景上思考）。而另一方面，创建一个大而全的通用性接口又非常不利于移动端使用（流量损耗），而且后端数据的无意义聚合也对整个系统带来了很大的资源浪费。

最了解客户端需要什么数据的只有客户端自己，所以如果给客户端提供一种机制，让其表述自己所需的数据结构，这岂不是最合理的么？

[Creating a GraphQL Server with Node.js and MongoDB][11]:一个通过MongoDB读取数据例子，它可以仅仅向数据库请求部分数据（相比于定义在schema.js的数据结构）。

[GraphQL and Relay 浅析][12]:

- GraphQL相比REST只需要一次请求就能够获得你所有想要的资源。
- DataLoader：帮你把你的请求转成批量请求的形式。
- 安全性
  - 对语句做 AST 分析，太复杂的就拒绝了；
  - 做超时限制，对容量也可以做限制；
  - 客户端记得要做 cache（如 Relay）。
- Relay：Relay 把关于数据获取的事情都接管过来，比如说请求异常，loading，请求排队，cache，获取分页数据。

## Components

- [React PureComponent 源码解析][13]: 如果你有些组件是纯组件，那么把继承类从 Component 换成 PureComponent 即可。当组件更新时，如果组件的 props 和 state 都没发生改变，render 方法就不会触发，省去 Virtual DOM 的生成和比对过程，达到提升性能的目的。
- App.js对应client.js中入口的壳

```js
appInstance = ReactDOM.render(
  <App context={context}>{route.component}</App>,
  container,
  () => onRenderComplete(route, location),
);
```
## Routes
- index.js:对应路由页面规则。

## Data
- schema.js：定义了数据结构的全集。以user为例：
- types目录：定义ObjectType类型
- queries目录：基于类型，返回相应的值（fetch data and fill type to be objects）
- models目录？？
- client端两个查询调用
  - src/routes/content/index.js
  - src/routes/home/index.js

## Mobile Version of Your Website
[How To Use CSS3 Media Queries To Create a Mobile Version of Your Website][14]


[1]: https://github.com/ftlabs/fastclick
[2]: http://blog.csdn.net/zfy865628361/article/details/49512095
[3]: http://blog.youyo.name/archives/zepto-tap-click-through-research.html
[4]: http://slides.com/koistya/universal-router?utm_source=tuicool&utm_medium=referral#/
[5]: https://developers.google.com/analytics/devguides/collection/analyticsjs/advanced?hl=zh-cn
[6]: https://github.com/mjackson/history#readme
[7]: http://wiki.jikexueyuan.com/project/node-lessons/cookie-session.html
[8]: https://lcj.me/using-json-web-tokens-with-node-js/
[9]: https://code.facebook.com/posts/1691455094417024/graphql-a-data-query-language/
[10]: http://blog.kazaff.me/2016/01/01/GraphQL%E4%BB%80%E4%B9%88%E9%AC%BC/
[11]: https://www.sitepoint.com/creating-graphql-server-nodejs-mongodb/
[12]: https://segmentfault.com/a/1190000004586237#articleHeader3
[13]: https://segmentfault.com/a/1190000006741060
[14]: https://www.smashingmagazine.com/2010/07/how-to-use-css3-media-queries-to-create-a-mobile-version-of-your-website/
