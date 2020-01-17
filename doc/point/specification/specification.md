# js 规范概念介绍
大概有这么几种: CJS AMD UMD ESM
[原文文档][docUrl]
[AMD][AMD]
[UMD][UMD]
[ESM][ESM]
[Tree-shakeable][Tree-shakeable]

# 概念
  - CJS:
    - 定义:
      既CommonJS
    - demo:
      ```
      //importing 
      const doSomething = require('./doSomething.js'); 

      //exporting
      module.exports = function doSomething(n) {
        // do something
      }
      ```
    - 其他:
      - node使用的是cjs
      - CJS imports module synchronously.
      - 可以从库中(node_modules)引用文件, 也可以直接引用本地文件
      - require文件后, 将会得到一个引用文件的副本(When CJS imports, it will give you a copy of the imported object.)
      - 不可以运行在浏览器

  - AMD:
    - 定义:
      既Asynchronous Module Definition
    - demo:
      ```
      define(['dep1', 'dep2'], function (dep1, dep2) {
          //Define the module value by returning a value.
          return function () {};
      });

      // "simplified CommonJS wrapping" https://requirejs.org/docs/whyamd.html
      define(function (require) {
          var dep1 = require('dep1'),
              dep2 = require('dep2');
          return function () {};
      });
      ```
    - 其他:
      - AMD imports modules asynchronously 
      - AMD is made for frontend (when it was proposed) (while CJS backend).
      - 感觉上AMD比CJS的语法更少
  
  - UMD
    - 定义:
      既 Universal Module Definition
    - demo:
      ```
      (function (root, factory) {
          if (typeof define === "function" && define.amd) {
              define(["jquery", "underscore"], factory);
          } else if (typeof exports === "object") {
              module.exports = factory(require("jquery"), require("underscore"));
          } else {
              root.Requester = factory(root.$, root._);
          }
      }(this, function ($, _) {
          // this is where I defined my module implementation

          var Requester = { // ... };

          return Requester;
      }));
      ```
    - 其他:
      - 与CJS或AMD不同，UMD更像是一种配置多个模块系统的模式
      - 前后端通用
      - 使用Rollup / Webpack等捆绑程序时，UMD通常用作备用模块
  
  - ESM
    - 定义:
      既ES Modules, javascript建议实现一套标准的模块系统(It is Javascript's proposal to implement a standard module system)
    - demo:
      ```
      import React from 'react';

      import {foo, bar} from './myLib';
      ...
      export default function() {
        // your Function
      };
      export const function1() {...};
      export const function2() {...};
      ```
    - 其他:
      - 可以运行于现代浏览器
      - Tree-shakeable, due to ES6's static module structure
      - 包含每个规范最好的部分: 类似于cjs简单的语法, amd的异步
      - ESM允许像Rollup这样的打包程序删除不必要的代码，从而使站点可以发布较少的代码来加快加载速度
      - 可以在HTML中调用, 比如:
        ```
        <script type="module">
          import {func1} from 'my-lib';
          func1();
        </script>
        ```

# 总结
  - ESM is the best module format thanks to its simple syntax, async nature, and tree-shakeability.
  - UMD works everywhere and usually used as a fallback in case ESM does not work
  - CJS is synchronous and good for back end.
  - AMD is asynchronous and good for front end.
  - ES6模块不是完全异步的，至少不是现在大多数地方都在使用它们。除非您使用动态导入，否则每个导入语句都会在下一条语句开始执行之前运行完毕，并且获取（和解析）模块的过程就是其中的一部分


[docUrl]: https://dev.to/iggredible/what-the-heck-are-cjs-amd-umd-and-esm-ikm
[AMD]: https://requirejs.org/docs/whyamd.html
[UMD]: http://bob.yexley.net/umd-javascript-that-runs-anywhere/
[ESM]: https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/
[Tree-shakeable]: https://zhuanlan.zhihu.com/p/33154109