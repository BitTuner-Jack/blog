## nrm 是什么、用来做什么

**nrm（NPM registry manager）是用来管理/切换 npm 镜像源的工具**，适合在不同网络环境下快速切换 registry（例如 npm 官方源、腾讯、华为等）。它的价值在于：切换后你仍然直接用 `npm install`，不需要再换成 `cnpm` 之类的命令；并且还支持对多个源**测速**。

---

## 最常用的命令（你基本只需要这几个）

### 1) 查看所有源

- `nrm ls`：列出所有注册表（registry）

### 2) 看当前正在用哪个源

- `nrm current`：显示当前注册表名称

### 3) 切换到某个源（核心）

- `nrm use <registry>`：切换注册表

例如切换到淘宝源的示例就是：`nrm use taobao`  
要切腾讯源则用：`nrm use tencent`（因为你的 `nrm ls` 里就有 `tencent` 这个名称）

切换后建议确认一下 npm 实际 registry：

- `npm config get registry`（确认 npm 已跟随切换）

### 4) 测速，看看哪个源最快

- nrm 支持对多个源**测速**（一般命令是 `nrm test`，具体以 `nrm --help` 输出为准）