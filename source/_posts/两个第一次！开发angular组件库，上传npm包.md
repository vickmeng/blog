---
title: 两个第一次！
date: 2018-12-10 15:42:41
excerpt: 开发angular组件库，上传npm包
photos:
- ./img/packages.jpg

---
## 事情的开始是这样的
应业务需求做一个可以放在angular的表单里使用的富文本编辑器。为了方便同步给其他项目组，故而决定传个npm包。这也是我的首个有使用价值的开源项目。
## 开始
选了个star多，不需其他依赖的开源项目进行二次封装。感谢原作者。  

https://github.com/wangfupeng1988/wangEditor

AngularCLI v6集成了ng-packagr，提供了整套制作第三方组件的方案。
现学现卖，参考这个文章：  

https://blog.angularindepth.com/creating-a-library-in-angular-6-87799552e7e5

[angularindepth](https://blog.angularindepth.com)真是个好平台!

遇到的问题：
1. 头个问题就是纯傻，依赖的wangeditor没能自动install。我以为在angular项目里添加依赖包就可以了，实则不然，应该在project里进行安装（记得设置.gitignore）。
2. 试图配置到peerDependencies里面，依然没能自动install，查资料应该是npm2与npm3对peerDependencies的实现是有差异的，描述如下：
    http://link.zhihu.com/?target=https%3A//github.com/npm/npm/issues/6565
    这里给的方案是按提示手动npm install，然而洒家并不能认同这种结果。
    遇事不决问大哥：
    https://www.zhihu.com/people/sangka/activities

3. 还是要放在dependencies里。又报错，什么什么wangeditor不在白名单......
    https://stackoverflow。com/questions/51216616/what-is-the-proper-way-to-use-a-dependent-npm-package-in-angular-6-library-proje
    ​
    ng-package.json里配置whitelistedNonPeerDependencies，好用了。

剩下的一个问题就是如何布置针对组件库的css，首先我不想每个组件都手动引入，其次不希望暴漏给整个项目，以免冲突，待后续调查~

ps：我原本打算在组件里处理回压，几经思考觉得这种事还是放在业务里比较合适

 