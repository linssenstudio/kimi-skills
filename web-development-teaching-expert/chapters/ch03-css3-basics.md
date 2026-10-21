# 第3章 CSS3基础

> 教材定位：第1部分第3章 | 前置：ch01（head/style 位置）、ch02（文本结构、导航）
> 原文核对：full_text.txt 行2492–4030

## 核心思想
CSS 是 Web 标准的"表现"层：用 `selector{property:value;}` 一次定义、处处生效，实现"内容与表现分离"。本章解决三个问题：**对什么内容**（选择器）、**设什么效果**（属性）、**写在哪里**（三种使用方式）。

## 教学目标（教材原文）
- 知识：CSS 概念与优点；样式表项定义方式；长度/颜色单位；区分站点/网页/行内样式场景；5 种基本选择器；颜色背景/字体/文本属性
- 技能：熟练三种样式使用方式、5 种选择器、color/background 系列、font 系列、line-height/text-align/text-decoration/text-indent
- 素养：理解"结构与表现分离"工程思想；电影欣赏网站（文化多样性）

## 知识点

### KP3.1 为什么用 CSS（3.1.1）—— 课堂导入案例
- 对比演示（教材经典导入）：100 个 `<h1>` 要居中+下划线——HTML 方式需重复 `align="center"`+`<u>` 一百次且难维护；CSS 方式一条 `h1{text-align:center; text-decoration:underline;}` 全解决
- CSS 三大优点：消除重复定义、易于维护（改一处全站更新）、表现力更强（去下划线、图像项目符号、半透明等）
- 大网站场景：外部样式表文件让多页面共享"皮肤"

### KP3.2 样式定义语法与单位（3.1.2、3.1.3）
- 语法：`selector {property1:value1; property2:value2;}` ⚠ 全部英文标点
- CSS 注释：`/* 注释 */`（与 HTML 的 `<!-- -->` 不同，易混点）
- 长度单位：**px、em、% 最常用**（教材明确，其他少用）
- 颜色单位：颜色名（green）、#rrggbb、#rgb、rgb(r,g,b)、rgb 百分比；新版浏览器支持 HSL/HSLA（较少用）。同一绿色的 5 种等价写法可作课堂练习

### KP3.3 三种使用方式与优先级直觉（3.2）—— 考试重点
| 方式 | 写法 | 适用场景 |
|---|---|---|
| 站点样式（外部） | `<link rel="stylesheet" type="text/css" href="mycss.css" />` 在 head | 多页面统一风格，**应用最广** |
| 网页样式（内嵌） | head 内 `<style>` 块 | 仅当前页的独特效 |
| 行内样式 | `<p style="...">` | 仅临时测试，**强烈不建议**（违背分离原则） |
- ⚠ 顺序规则：同时使用时 `<link>` 在前 `<style>` 在后，网页样式才能覆盖站点样式
- .css 文件创建：纯文本文件改扩展名
- 子目录页面链接上级样式表：`href="../mycss.css"`（复习相对路径）

### KP3.4 五种基本选择器（3.3）
1. **标记符选择器**：`a{text-decoration:none;}` 作用于所有该元素；注意块元素作用范围（h2 的 border-bottom 横贯整行宽度，不止文字）
2. **类选择器**：`.center{text-align:center;}` + `class="center"`；可限定 `h1.center`；同类名可被"标记符.类名"复用而互不影响（`h1.fancy` 蓝底白字 vs `.fancy` 红底黄字）
3. **ID选择器**：`#bread{...}` + `id="bread"`；**语义原则：ID=独一无二（单页内唯一），类=类别（多次出现）**——按语义而非视觉效果选择；`div#sidebar` 属画蛇添足
4. **伪类选择器**：`a:link / a:visited / a:hover / a:active`，必须按 **LoVe HAte** 顺序书写避免冲突；`:hover` 也可用于其他元素（如 `p:hover`）；可与类/ID 联合 `a#bread:hover`
5. **群组选择器**：逗号编组 `h1,h2,h3,h4,h5,h6{font-family:楷体;}`
- 块元素 vs 行内元素（重述）：块元素自带换行（h1–h6、p、ul/ol、li、div），行内元素不换行（a、img）

