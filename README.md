# pwa demo for gulp

# 演示功能
gulp使用workbox 实现pwa
# 关键内容
- gulpfile.babel.js中`service-worker`task 1 2
- app/sw.js中 1 2

# Usage
```sh
gulp build
python3 -m http.server 3004
```

# pwa方案理论
(个人理解: 理论有了, 实践问题不大 OvO)
- 一.饿了么pwa升级实践4步骤PRPL(Push/Preload、Render、Precache、Lazy-Load)
  - 1.PUSH/PRELOAD，推送/预加载初始URL(可理解为首页)路由所需的关键资源(首页关键资源)。
       - (1)首页html中的`<link rel="preload">` `<script>`以便被浏览器preload扫码器识别应用依赖关系教深处的资源, 进行提前加载
       - (2)server push
       - (3)首页关键资源可从webpack entry依赖资源大致看出
  - 2.RENDER，渲染初始路由，尽快让应用可被交互
       - (1)多页应用不依赖js做路由 而根据page, 因此不需要做什么
       - (2)骨架屏提升白屏期间用户响应, 1>黑魔法setTimeout(() => new Vue(), 0)以便主业务逻辑执行前 骨架屏能顺利绘制
          2>preload骨架屏css以便所有css下载前骨架屏顺利绘制
  - 3.PRE-CACHE，用 Service Worker 预缓存剩下的路由
       - (1) 利用service worker主动发起请求预取 并缓存剩下路由, 只prefetch appshell或者称之"关键路由"或"安装包",
       e.g.在首页precache: order shop profile sales offline等路由资源
       - (2) 自动化方法: 利用webpack生成prefetch, 每次构建时根据prefetch清单生成新的service-worker.js文件,
       新service-worker.js激活时还行prefetch_钩子是install还是activate?
  - 4.LAZY-LOAD 按需懒加载、懒实例化剩下的路由
       - (1)多页应用天生根据page懒加载, 因此不需要做什么 
       - (2)预测下一步操作并预加载资源 以便下一步操作迅速响应

- 二.workbox使用过程中问题解决 todo

