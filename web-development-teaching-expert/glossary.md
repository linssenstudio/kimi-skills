# 术语表（Glossary）

> 按字母/拼音序，标注教材章节来源。检索某术语细节时跳转对应 `chapters/chNN-*.md`。

## A–C
- **alt 属性**：图像的替代文本，图像无法显示时呈现，也是无障碍阅读的基础。ch04、ch09
- **语义化标记（semantic markup）**：用标记表达内容含义而非外观（如 `<strong>` 表示重要而非"加粗"）。ch01、ch02
- **内容与表现分离**：HTML 管结构内容，CSS 管外观，JS 管行为——Web 标准三层架构的核心原则。ch01、ch03、ch09
- **层叠（cascade）**：多条规则冲突时按"重要性→优先级(specificity)→源码顺序"决定生效样式的机制。ch03
- **优先级 / specificity**：选择器权重计算：行内 > id > 类/伪类/属性 > 标记符。ch03
- **超链接 / 锚点链接 / 相对 URL / 绝对 URL**：站内用相对 URL；`#锚点名` 跳转页内位置。ch02、ch09
- **DOM（文档对象模型）**：浏览器把网页解析成的对象树，JS 通过它读写页面。ch07
- **DW 站点（site）**：Dreamweaver 管理的网站文件夹，建立站点是所有操作的起点。ch09
- **响应式设计（responsive design）**：网站随设备环境（平台、屏幕尺寸、定向）自动调整的設計方法；核心技术为 viewport meta + 媒体查询 / Bootstrap 栅格。ch07、ch09、ch10
- **表单（form）**：收集用户输入提交服务器的元素集合；`action` 指定处理程序，`method` 常用 POST。ch05、ch07

## F–J
- **浮动（float）与清除浮动（clear）**：块脱离文档流左右排列；父元素塌陷用 clear 或清除浮动技巧解决。ch06
- **盒模型（box model）**：content + padding + border + margin；`box-sizing:border-box` 改变宽度计算方式。ch03、ch06
- ** emmet **：HTML/CSS 缩写快速输入插件语法（`ul>li*3`），DW 与 VS Code 内置。ch09
- **信息架构**：网站内容的组织方式（栏目与层级），须符合普通人思维习惯。ch08、ch10
- **媒体查询（media query）**：`@media mediatype and (media feature){…}`，响应式核心语法；常用 max-width/min-width。ch06、ch09
- **后备箱测试（trunk test）**：Steve Krug 的导航可用性测试——随机取页面遮住网站标识，看能否回答"我在哪个网站/哪个页面/有哪些栏目/当前位置/如何搜索"。ch08、ch10

## K–S
- **块级元素 / 行内元素**：div/p/h1 独占一行；span/a/em 行内排列；`display` 可转换。ch02、ch03
- **KISS 原则**：Keep It Simple and Stupid——保持简单易懂，当代网页设计主流。ch10
- **类选择器（.class）与 ID 选择器（#id）**：类可复用、id 唯一；class 用于样式，id 兼作锚点与 JS 钩子。ch03
- **link / @import / 页内 style / 行内 style**：CSS 四种用法，推荐外部链接式；页内须置于 link 之后。ch03、ch09
- **label 标签**：关联表单控件（for=id），扩大点击区域、提升可用性。ch05
- **四原则（紧凑、对齐、重复、对比）**：Robin Williams 版式设计四原则，教材 ch08 核心框架。
- **扫描而非阅读**：用户浏览网页的行为特征；设计应服务扫读（标题、要点、短段落）。ch08、ch10
- **事件驱动**：JS 通过事件（click/mouseover/submit…）响应用户操作的编程模型。ch07
- **SOP（标准操作规程）**：工程实践的规范化流程概念，网站开发五流程即一例。ch10

## T–Z
- ** viewport **：`<meta name="viewport" content="width=device-width, initial-scale=1.0">`，移动适配第一步。ch07、ch09、ch10
- **Web 标准三层**：结构（HTML）/ 表现（CSS）/ 行为（JavaScript）。ch01
- **伪类（pseudo-class）**：`:hover`/`:link`/`:visited` 等按状态匹配的选择器；链接伪类顺序 LoVe/HAte。ch03、ch06
- **网站开发五流程**：规划 → 设计 → 开发 → 发布 → 维护（循环）。ch10
- **网站策划书**：含调研、目的与功能、技术方案、内容规划、设计、维护、测试、发布推广、日程、费用 10 项。ch10
- **栅格系统（grid）**：Bootstrap 12 列响应式栅格（col-md-6 等）。ch07、ch09、ch10
- **字符编码**：`<meta charset="utf-8">`，缺失会中文乱码。ch01
- **CSS 继承**：部分属性（字体、颜色）自动传给后代元素。ch03
