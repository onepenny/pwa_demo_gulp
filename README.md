# workbox demo for gulp

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

# TODO
- 更精细的缓存控制
饿了么pwa升级实践 4步骤(初始url预取_?, 渲染_提速首次渲染与首次可交互时间_preload?, 关键路由即AppShell预取_prefetch?, lazy-load剩下的路由资源)

