# 使用vscode来调试Cli
  [官方参考文档][doc]

# 背景
  - 由于在cli开发过程中只能通过console或者cli执行的结果来测试, 虽然说能完成整个cli的开发, 但是:
    - 1. 留下了很多console, 很low, 还得清理, 如果遇到新问题, 还得打开
    - 2. 直接看结果, 万一歪打正着呢? 这样会丢失很多中间态

# 相关插件
  debugger for chrome

# 开始调试
  1. 调试界面介绍
  ![debugger-0][debugger-0]
  2. 点击箭头处按钮, 将会在当前work space下生成./vscode/launch.json文件
  ![debugger-1][debugger-1]
  3. 配置launch.json文件:
    ```
    {
      "type": "node",
      "request": "launch",
      "name": "mkt create",
      "program": "${workspaceFolder}/index.js",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "args": ["create", "-m", "app/202002/demo"],
    },
    ```
    这里需要注意, 由于是用node启动,"request": "launch", 区别于浏览器的attach方式
  4. 打好断点, 点击上方或者下方的三角箭头, 就可以愉快的debug了, 可以watch变量, 也可以悬浮鼠标提示
  ![debugger-2][debugger-2]

  5. 日志点, 比较骚气
  在代码左侧栏, 右键, 选择add logPoint, 还可以使用表达式
  ![log][log]

# 问题
  1. debug不生效
    因为本地重新npm i 当前cli项目了, 所以项目运行的真实代码是在/usr/local/lib/node_modules/mkt-cli目录下, 没有进断点;
    解决方案: 执行npm link, 建立软链接, 改变运行目录


[doc]: https://code.visualstudio.com/docs/editor/debugging
[debugger-0]: ./assets/debugging_hero.png 
[debugger-1]: ./assets/debbuger-1.jpg 
[debugger-2]: ./assets/debbuger-2.jpg 
[log]: ./assets/log-point.gif