# 第1章 HTML5基础

> 教材定位：第1部分"网页制作基础"第1章 | 前置：无（零基础入口章）
> 原文核对：full_text.txt 行162–1210（提取自 PDF 第1章）

## 核心思想
HTML 用标记符（tag）和属性（attribute）定义网页结构；浏览器按"请求—响应"模式从服务器获取 HTML 并解析显示。本章让学生从零写出第一个完整网页。

## 教学目标（教材原文）
- 知识目标：理解 Internet/WWW/网站/网页概念；HTML 标记符与属性语法；Web 标准；掌握 `<html><head><title><meta><body>`；注释与特殊字符
- 技能目标：用记事本+浏览器完成"编写—保存—双击测试—修改—再保存"闭环；创建基本网页结构并添加文本/图像/注释/特殊字符
- 素养目标：信息素养；做中学；传统文化认同（人物介绍网页实例）

## 知识点

### KP1.1 Internet、WWW 与浏览器-服务器原理（1.1.1）
- 概念：Internet 是以 TCP/IP 连接的全球数据通信网；WWW 只是 Internet 的服务之一（≠Internet），由 Web 服务器组成，通过浏览器浏览
- 工作过程（讲授板书用）：输入地址 → 浏览器发出"请求" → 服务器"响应" → 网页传回 → 浏览器显示；点击超链接重复此过程
- 网站 = 逻辑上视为整体的网页集合；主页通常为 index.htm / index.html
- 常用浏览器：Chrome（本书默认）、Safari、Edge、Firefox
- 课堂提问：WWW 和 Internet 是不是一回事？（不是，WWW 是 Internet 的服务之一）

### KP1.2 HTML 本质与 Web 标准（1.1.2）
- HTML（HyperText Markup Language）是表示网页的规范，用标记符定义内容显示；超文本的特征是包含指向其他位置的链接（网状结构）
- Web 标准三部分（考试高频）：**结构** Structure（HTML/XML/XHTML）→ **表现** Presentation（CSS，第3/6章）→ **行为** Behavior（DOM/BOM/JavaScript，第7章）
- 课堂演示：浏览器右键"查看网页源代码"展示 HTML 本质
- HTML 版本脉络：HTML3.2 → HTML4.0/4.01 → XHTML1.0/1.1 → HTML5（本书以 HTML5 为准）

### KP1.3 创建与测试网页流程（1.1.3）—— 实操核心
- 操作流程（Windows 10 为例）：记事本输入代码 → 另存为 `.htm`/`.html` → 双击用 Chrome 打开测试 → 右键"打开方式>记事本"修改 → **保存后更改才生效** → 刷新重测
- 文件命名规范：只用英文字母、数字、下划线；名称要有含义（`xinqiji.htm` 好，`file1.htm` 差）
- 工具分类：HTML 编辑器（VS Code、Notepad++、Sublime Text、UltraEdit、Xcode）；所见即所得编辑器（Dreamweaver，第9章）
- 常见错误：忘记保存就刷新；文件名无扩展名或存成 .txt

### KP1.4 标记符语法（1.2.1）
- 语法规则：标记符用 `<>` 括起；绝大多数成对出现（`<h1>...</h1>`），结束标记符多一个 `/`；少数单标记符如 `<br>`
- 属性写法：放在开始标记符内，与标记符空格分隔；`属性="值"`（双引号成对）；多属性间空格分隔。例：`<a href="target.htm" title="点击有惊喜">超链接</a>`
- HTML5 约定标记符小写（不区分大小写但建议小写）
- ⚠ 中英字符陷阱：`<`、`>`、引号必须是英文字符，中文标点会出错（课堂必讲）
- 元素四分类：**顶级元素**（html/head/body）、**首部元素**（title/style/link/meta/base/script）、**块元素**（h1–h6/p/pre/div/ul/ol/dl/table/form + HTML5 新增 article/section/nav，显示时另起一行）、**行内元素**（a/br/img/em/strong/sub/sup/code/var/span）
- 全局属性：id（唯一）、class、style、title（工具提示）、lang

