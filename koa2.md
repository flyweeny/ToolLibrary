
# Koa2基本配置
```node
npm install koa -D
```
### index.js
```js
const Koa = require('Koa');
const app = new Koa();

app.use(async (ctx, next) => {
    const start = Date.now();
    await next();
    const ms = Date.now() - start;
    console.log(`${ctx.method} ${ctx.url} - ${ms}ms`)
});

app.use(async (ctx, next) => {
    const start = Date.now();
    await next();
    const ms = Date.now() - start;
    ctx.set('X-Response-Time', `${ms}ms`)
});

app.use(async (ctx, next) => {
    ctx.assert(ctx.request.accepts('xml'), 406);
    await next();
});

app.use(async ctx => {
    ctx.body = 'hello world';
});

function logger(format) {
    format = format || ':method ":url"';
    return async function (ctx, next) {
        const str = format
            .replace(':method', ctx.method)
            .replace(':url', ctx.url);

        console.log(str);
        await next();
    };
}

app.use(logger());
app.use(logger(':method :url'));
app.listen(3000);
console.log('[demo] is going');
```
### koa-compose.js
```js
const compose = require('koa-compose');
const koa = require('koa');
const app = new koa();

async function random(ctx, next) {
    if ('/random' === ctx.path) {
        ctx.body = Math.floor(Math.random() * 10);
    } else {
        await next();
    }
}

async function backwards(ctx, next) {
    if ('/backwards' === ctx.path) {
        ctx.body = 'backwards';
    } else {
        await next();
    }
}

async function pi(ctx, next) {
    if ('/pi' === ctx.path) {
        ctx.body = String(Math.PI);
    } else {
        await next();
    }
}

const all = compose([random, backwards, pi]);

app.use(all);

app.listen(3000);
```
### koa-order.js
```js
const koa = require('koa');
const app = new koa();

app.use(async function (ctx, next) {
    console.log('>> one');
    await next();
    console.log('<< one');
});

app.use(async function (ctx, next) {
    console.log('>> two');
    ctx.body = 'two';
    await next();
    console.log('<< two');
});

app.use(async function (ctx, next) {
    console.log('>> three');
    await next();
    console.log('<< three');
});

app.listen(3000);
```

## debug调试
#### 1.cmd
```
npm install debug -D
set DEBUG=*,-not_this
// example
set DEBUG=* & node app.js
```
