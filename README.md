# ALIST-BEAUTIFICATION

一个创新的 AList 动态美化工具，通过动态监控页面变化并自动替换元素背景色，实现对 AList 前端的高效美化，同时保持对 AList 版本更新的良好适应性。

## 🎯 核心特点

- **动态监控**：自动监听页面变化，实时美化背景色
- **智能识别**：精准识别需要美化的元素，避免误操作
- **高适应性**：无需枚举修改前端元素，对 AList 版本更新有更好的兼容性
- **自定义灵活**：支持自定义背景色，满足个性化需求
- **多种使用方式**：支持直接复制 HTML 代码或通过 CDN 引入
- **登录界面优化**：提供专门的登录界面美化支持

## 📁 项目结构

```
alist-beautification/
├── head.html          # 自定义头部（传统美化代码，包含自定义字体等）
├── body_with_login.html # 包含动态美化监视器和登录界面优化
├── src/
│   ├── beautifier.js       # 核心动态美化监视器 JS 代码
│   └── beautifier_with_login.js # 带有登录界面美化的 JS 代码
└── LICENSE
```

## 🚀 使用方法

### 方法一：直接复制 HTML 代码

1. 登录 AList 后台
2. 进入 `设置 > 全局`
3. 将 `head.html` 的内容复制到 `自定义头部` 字段
4. 将 `body_with_login.html` 的内容复制到 `自定义内容` 字段
5. 保存设置，刷新页面即可生效

### 方法二：通过 CDN 引入

如果只需要美化背景色功能，可以直接从 CDN 引入：

```html
<!-- 修正部分区域的透明 -->
<style>
    .hope-ui-light,
    .hope-ui-dark {
        --hope-colors-background: transparent;
    }
</style>

<!-- 仅引入核心美化功能 -->
<script type="module" src="https://fastly.jsdelivr.net/gh/adogecheems/alist-beautification@latest/src/beautifier.js"></script>

<!-- 或引入包含登录界面美化的版本 -->
<script type="module" src="https://fastly.jsdelivr.net/gh/adogecheems/alist-beautification@latest/src/beautifier_with_login.js"></script>
```

## 💡 控制台操作

美化器实例暴露了以下方法，可通过 `window.beautifier` 访问：

- `observe()`：开始监听页面变化并美化背景色
- `disconnect()`：停止监听页面变化
- `undo()`：恢复页面背景色到默认状态

### 示例

```javascript
// 完全消除美化效果
window.beautifier.undo();

// 重新开始美化
window.beautifier.observe();
```

## 🎨 自定义背景色

可以通过修改代码中的背景色变量来自定义美化效果：

```javascript
// 在 beautifier.js 或 body_with_login.html 中找到以下代码
static lightBgColor = 'rgba(255, 255, 255, 0.8)'; // 浅色模式背景色
static darkBgColor = 'rgb(32, 36, 37)'; // 深色模式背景色
```

### 修改示例

```javascript
// 为深色模式添加半透明效果
static lightBgColor = 'rgba(255, 255, 255, 0.8)';
static darkBgColor = 'rgba(32, 36, 37, 0.8)';
```

## 🔧 技术实现

项目核心是 `Beautifier` 类，通过以下技术实现动态美化：

1. 使用 `MutationObserver` 监听 DOM 变化
2. 智能识别带有背景色的元素
3. 自动替换为自定义背景色
4. 为美化元素添加 `data-beautified` 属性，方便恢复

## 📝 注意事项

1. 该美化工具主要针对 AList 的背景色进行优化
2. 支持浅色模式和深色模式
3. 自动忽略不需要美化的元素（如按钮、图标、代码编辑器等）
4. 对管理页面（路径以 `/@manage` 开头）不进行美化

## 📄 许可协议

本项目采用 AGPL-3.0 许可协议，详细信息请查看 [LICENSE](LICENSE) 文件。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request，一起做一个内外网自动切换的资源加载系统改进这个项目！

## ⭐ 支持

如果这个项目对你有帮助，请给个 Star 支持一下吧！

