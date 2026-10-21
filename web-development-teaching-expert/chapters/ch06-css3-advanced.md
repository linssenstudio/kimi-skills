# 第6章 CSS3进阶

> 教材定位：第2部分"前端开发核心技术"第1章 | 前置：ch03（基本选择器与属性）、ch02（列表）
> 原文核对：full_text.txt 行7169–10093 | 全书最重的 CSS 章：高级选择器 + 盒模型 + 定位 + 优先级

## 核心思想
从"修饰元素"升级到"控制布局"：高级选择器精确选中元素，盒模型度量元素，定位机制摆放元素，优先级规则裁决冲突。

## 教学目标（教材原文）
- 知识：4 种高级选择器；盒模型；文档流与 3 种定位机制；div/span；静态/浮动/相对/绝对/固定定位；分类/列表/特效属性
- 技能：精确选择元素；padding/border/margin 修饰；各定位法做布局；特效属性；一体化风格设计
- 素养：对比 5 基本+4 高级选择器探讨技术演化；布局影响信息传递效率；中华美食网站（文化自信）

## 知识点

### KP6.1 高级选择器（6.1）
| 选择器 | 写法 | 选中 | 例 |
|---|---|---|---|
| 后代 | `A B`（空格=结合符） | A 内**任意深度**的 B | `h1 em{color:red;}`；`div#sidebar a{color:white;}` vs `div#main a{color:blue;}`（左右栏不同链接色，经典教学案例） |
| 子元素 | `A > B` | 仅直接子元素（嵌套一层） | `h1 > strong`；`>` 旁空格可选 |
| 相邻兄弟 | `A + B` | 紧跟 A 后、同父的 B（只选后者） | `h1 + p{margin-top:50px;}`；`li + li{font-weight:bold;}` 跳过每组第1项 |
| 属性 | `[attr]`、`[attr=值]` | 带指定属性/属性值的元素 | `[title]`、`input[type="text"]`、`a[href][title]` |
- 可组合：`table.company td > p`、`#box > #container table + ul`
- 素养讨论点：与第3章 5 种基本选择器对比，看选择器表达能力的技术演化

### KP6.2 盒模型（6.2.1）—— 全书最重要概念之一
- 结构（由内而外，考试排序题）：**内容 content → padding 填充 → border 边框 → margin 边距**
- width/height 指**内容区域**尺寸；总宽度 = width + 左右 padding + 左右 border + 左右 margin（教材算例：要总宽 60px、margin 10px、padding 5px → width=30px）
- 背景作用于 content+padding+border 区域；margin 默认透明
- 多值缩写顺序：**上右下左**（顺时针）；2~3 个值时未指定的边取对边
- padding 不许负值；margin 可负值（负边距两栏布局案例：#content{width:100%; margin-right:-200px; float:left} + #sidebar{width:200px; float:left}）
- **边距合并**：普通流中块框垂直边距相遇取较大者（两个 50px 段落间距是 50px 不是 100px）；行内框/浮动/绝对定位不合并
- 块居中经典写法：`margin:0 auto;`
- 浏览器默认样式差异 → 重置：`*{margin:0; padding:0;}`
- border 三要素：颜色/样式/宽度 × 4 方向；样式 none|dotted|dashed|solid|double|groove|ridge|inset|outset（默认 none）；宽度 thin|medium|thick|长度；`border:1px solid black;` 值无顺序要求
- 盒模型也适用行内元素：`a:hover{padding-bottom:3px; border-bottom:1px dotted black;}`（另类悬停下划线）

### KP6.3 文档流与定位机制（6.2.2）
- 文档流：块框从上到下排列（垂直间距由垂直边距算出）；行内框从左到右水平排列（行尾换行）
- 3 种定位机制：**普通流**（默认，相对定位基于它）、**浮动**（从流中移出但内容仍环绕）、**绝对/固定**（完全移出，类似 PS 图层）
- div（自定义块）+ span（自定义行内）配合 id/class 命名；span 应用：导航当前项 `<span class="current">` 加粗不可点
- HTML5 语义标记符：`<header><footer>` 等可替代 `<div id="header">`（现代实践推荐语义化）

### KP6.4 浮动定位（6.2.3）
- 机制："河流绕小岛"——浮动框移出文本流，但其他框的**内容**环绕它；浮动框移到碰到包含框或另一浮动框为止
- `float: left|right|none`（默认 none）
- `clear: left|right|both|none`——both 最常用
- 典型分栏布局（教材标准案例，必掌握）：#box{margin:0 auto} → #header → #sidebar{float:left; 200px} + #main{float:left; 600px} → #footer{clear:both}
- ⚠ footer 不加 clear:both 会被挤到浮动元素旁边（常见错误）

### KP6.5 相对定位（6.2.4）
- `position:relative` + top/left 偏移；**仍在文档流中，原空间保留**，可能覆盖其他元素
- 应用：`a:hover{position:relative; top:2px; left:2px;}` 悬停"按下"效果
- 另一作用：作为后代绝对定位元素的"已定位祖先"参照物

### KP6.6 绝对定位与固定定位（6.2.5）
- `position:absolute`：**完全脱离文档流**（后续元素上移补位）；相对最近的已定位祖先（position≠static）定位，无则相对浏览器窗口左上角/body；生成块级框
- 层级：`z-index` 控制堆叠，**值大者在上**（考试陷阱：不是值小覆盖值大）
- `position:fixed`：同绝对定位但相对**视口**，滚动不移动（顶部固定条、`#totop` 返回顶部按钮案例）
- 绝对定位布局实例要点：#container{position:relative} 作参照 → #main{position:absolute; top:0; left:200px}；#new 相对 #main 定位右上角
- ⚠ 绝对定位参照 body 会随滚动移出视线；fixed 始终相对可见窗口