### KP1.5 网页基本结构（1.2.2）
- 最小骨架：`<html>` → `<head>`（`<title>` 必有；`<meta>` 元信息）+ `<body>`（实际内容）
- `<title>` 显示在浏览器标签页，用作书签；要有意义（"新浪首页"而非"首页"）
- `<meta>` 常用：`<meta charset="UTF-8">`（HTML5 写法，解决中文乱码）；name="keywords"/"description"（SEO）；旧写法 `http-equiv="Content-Type" content="text/html; charset=UTF-8"`
- ⚠ 已废弃：`<body>` 的 bgcolor/background 等视觉属性在 HTML5 中废弃 → 用 CSS（第3/6章）
- 嵌套规则：标记符必须闭合、嵌套关系清晰；浏览器会"智能容错"错误代码，但必须教学生写规范代码
- 结构树心智模型：所有标记符构成树——html 为根，head/body 为子，块元素含行内元素

### KP1.6 添加内容、注释与特殊字符（1.2.3）
- 素材准备：文本去除格式后放 `<p>`；图像改有意义的文件名
- 注释：`<!-- 注释 -->`，不在浏览器显示；是代码可维护性的基本规范
- 参考字符（字符实体）：`&` 开头 `;` 结尾，**名称区分大小写**。常用：`&lt;` `&gt;` `&amp;` `&nbsp;`（空格）
- 示例：显示 `<Tom & Jerry>` → `<p> &lt;Tom &amp; Jerry&gt; is a popular show. </p>`

## 综合实例：人物介绍网页（1.3，课堂演示/学生模仿）
制作《古剑奇谭》百里屠苏介绍页。核心代码结构（教材原文，含注释教学）：
```html
<html>
<head><title>百里屠苏简介</title></head>
<body>
<h1>百里屠苏<img src="百里屠苏.jpg" align="right"></h1>
<h2>简介</h2>
<hr>
<p>上海烛龙研发的单机游戏《古剑奇谭：琴心剑魄今何在》第一男主角……</p>
<h2>人物关系</h2>
<hr>
<p>父亲：百里巫祝<br>母亲：韩休宁<br>师尊：紫胤真人</p>
</body>
</html>
```
- 演示要点：h1–h6 建文档逻辑结构；`<hr>` 分割线；`<br>` 段内换行；`<img src align>` 插图
- ⚠ 注意：img 的 align 属性已属废弃写法（教材在第2章明确说明），现代替代：CSS float/布局

## 反模式（教学生避免）
- 用记事本保存成 `.txt`（应另存为 `.html`）
- 标记符/引号用中文字符
- 嵌套交叉错误：`<body><h1><span>...</h1></span></body>`（浏览器能容错但属错误代码）
- 改完代码不保存就刷新浏览器
- 网页标题写成"首页"这类无意义文字
- 用 body 的 bgcolor 等废弃属性设置外观

## 教材练习题（可核对的考核素材）
- 客观题样例：①"可以用文本编辑器编辑HTML文件"（√）②"title标记符与title属性含义相同"（×）③ `<meta charset="UTF-8">` 可解决中文乱码（√）④不属于全局属性的是 size ⑤空格参考字符是 `&nbsp;` ⑥表现对应技术是 CSS
- 问答题：WWW 工作原理；HTML 工作原理；Web 标准组成
- 综合实践：①选题并写网站规划报告（目标/观众/内容/组织）②仿 1.3 制作人物介绍网页

## 验收标准（学完能做什么）
- 能用记事本独立写出含 html/head/title/meta charset/body/h1/p/img/注释 的完整网页并在浏览器成功打开
- 能口述"请求—响应"过程和 Web 标准三部分
- 能正确使用 `&lt;` `&gt;` `&amp;` `&nbsp;`

## 关联
- → ch02（文本格式与超链接深化 h/p/br 用法）、ch03（CSS 表现层）、ch04（img 详解）、ch07（行为层）
