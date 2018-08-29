# webpack配置
```js
{
  "name": "demo1",
  "version": "1.0.0",
  "description": "webpack-demo",
  "private": true,
  "main": "index.js",
  "scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production",
    "test": "echo \"Error: no test specified\" && exit 1",
    "watch": "webpack --watch --mode development",
    "start": "webpack-dev-server --open",
    "server": "node server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "clean-webpack-plugin": "^0.1.19",
    "css-loader": "^1.0.0",
    "express": "^4.16.3",
    "file-loader": "^2.0.0",
    "html-webpack-plugin": "^3.2.0",
    "style-loader": "^0.23.0",
    "webpack": "^4.17.1",
    "webpack-cli": "^3.1.0",
    "webpack-dev-middleware": "^3.2.0",
    "webpack-dev-server": "^3.1.6"
  },
  "dependencies": {
    "lodash": "^4.17.10"
  }
}

```
