# Wiki 网页模板使用说明

## 文件位置

| 文件 | 用途 |
|---|---|
| `references/wiki-template.html` | 纯骨架。含 CSS、结构、交互 JS 与全部占位符，**不含任何行业实例内容** |
| `references/example-education.html` | 完整实例（教育领域），用于参照成品形态，不参与生成 |

## 生成步骤

1. 复制 `wiki-template.html` 全文。
2. 替换全部 `{{占位符}}`。
3. 替换完成后自查：文件中不应再出现 `{{` 或 `}}`，也不应出现任何与本次身份无关的行业词汇。

## 占位符清单

| 占位符 | 含义 |
|---|---|
| `{{PAGE_TITLE}}` | 浏览器标签标题 |
| `{{TOPBAR_LOGO}}` | 顶栏左侧标识，建议为「领域 + 解读」形式 |
| `{{DOC_REF}}` | 顶栏右侧文号或发布标识 |
| `{{NAV_ITEMS}}` | 侧边栏五条维度导航，形如 `<a href="#d1" class="nav-item">一、背景与风向</a>`，共 5 行 |
| `{{APPENDIX_NAV_LABEL}}` | 附录导航文字，如「受众行动清单」 |
| `{{HERO_REF}}` | 首屏上方文号行 |
| `{{DOC_TITLE}}` | 文件标题 |
| `{{HERO_SUBTITLE}}` | 副标题，写明面向哪个身份 |
| `{{HERO_META}}` | 三个 `<span>`，依次为发布主体、发布时间、核心目标 |
| `{{D1_NAME}}` … `{{D5_NAME}}` | 五个维度的名称 |
| `{{D1_QUESTION}}` … `{{D5_QUESTION}}` | 该维度核心追问，按本次身份改写 |
| `{{D1_KEYWORDS}}` … `{{D5_KEYWORDS}}` | 关键词，中文间隔号连接 |
| `{{D1_AUDIENCE_LABEL}}` … `{{D5_AUDIENCE_LABEL}}` | 受众之问的标签，写成本次身份的口吻，如「科室主任的思考」 |
| `{{D1_AUDIENCE_THOUGHT}}` … `{{D5_AUDIENCE_THOUGHT}}` | 该身份在这一维度上的切身关切 |
| `{{D1_BODY}}` … `{{D5_BODY}}` | 维度正文，由 `<div class="text">`、`<table class="wiki-table">`、`<h3>` 等自由组合 |
| `{{D1_CONCLUSION}}` … `{{D5_CONCLUSION}}` | 结论框正文，一句话判断，可用 `<strong>` |
| `{{D1_TAGS}}` … `{{D5_TAGS}}` | 标签，由多个 `<span class="tag">` 组成；不需要时整块删除 |
| `{{APPENDIX_TITLE}}` | 附录标题，如「科室主任行动清单」 |
| `{{APPENDIX_BODY}}` | 附录正文，通常是一张按时间分档的行动表 |
| `{{FOOTER}}` | 页脚，文号与免责说明，用 `<br>` 换行 |

## 可复用组件

| 组件 | 写法 | 用途 |
|---|---|---|
| 正文段 | `<div class="text"><p>…</p></div>` | 普通解读段落 |
| 列表 | `<div class="text"><ul><li>…</li></ul></div>` | 并列要点 |
| 对照表 | `<table class="wiki-table">` + `<thead>/<tbody>` | 原文要点与行动指向对照 |
| 结论框 | `<div class="callout">` | 每维度收尾一句判断 |
| 标签 | `<div class="tags"><span class="tag">…</span></div>` | 关键词标签 |
| 小标题 | `<h3>…</h3>` | 同一维度内的分节 |
| 过渡箭头 | `<div class="arrow-row">↓ ↓ ↓</div>` | 维度之间的分隔，已内置 |

## 可调项

### 配色

修改 `:root` 变量：

```css
:root {
  --ink: #2C2C2C;          /* 主文字色 */
  --accent: #3A5F8A;       /* 主题色 */
  --accent-light: #E8EFF5; /* 结论框背景 */
  --paper: #FEFEFA;        /* 页面底色 */
}
```

### 侧边栏

- 默认宽度 `--sidebar-w: 248px;`
- 设为 `0px` 可隐藏侧边栏
- 窗口宽度 ≤ 900px 时自动收起，由顶栏汉堡按钮唤出

### 维度数量

本骨架固定五维。如需增减，复制或删除整个 `<div class="section">` 区块，并同步侧边栏 `{{NAV_ITEMS}}` 中的导航条目，同时检查 `.arrow-row` 的数量与位置。

## 已知修正记录

相对旧版模板，骨架已修正两处缺陷：

1. 顶栏汉堡按钮原先带 `display: none !important`，导致移动端无法唤出侧边栏，已改为媒体查询控制。
2. 侧边栏默认宽度原为 `0px`，导航实际不可见，已改为 `248px`。
