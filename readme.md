
# bpframework Middleware specification

The middleware must have below methods:

```js
interface BpframeworkMiddleware {
  /** name of middleware */
  name: string,
  /** web framework type. e.g. 'koa' **/
  type: string,
  /** call after route */
  initiator: (app:any)=>void,
  /** initiator the middleware */
  afterRoute: (app:any)=>Promise<boolean>,
  /** call before route */
  beforeRoute: (app:any)=>Promise<boolean>,
}
```

Example:

```js
export default {
  name: 'test-middleware',
  type: 'koa',
  initiator(app) {

  },
  async beforeRoute(ctx): boolean {
    // To interrupt process of follow-up .
    return false;
  },
  async afterRoute(ctx): boolean {
    // To interrupt process of follow-up.
    return false;
  },
}
```

### List

| name           | descs                                                |
| -------------- | ---------------------------------------------------- |
| koa-i18n       | https://github.com/bpcloud/middleware-koa-i18n       |
| koa-bodyparser | https://github.com/bpcloud/middleware-koa-bodyparser |
| koa-cors       | https://github.com/bpcloud/middleware-koa-cors       |