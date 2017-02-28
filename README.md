https://github.com/mishoo/UglifyJS2/issues/1516#issuecomment-283086850
https://github.com/webpack/webpack/issues/4395

```bash
npm run compress // using uglifyjs
npm run build // using webpack
```

# Minified by uglifyjs-webpack-plugin (BAD)

```javascript
!function(e){function r(t){if(n[t])return n[t].exports;var o=n[t]={i:t,l:!1,exports:{}};return e[t].call(o.exports,o,o.exports,r),o.l=!0,o.exports}var n={};return r.m=e,r.c=n,r.i=function(e){return e},r.d=function(e,n,t){r.o(e,n)||Object.defineProperty(e,n,{configurable:!1,enumerable:!0,get:t})},r.n=function(e){var n=e&&e.__esModule?function(){return e.default}:function(){return e};return r.d(n,"a",n),n},r.o=function(e,r){return Object.prototype.hasOwnProperty.call(e,r)},r.p="",r(r.s=0)}([function(e,r,n){!function(e){function r(n){if(t[n])return t[n].exports;var o=t[n]={i:n,l:!1,exports:{}};return e[n].call(o.exports,o,o.exports,r),o.l=!0,o.exports}var n=window.webpackJsonp;window.webpackJsonp=function(t,u,a){for(var c,i,f,l=[];0<t.length;0++)i=t[0],o[i]&&l.push(o[i][0]),o[i]=0;for(c in u)Object.prototype.hasOwnProperty.call(u,c)&&(e[c]=u[c]);for(n&&n(t,u,a);l.length;)l.shift()();if(a)for(0=0;0<a.length;0++)f=r(r.s=a[0]);return f};var t={},o={4:0};r.e=function(e){function n(){u.onerror=u.onload=null,clearTimeout(a);var r=o[e];0!==r&&(r&&r[1](new Error("Loading chunk "+e+" failed.")),o[e]=void 0)}if(0===o[e])return Promise.resolve();if(o[e])return o[e][2];var t=document.getElementsByTagName("head")[0],u=document.createElement("script");u.type="text/javascript",u.charset="utf-8",u.async=!0,u.timeout=12e4,r.nc&&u.setAttribute("nonce",r.nc),u.src=r.p+""+({2:"vendors",3:"app"}[e]||e)+"."+{0:"4cda7157b54f2171e6a7",1:"527f2477a26b65a8ad65",2:"9499e7f4c8801da2e0da",3:"a00d56bf028f83f4a883"}[e]+".js";var a=setTimeout(n,12e4);u.onerror=u.onload=n;var c=new Promise(function(r,n){o[e]=[r,n]});return o[e][2]=c,t.appendChild(u),c},r.m=e,r.c=t,r.i=function(e){return e},r.d=function(e,n,t){r.o(e,n)||Object.defineProperty(e,n,{configurable:!1,enumerable:!0,get:t})},r.n=function(e){var n=e&&e.__esModule?function(){return e.default}:function(){return e};return r.d(n,"a",n),n},r.o=function(e,r){return Object.prototype.hasOwnProperty.call(e,r)},r.p="/",r.oe=function(e){throw console.error(e),e}}([])}]);
```

```
Uncaught ReferenceError: Invalid left-hand side expression in postfix operation
```

```
for(0=0;0<a.length;0++) // 0++ is the bad guy
```

# Minified by uglifyjs cli (GOOD)

```javascript
!function(modules){function __webpack_require__(moduleId){if(installedModules[moduleId])return installedModules[moduleId].exports;var module=installedModules[moduleId]={i:moduleId,l:!1,exports:{}};return modules[moduleId].call(module.exports,module,module.exports,__webpack_require__),module.l=!0,module.exports}var parentJsonpFunction=window.webpackJsonp;window.webpackJsonp=function(chunkIds,moreModules,executeModules){for(var moduleId,chunkId,result,i=0,resolves=[];i<chunkIds.length;i++)chunkId=chunkIds[i],installedChunks[chunkId]&&resolves.push(installedChunks[chunkId][0]),installedChunks[chunkId]=0;for(moduleId in moreModules)Object.prototype.hasOwnProperty.call(moreModules,moduleId)&&(modules[moduleId]=moreModules[moduleId]);for(parentJsonpFunction&&parentJsonpFunction(chunkIds,moreModules,executeModules);resolves.length;)resolves.shift()();if(executeModules)for(i=0;i<executeModules.length;i++)result=__webpack_require__(__webpack_require__.s=executeModules[i]);return result};var installedModules={},installedChunks={4:0};__webpack_require__.e=function(chunkId){function onScriptComplete(){script.onerror=script.onload=null,clearTimeout(timeout);var chunk=installedChunks[chunkId];0!==chunk&&(chunk&&chunk[1](new Error("Loading chunk "+chunkId+" failed.")),installedChunks[chunkId]=void 0)}if(0===installedChunks[chunkId])return Promise.resolve();if(installedChunks[chunkId])return installedChunks[chunkId][2];var head=document.getElementsByTagName("head")[0],script=document.createElement("script");script.type="text/javascript",script.charset="utf-8",script.async=!0,script.timeout=12e4,__webpack_require__.nc&&script.setAttribute("nonce",__webpack_require__.nc),script.src=__webpack_require__.p+""+({2:"vendors",3:"app"}[chunkId]||chunkId)+"."+{0:"4cda7157b54f2171e6a7",1:"527f2477a26b65a8ad65",2:"9499e7f4c8801da2e0da",3:"a00d56bf028f83f4a883"}[chunkId]+".js";var timeout=setTimeout(onScriptComplete,12e4);script.onerror=script.onload=onScriptComplete;var promise=new Promise(function(resolve,reject){installedChunks[chunkId]=[resolve,reject]});return installedChunks[chunkId][2]=promise,head.appendChild(script),promise},__webpack_require__.m=modules,__webpack_require__.c=installedModules,__webpack_require__.i=function(value){return value},__webpack_require__.d=function(exports,name,getter){__webpack_require__.o(exports,name)||Object.defineProperty(exports,name,{configurable:!1,enumerable:!0,get:getter})},__webpack_require__.n=function(module){var getter=module&&module.__esModule?function(){return module.default}:function(){return module};return __webpack_require__.d(getter,"a",getter),getter},__webpack_require__.o=function(object,property){return Object.prototype.hasOwnProperty.call(object,property)},__webpack_require__.p="/",__webpack_require__.oe=function(err){throw console.error(err),err}}([]);
```
