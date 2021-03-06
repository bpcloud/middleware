
# bpframework Middleware specification

The middleware must have below methods:

```js
interface BpframeworkMiddleware {
  /** name of middleware */
  name: string,
  /** web framework type. e.g. 'koa' **/
  type: string,
  /** initiator the middleware */
  initiator: (app:any, bpApp:any)=>void,
  /** The framework context finished, all objects of framework, e.g. FeignClient, start working. */
  contextFinished?: (app:any, bpApp:any)=>void,
  /** call before route */
  beforeRoute?: (app:any, bpApp:any)=>Promise<boolean>,
  /** call after route */
  afterRoute?: (app:any, bpApp:any)=>Promise<boolean>,
}
```

`initiator` -> `contextFinished` -> `beforeRoute` -> `afterRoute`

Example:

```js
export default {
  name: 'test-middleware',
  type: 'koa',
  initiator(app, bpApp) {

  },
  async beforeRoute(ctx, bpApp): boolean {
    // To interrupt process of follow-up .
    return false;
  },
  async afterRoute(ctx, bpApp): boolean {
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
| redis          | https://github.com/bpcloud/middleware-redis          |
| database       | https://github.com/bpcloud/middleware-db             |
| logger         | https://github.com/bpcloud/middleware-log4js         |

