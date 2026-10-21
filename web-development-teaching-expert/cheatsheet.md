# 速查表（Cheatsheet）

> 一页式决策参考。细节回查对应章节文件。

## HTML 骨架（第一课即给学生的最小模板）
```html
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>页面标题</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <!-- 内容 -->
</body>
</html>
```

## 图像格式选择
| 场景 | 格式 |
|---|---|
| 照片、渐变丰富 | JPEG |
| 需要透明、图标 | PNG |
| 简单动图 | GIF |
| Logo/矢量 | SVG |
| 追求体积（现代浏览器） | WebP |

## class vs id
| | class | id |
|---|---|---|
| 页面内可复用 | ✓ | ✗ 唯一 |
| 主要用途 | CSS 样式 | JS 钩子、锚点 |
| 选择器 | `.name` | `#name` |
| 优先级 | 中 | 高 |

## CSS 优先级（从低到高）
标记符选择器 < 类/伪类/属性选择器 < ID 选择器 < 行内 style < `!important`（慎用）
同级冲突 → 后写的生效。外部表先 link，页内 style 置后。

## 四种 CSS 用法选择
| 用法 | 何时用 |
|---|---|
| 外部 `<link>` | 默认，全站共享 |
| 页内 `<style>` | 仅本页的规则 |
| 行内 `style=""` | 尽量避免（调试/临时除外） |
| `@import` | 不推荐（阻塞加载） |

## 定位方式选择
| 需求 | 方案 |
|---|---|
| 普通文档流 | 默认 static |
| 相对原位置微调（如按钮按下偏移） | relative |
| 相对最近定位祖先精确放置 | absolute |
| 吸附屏幕（固定导航/返回顶部） | fixed |
| 多列并排（传统） | float + clear |
| 多列并排（现代） | flexbox / grid |

## 媒体查询断点（教材案例）
```
@media screen and (min-width:1200px)
@media screen and (min-width:992px)
@media screen and (min-width:768px)
@media screen and (min-width:480px)
```
max-width 方案务必**从大到小**书写。mediatype：all/print/screen/speech。

## JS 调试三板斧
1. F12 打开开发者工具 → Console 看报错行号；
2. `console.log(变量)` 追踪值；
3. 常见元凶：大小写、`=` 当 `==`、引号未配对、getElementById 的 id 拼写、脚本在 DOM 加载前执行（放 body 末尾或 DOMContentLoaded）。

## 表单控件速查
单行文本 `input type=text` / 密码 `password` / 多行 `textarea` / 单选 `radio`（同 name 成组）/ 多选 `checkbox` / 下拉 `select>option` / 提交 `submit` / 普通按钮 `button`。每个控件配 `<label for>`。form 不可嵌套。

## 网站开发五流程
规划（目标·用户·风格·技术·信息架构）→ 设计（导航·版式·主页）→ 开发（模板先行·测试贯穿）→ 发布（ISP+FTP）→ 维护（更新循环）。

## 设计四原则（ch08）
紧凑（相关内容成组）· 对齐（元素间有视觉联系）· 重复（统一风格要素复现）· 对比（差异要大胆）。外加：适合扫描、后备箱测试。
