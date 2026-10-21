# 第5章 表格与表单

> 教材定位：第1部分第5章 | 前置：ch01–ch03（HTML 语法、CSS 属性）
> 原文核对：full_text.txt 行5380–7168

## 核心思想
表格组织数据（行列→单元格），表单收集用户输入（控件→提交服务器）。两者都是"功能性对象"：表格偏呈现，表单偏交互。

## 教学目标（教材原文）
- 知识：`<table><caption><tr><td><th>` 及属性；区分三种对齐（表格页面对齐/数据水平/垂直）；表单概念与工作原理；控件类型；`<form><input><label><textarea><select><option><fieldset><legend>`
- 技能：构造表格、CSS 修饰表格、构造表单、标签可用性、CSS 修饰表单
- 素养：信息呈现方式影响理解；交互性是现代媒体关键特征；知行合一

## 知识点

### KP5.1 表格基本构成（5.1.1）
- 标记符：`<table>` 整体 → `<caption>` 标题（直接跟在 table 后，可用 CSS text-align 定位）→ `<tr>` 行 → `<td>` 数据格 / `<th>` 表头格（两者可混用，th 表示行列标题）
- ⚠ 表格默认无边框（演示时加 `border="1"`）；**空单元格不显示边框** → 放 `&nbsp;`
- 教学示例：课程表（th 做行列表头，含 img 单元格）

### KP5.2 合并单元格（5.1.2）—— 学生易错点
- `rowspan="n"` 纵跨 n 行；`colspan="n"` 横跨 n 列
- 规则：跨行/跨列的单元格**只在首次出现的行/位置写**，后续行相应少写单元格（学生情况表：第1行3个 th 占6列）
- ⚠ 判断题考点：表格列数 = 第一行 th/td 的 colspan 之和

### KP5.3 构造表格四步法（5.1.3，教学操作流程）
1. `<table>` 包住全部，需要标题加 `<caption>`
2. 逐行写 `<tr>`（行数 = 垂直方向单元格最大数）
3. 每行内依次写 `<th>/<td>`，跨行用 rowspan（只在首行写）、跨列用 colspan
4. 空单元格填 `&nbsp;`
- ⚠ 复杂表格先在纸上画草图（教材强调）

### KP5.4 边框与分隔线（5.2.1）
- HTML 属性（了解即可）：frame（外框：void/above/below/hsides/vsides/lhs/rhs/box）、rules（分隔线：none/groups/rows/cols/all）、border（px；`border="0"` ⇔ frame=void rules=none）
- **CSS 方式（推荐教学重点）**：`table{border-top/bottom}` + `td,th{border-top}`；table 的 border 是外围框，td/th 的 border 是单元格框

### KP5.5 单元格空白（5.2.2）
- HTML 属性：cellspacing（单元格之间）、cellpadding（框线与数据之间）
- CSS 方式：`border-collapse: collapse|separate`（默认 separate 分离；collapse 合并单框且忽略 border-spacing）；`border-spacing: 水平 垂直`；`padding` 用于 td/th ≈ cellpadding

### KP5.6 三种对齐（5.2.3）—— 区分清楚是考试点
| 对齐对象 | HTML 属性 | CSS 替代（推荐） |
|---|---|---|
| 表格在页面中 | `<table align>`（left/right 会文本环绕） | `table{margin:0 auto;}` 居中；`float:left/right` |
| 数据水平对齐 | tr/td/th 的 align（默认 left） | text-align |
| 数据垂直对齐 | tr/td/th 的 valign（top/middle**默认**/bottom/baseline） | vertical-align |
- ⚠ valign 没有 center 值（垂直居中用 middle）——选择题陷阱

### KP5.7 表单工作原理（5.3.1、5.3.2）
- 表单 = 浏览者与服务器信息交互的页面元素；流程：填写 → 点提交 → 数据按指定方式发到服务器 → 服务器程序处理 → 返回结果页
- 表单 = 普通页面元素 + 控件；控件有 name（作用域为所在表单）、初始值、当前值
- 7 类控件：文本框（单行/密码/多行）、复选框、单选框、按钮（submit/reset/普通）、选项菜单、文件选择框、隐藏控件
- ⚠ 表单需要服务器端程序（PHP/JSP/ASP.NET）支持——超出本书范围；简易方案 `action="mailto:邮箱" enctype="text/plain"`

### KP5.8 `<form>` 标记符（5.3.3）
```html
<form action="服务器端程序url" method="get|post" enctype="type"> ... </form>
```
- ⚠ **表单不能嵌套**，必须有 `</form>`
- method：get（附加在 URL 末尾，默认）vs post（数据包发送，设计者偏好）
- 一页可多表单；每个表单通常必须有提交按钮

### KP5.9 各控件语法（5.4）
- 文本框：`<input type="text" name value size maxlength placeholder />`（type 默认 text）；密码框 `type="password"`（输入显示为圆点）
- 复选框 `type="checkbox"` / 单选框 `type="radio"`；`checked="checked"` 预选；⚠ **同 name 的单选框成组，组内只能选一个**
- 标签可用性：`<label for="控件id">` + 控件 `id` —— 点文字即选中控件（教学演示必选）
- 按钮：submit / reset / button（自定义，可 onclick 执行 JS）；⚠ 实际中很少用 reset；图像按钮 `type="image" src alt`
- 多行文本框：`<textarea rows cols placeholder>默认文本</textarea>`（超出可视区出滚动条）
- 选项菜单：`<select name size multiple="multiple">` + `<option value selected="selected">`；size 默认 1；multiple 允许多选（Ctrl/Shift）
- 分组：`<fieldset><legend>标题</legend>...</fieldset>`

## 综合实例（5.5）
- 复杂表格页（CBA 数据）：`border-collapse:collapse`；`.heading` 黑底白字表头；`.even` 奇偶行变色；**`tr:hover{background:gray;}` 行悬停**（伪类用于非 a 元素的实战）
- 登录页：form 居中盒子 + `border-radius` 圆角 + `box-shadow` 内阴影输入框 + label 关联"记住密码"
- 注册页：fieldset/legend 分组、`input[type="submit"]` **属性选择器**（第6章正式讲）、`display:block` 按钮居中、登录/注册页互链

## 反模式
- 嵌套 `<form>`
- 单选框忘写相同 name（失去互斥）
- 空单元格不写 `&nbsp;` 导致边框缺失
- 用 valign="center"（不存在，用 middle）
- 控件不写 label（可用性差）
- rowspan 跨行后在后续行重复写该单元格（错位）

## 教材练习题（考核素材）
- 判断：表格列数=首行 colspan 之和（√）；垂直对齐默认居中（√）；表单可嵌套（×）；文本框/密码框/复选框都用 input（√）
- 单选：默认水平对齐是 left 不是居中（D错）；valign 无 center；创建文本框 `<input>` 即可；label 正确写法是控件 `id` + label `for`（D）
- 填空：cellpadding；rowspan；`checked="checked"`；value 控制按钮文字
- 综合实践：①日历网页（月份格跨行/列、周末节假日异色、日期格含小图）②表单页（≥4种控件含单选/复选/文本框，全设 label）③互评

## 验收标准
- 能按四步法手写含 rowspan/colspan 的不规则表格且结构不错位
- 能用 CSS 实现斑马纹+悬停行变色表格
- 能做出完整登录/注册表单（label 关联、控件分组、样式修饰）
- 能口述表单提交全过程并区分 get/post

## 关联
- ← ch02（列表/对齐概念）、ch03（CSS）| → ch06（border/padding/float/属性选择器原理）、ch07（JS 表单交互）
