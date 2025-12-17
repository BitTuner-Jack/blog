## 一、官方源地址

**官方默认源**：

```
https://registry.npmjs.org/
```

---

## 二、常用镜像源链接

国内主流镜像源（按使用广泛度排序）：

| 镜像源            | 地址                                           | 特点                 |
| ----------------- | ---------------------------------------------- | -------------------- |
| **淘宝 NPM 镜像** | `https://registry.npmmirror.com/`              | 更新及时，使用最广泛 |
| 腾讯云镜像        | `https://mirrors.cloud.tencent.com/npm/`       | 服务质量稳定         |
| 华为云镜像        | `https://repo.huaweicloud.com/repository/npm/` | 企业级服务           |
| cnpmjs 镜像       | `https://r.cnpmjs.org/`                        | 社区维护             |

> ⚠️ 注意：淘宝镜像已弃用旧域名 `registry.npm.taobao.org`，现统一使用 `registry.npmmirror.com`

---

## 三、设置方法

### 1. 临时设置（单次命令有效）

仅在当前命令中使用指定源，不修改全局配置：

```bash
# 安装特定包时使用镜像源
npm install 包名 --registry=https://registry.npmmirror.com

# 从官方源临时安装
npm install opencode-ai --registry=https://registry.npmjs.org/
```

特点：灵活、安全，不影响其他项目

### 2. 全局/永久设置

修改 npm 默认配置，后续所有操作均使用新源：

```bash
# 设置为淘宝镜像（推荐国内用户）
npm config set registry https://registry.npmmirror.com

# 恢复官方源
npm config set registry https://registry.npmjs.org/

# 查看当前配置
npm config get registry
```

特点：一次设置，永久生效（直到手动修改）

> 注意：有时候镜像源同步慢，导致无法update一些包，使用官方源即可。 

---

## 四、验证与排查

**查看当前使用的源**：

```bash
npm config get registry
```

输出示例：

- `https://registry.npmjs.org/` → 官方源
- `https://registry.npmmirror.com/` → 淘宝镜像

**查看详细配置**：

```bash
npm config list
```

**清理缓存（切换源后推荐执行）**：

```bash
npm cache clean --force
```

---

## 五、重要提醒

1. **镜像同步延迟**：国内镜像可能存在 5-30 分钟延迟，新版本包可能无法立即安装

2. **二进制包风险**：部分包含原生二进制文件的包（如 `opencode-ai`）在镜像源可能同步不完整，导致安装失败。此时建议：
```bash
# 方式一：临时使用官方源安装
npm install opencode-ai --registry=https://registry.npmjs.org/

# 方式二：安装后切回镜像源
npm config set registry https://registry.npmmirror.com/
```

通过灵活运用临时设置和全局设置，可以在保证速度的同时，规避镜像源可能带来的问题。