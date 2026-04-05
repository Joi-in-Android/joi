# Ghosthand 使用指南

Ghosthand 是 Joi 操控 Android 手机屏幕的核心工具。

## 基本信息

- **API 端点**: `http://127.0.0.1:5583`
- **协议**: HTTP REST API
- **作用**: 通过 Android AccessibilityService 操控屏幕

## 常用端点

| 端点 | 用途 |
|------|------|
| `GET /screen` | 获取屏幕元素树 |
| `GET /screenshot` | 获取截图 (base64) |
| `POST /tap` | 点击坐标 |
| `POST /click` | 点击 nodeId |
| `POST /swipe` | 滑动 |
| `POST /input` | 输入文字 |
| `POST /launch` | 启动 App |
| `POST /home` | 按 Home 键 |

## 使用场景

1. **安装 APK**: MT管理器文件浏览器 → 导航到 `/data/local/tmp/` → 点击 APK → INSTALL
2. **卸载 App**: 设置 → 应用管理 → 搜索 → 卸载
3. **操控 App**: 截图找节点 → /click 或 /tap → 触发 UI 交互

## 关键经验

- `/storage/emulated/0/Download/` 是虚拟路径，写入会"成功"但不落地
- 真实可用的 APK 存放路径: `/data/local/tmp/`
- Android framework 服务 (`pm`, `am`) 在 chroot 内不可用
