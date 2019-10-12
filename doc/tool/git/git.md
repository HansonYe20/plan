# 基本/网页操作
  这点无需过多赘述
---
# SSH
- 场景: 每次输入密码太麻烦, 使用ssh提交代码方便啊
- 使用方法: [SSH keys][gitSSH]
+ 涉及概念:
  - 公钥
  - 私钥
  - 加密方式
+ 登录原理: 
参考 [阮一峰老师的文档][ruanyifeng], 介绍很详细
---
# license
  创建项目的时候需要指定一种类型的license, 不同的license授权范围不同
---
# readme
## 1.语法:
使用markdown语法, 具体语法参考了[markdown站点][markdown1],
[其他补充][markdown2]
## 2.chrome相关插件:
- FeHelper
+ MarkDown Preview Plus
  - 可以直接读取本地文件
  - 如果不能读取, 右键=>管理扩展程序=>允许访问文件网址, 需要手动打开读取本地文件的权限

## 3.思考:
- (1)html如何展示markdown文件?
  将markdown内容转成html
  ```
  import marked from 'marked';
  const mdContent = `# 文档中心`
  marked.setOptions({
    renderer: new marked.Renderer(),
    gfm: true,
    tables: true,
    breaks: true,
    pedantic: false,
    sanitize: false,
    smartLists: true,
    smartypants: false,
  });
  const mdHtml = marked(mdContent);
  ```
  ```
  <div dangerouslySetInnerHTML={{ __html: mdHtml }}></div>
  ```
- (2)...
---
# 不常用但重要的命令
- 账户锁住: rm -f ./.git/index.lock
- 回滚: ...
- // todo


# 视图化工具
- sourceTree

# vscode相关git插件及使用
1. [vscode同步设置][settings sync](仅针对macOs)
  - upload: Shift + Option + U
  - download: Shift + Option + D
2. GitLens

[gitSSH]: https://github.com/settings/keys 'SSH keys'
[ruanyifeng]: http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html 'ruanyifeng'
[markdown1]: https://www.markdown.cn/ 'markdown1'
[markdown2]: https://guo365.github.io/study/Markdown.html#41 'markdown2'
[settings sync]: https://github.com/shanalikhan/code-settings-sync 'settings sync'