### KP3.5 颜色与背景属性（3.4.1）
- `color` 文本色；`background-color`（默认 transparent）
- `background-image:url(bg.jpg)|none`（默认 none）⚠ url() 不能省
- `background-attachment: scroll|fixed`（fixed=水印效果）
- `background-position`：关键字/百分比/长度，默认 `0% 0%`，单值时垂直取 50%
- `background-repeat: repeat|repeat-x|repeat-y|no-repeat`（默认 repeat 平铺）
- 组合属性 `background`：值顺序任意；⚠ **未指定的值重置为默认**（`h1{background:lightblue;}` 会清掉背景图）——样式冲突隐患，第6章详述

### KP3.6 字体属性（3.4.2）
- `font-family`：字体列表逗号分隔逐级回退（`楷体,黑体`）；多词字体名加引号 `"Times New Roman"`；字体族：cursive/fantasy/monospace/serif/sans-serif
- `font-size`：绝对（xx-small…xx-large，默认 medium）、相对（smaller/larger 相对上级）、长度（px/em）、百分数
- `font-style: normal|italic|oblique`；`font-variant: small-caps`
- `font-weight: normal|bold|bolder|lighter|100–900`（normal=400, bold=700；实际系统常只有两档）
- 组合 `font` 规则（考试易错）：`[style|variant|weight]? size[/line-height]? family`——**size 和 family 必须有且 size 在前**；`font:20px;` ❌ `font:bold small-caps;` ❌

### KP3.7 文本属性（3.4.3）
- `line-height`：数字（倍数，如 1.5）、长度、百分数
- `text-align: left|right|center|justify`（CSS 版 align）
- `text-decoration: none|underline|overline|line-through|blink`（blink 有浏览器不支持）；可叠加 `underline overline`
- `text-indent:2em` = 中文首行缩进两字（高频实用点）

## 综合实例：电影欣赏网站（3.5）—— CSS 化多页网站
- 信息架构：根目录 index.htm + css.css；html/ 与 images/ 两个文件夹；5 栏目（剧情/动画/科幻/动作/悬疑）
- 视觉设计模式（可复用教学案例）：`#box{width:80%; margin:0 auto;}` 页面盒子居中；`#nav` 主导航背景+大字；`a{text-decoration:none}` + `a:hover{underline+red}`；**不同栏目用不同背景色区分**（网页样式 `<style>#box{background:lightyellow;}</style>` 覆盖站点样式）
- css.css 完整样式表（教材原文，含 #box/#nav/#bread/h1/h2/a/a:hover/.banner/.pics/.intro/.lastline）
- 面包屑下划线用 `border-bottom:1px black dotted`（非 text-decoration，第6章原理）

## 反模式
- 行内样式当常规手段（只许临时测试）
- `<link>` 写在 `<style>` 之后（覆盖顺序反了）
- `background-image:bg.jpg` 漏写 url()
- `font` 组合属性缺 size/family
- 按视觉效果选 class 还是 id（应按语义）
- CSS 里用 HTML 注释 `<!-- -->`

## 教材练习题（考核素材）
- 判断：颜色方法超3种（√）；`p{text-indent:2em;}` 缩进两字（√）；去下划线选择器是 a（√）；三种样式中站点样式最重要（√）
- 单选：伪类可与类联合使用（D错）；`p{font:italic bold 24px;}` 不能工作（缺 family）；`p{background:url(bg.jpg) fixed;}` 正确
- 填空：水印效果→background-attachment；px、em、%；line-height 可取数字/长度/百分数
- 综合实践：①给唐诗宋词网站加 CSS（站点样式+页内样式+4类选择器）②补全电影欣赏网站 ③两人互评（组员须与上次不同）

## 验收标准
- 能为既有 HTML 网站写外部样式表并正确链接（含子目录 `../` 路径）
- 能正确使用 5 种选择器并说明各自语义场景
- 能默写 LoVe HAte 顺序并解释原因
- 能用 font 组合属性写出合法规则并指出非法写法

## 关联
- ← ch02（被美化的网站骨架）| → ch06（高级选择器、盒模型、定位、优先级计算）、ch04（图像配合）