### KP6.7 分类属性（6.3.1）
- `cursor`：指针形状（wait、pointer、`url(cursor.ico),auto` 自定义）
- `display`：none（不显示**不留空间**）、inline、block、inline-block（横向排列又可设宽高的关键值）
- `visibility: visible|hidden|inherit`：隐藏但**保留空间**——与 display:none 的区别是必考点

### KP6.8 列表属性（6.3.2）
- `list-style-image:url(bullet.gif)` 图片符号；`list-style-position: inside|outside`（默认 outside）；`list-style-type`（disc/circle/square/decimal/upper-roman 等）
- 组合 `list-style`；同时指定 type+image 时，仅图片不可显示才用 type

### KP6.9 特效属性（6.3.3）—— CSS3 亮点，课堂演示效果好
- `border-radius`：1–4 值（左上起顺时针），`/` 分隔水平/垂直半径；`border-radius:50%` 得圆形；100px/50px 椭圆；50px 胶囊
  - ⚠ 教材兼容写法 `-moz-`/`-webkit-` 前缀已过时（现代浏览器无需前缀，讲解时说明即可）
- `box-shadow: h偏移 v偏移 模糊 扩展 颜色 inset`（可多组逗号分隔；正值向右下；inset=内阴影）
- `text-shadow: h v blur color`（霓虹灯 `0 0 3px red`）
- `transition: property duration timing-function delay`（property 和 duration 必填；timing 默认 ease 慢快慢；多组逗号分隔）
- `transform:scale(2,1.5)` 2D 转换（旋转/缩放/移动/倾斜，详见 CSS 标准）

### KP6.10 样式优先级（6.4）—— 考试与调试核心
- 一般规则：**就近优先**（离对象越近优先级越高）；行内 style 属性最高；`<link>` 与 `<style>` 谁近谁优先 → 故 link 在前 style 在后（多个外部表越通用越靠前）；同级冲突**后定义者胜**
- 计算方法 (a,b,c)：a=ID 选择器个数，b=类+伪类+属性选择器个数，c=元素选择器个数；优先级=a×100+b×10+c
  - 例：`*`=0；`li`=1；`ul li`=2；`ul ol+li`=3；`h1+*[rel=up]`=11；`ul ol li.red`=13；`li.red.level`=21；`#box`=100；`#box #bread p`=201
- 继承细节：字号继承后 h1 实际显示 2em×继承值（浏览器样式系数）
- 最佳实践：规则尽量写具体（`#sidebar p` 而非依赖优先级计算）
- 调试工具：Chrome 开发者工具 Ctrl+Shift+I，删除线=被覆盖的属性（教学演示必用）

## 综合实例：中华美食网站（6.5）—— 分层 CSS 架构范例
- 八大菜系栏目；文件结构：根 index.htm + css/ + html/ + images/
- **分层样式表架构（教学方法论重点）**：base.css（全站通用，最先引入）→ index.css / lv1.css / lv2.css（层级样式，依次后引入）→ 页内 `<style>`（覆盖 `#main` 高度等页面差异）
- 技术点密集：顶部固定条 `position:fixed`+z-index:100；#main{position:relative; top:40px} 避让固定条；logo/搜索框/面包屑绝对定位于 #top；**导航条 = ul 列表 + `li{display:inline-block}` + `a{display:block; padding}` + `a#current` 当前栏目标签色**（导航条 CSS 化标准做法）；首页图片 `transition:transform 0.8s` + `a:hover img{transform:scale(1.05)}` 悬停放大；二级页图文交错 float + `<br class="clear"/>` 清浮动；三级页绝对定位右栏（烹饪工艺）
- ⚠ lv2.css 注释：`#box{padding:1px;}` 必须设置，否则 h1 的 margin 影响 #box（边距合并实战坑）

## 反模式
- 依赖优先级数值算样式而不是写具体选择器
- 浮动布局后忘 clear:both
- 混淆 display:none（不留空间）与 visibility:hidden（留空间）
- 以为 z-index 小的在上（实际大的在上）
- 绝对定位忘给祖先设 position:relative（参照物飞了）
- width 当成总宽度（忘了加 padding/border/margin）

## 教材练习题（考核素材）
- 判断：盒模型只能用于块元素（×）；子元素选择器是后代选择器特例（√）；transition 须配合其他属性变化（√）
- 单选：由内而外 padding→border→margin（B）；z-index 值小覆盖值大（D错）；相对定位在文档流中（D）；`border:1px solid black; border-width:1px 2px 3px 4px;` → 上右下左分别为 1/2/3/4px（C，后定义覆盖宽度）
- 填空：元素间距用 margin
- 综合实践（对应教材）：用浮动/定位完善前章网站、分层 CSS

## 验收标准
- 能手算任意选择器的 (a,b,c) 优先级
- 能画出盒模型并计算元素框总尺寸
- 能用浮动+clear 独立实现两栏布局，用 relative+absolute 实现叠加布局，用 fixed 做顶栏
- 能用 ul+display:inline-block 做横向导航条并标出当前栏目
- 能用开发者工具找出样式被谁覆盖

## 关联
- ← ch03（基本选择器/属性）、ch05（表格边框）| → ch07（JS 操作样式）、ch08（设计原则）、ch09（DW 可视化布局）、ch10（项目实战）
