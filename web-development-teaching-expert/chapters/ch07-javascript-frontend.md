# 第7章 JavaScript与前端开发技术

> 教材定位：第2部分第2章 | 前置：ch01（script 标记符）、ch05（表单）、ch06（样式操作）
> 原文核对：full_text.txt 行10094–13808 | 全书最长章

## 核心思想
JavaScript 是 Web 标准的"行为"层。主线：**三种引入方式 → 语言基础（变量/运算符/语句/函数）→ 三类对象（JS 对象/BOM/DOM）→ 前端框架（jQuery/Bootstrap/Vue/AngularJS/React）**。素养线：标记语言 vs 编程语言的差异；面向对象思想的演化。

## 教学目标（教材原文）
- 知识：客户端脚本概念；JS 变量/运算符/条件/循环/函数；对象属性与方法；对比 JS 对象、浏览器对象、文档对象；jQuery 语法；Bootstrap 使用
- 技能：3 种脚本引入；编写基本 JS 程序；三类对象编程；安装使用 jQuery 增交互；安装使用 Bootstrap 快速建站
- 素养：HTML/CSS/JS 对比；精益求精；面向对象思想演化；"工欲善其事必先利其器"

## 知识点

### KP7.1 客户端脚本与三种引入方式（7.1）
- 概念：脚本可在服务器端（PHP/ASP）或浏览器端运行；客户端脚本用于检测浏览器、响应动作、验证表单、自定义内容；优势：不依赖网络通信，降低传输量与服务器负荷
- 三种方式（考试点）：
  1. **`<script>` 内嵌**：建议放 head 便于维护；`function showmsg(){ alert("Hello World!"); }` + `<button onclick="showmsg();">`
  2. **直接添加**（事件属性内联）：`<p onclick="alert('Hello World!')">`
  3. **外部文件**：`<script src="test.js"></script>`（复用；⚠ 用了 src 则标记符内部脚本被忽略；.js 是纯文本文件）
- 入门演示：`alert("Hello World!")`

### KP7.2 JS 语言基础（7.2.1）
- 变量：`var` 声明；**弱类型**（类型由赋值隐式确定，可换类型再赋）；**区分大小写**（today≠Today）；不声明直接用会自动声明但不建议
- 数据类型：Number（64位 IEEE754，含 NaN）、Boolean、String、Null、Undefined、Object（Array/Date 等）
- 运算符 8 类：算术（+ - * / % ++ --）、逻辑（&& || !）、比较（**`==` 先类型转换再比 vs `===` 严格等于不转换**）、字符串（+ 接合）、位、赋值（= += -= 等）、条件（`?:` 唯一三目）、其他（`.` 成员、`[]` 索引、`()` 调用、delete/new/typeof/void）
- 单目/双目/三目（一元/二元/三元）
- 条件语句：if / if else / else if 链 / switch（⚠ case 后多条语句也**不加**大括号；⚠ 忘写 `break` 会贯穿下一 case）
- 循环：for（初始化;条件;调整 三部分分号分隔）/ while / do while（**至少执行一次**——与 while 的唯一区别）；break 跳出；continue 跳当次；⚠ 控制结束条件防死循环
- 函数：`function name(p1,p2){...}` 通常放 head 先定义后使用；`return` 返回值（无 return 返回不确定值）
- 注释：`//` 单行、`/* */` 多行
- 综合示例（教材）：`cal(a,b)` 函数 + document.write 演示 if/while/for；⚠ 辨析 `while(i=1)`（赋值，死循环）vs `while(i==1)`（比较）；cal(2,3) 走 `a<b` 分支返回 `(++a)*b=3*3=9`

### KP7.3 JavaScript 对象（7.2.2）
- 对象 = 属性（特性数据）+ 方法（操作函数）；用 `.` 层层引用；三类可操作对象：JS 对象、浏览器对象（BOM）、文档对象（DOM）
- **Array**：三种构造 `new Array()` / `new Array(10)` / `new Array(0,1,2)`，或 `var a=[0,1,2]`；**索引从 0 开始**；长度自动扩充（order[20]=x 扩到 21，中间填 null）；元素可混合类型可嵌套（二维数组）；`.length`；二维数组+嵌套 for 输出表格是经典课堂示例
- **Date**：四种构造（空=当前）；⚠ 月份 0=1 月；getDate/getDay(0=周日)/getHours/getMonth/getTime 等；时段问候语示例（if else if 链 + arrayDay 数组）
- **Math**：无需构造，静态：Math.PI/E/SQRT2、abs/pow/random()/round/sqrt
- **String**：`var txt="string"`；`.length`；charAt/indexOf/includes/replace/slice/split/toLowerCase/toUpperCase/trim；转义字符 `\' \" \\ \n \r \t`

### KP7.4 浏览器对象 BOM（7.2.3）
- BOM 让 JS 与浏览器"对话"；**window 是顶级对象**（全局变量/函数自动成为 window 成员）
- `window`：属性与方法见教材表7-1/7-2；window.open() 开窗口
- `screen`：width/height/availWidth/availHeight/colorDepth/pixelDepth
- `location`：href/protocol/host/pathname/search 等；方法 assign()（可后退）/reload()/replace()（不可后退）；`location.href='url'` ≈ assign —— **用 JS 实现超链接**（考试填空）
- `history`：back()/forward()/go(±n)
- `navigator`：appName/userAgent/cookieEnabled/platform 等

### KP7.5 文档对象 DOM（7.2.4）—— 教学核心
- DOM 是 W3C 标准：独立于平台和语言的接口，动态访问更新文档内容、结构、样式
- 节点树：document=根节点；元素节点/属性节点/文本节点/注释节点；parent/child/sibling 关系
- **document 对象**：代表当前文档（HTML 文档根节点）；访问元素方法：`getElementById()`、`getElementsByClassName()`、`getElementsByTagName()`、`querySelector()`、`querySelectorAll()`；集合属性 forms/images/links
- 元素对象：遍历 parentNode/firstChild/lastChild/nextSibling/children；内容样式 innerHTML/textContent/style；改树 appendChild/removeChild/replaceChild/insertBefore
- ⚠ `document.write()` 输出到网页 vs `console.log()` 输出到控制台（调试用后者）
- 动态改背景实例：`document.body.style.backgroundColor=document.getElementById("myBGColor").value`（JS 里 CSS 属性名转驼峰）
- **事件三种绑定方式**：① HTML 属性 `onclick="..."` ② JS 事件属性 `elementObject.onXXX=function(){...}` ③ `addEventListener("click", handler)`（⚠ 事件名无 "on"）
- 事件参数 e：screenX/screenY、clientX/clientY、keyCode + String.fromCharCode()
- **Tab 导航综合实例**（教材 7.2.4 节，HTML+CSS+JS 协同的标杆案例）：ul 浮动 li 做标签头（圆角+相对定位错位 1px 遮边框），div 内容区 `display:none`，`onmouseover="tab(this,i)"` 切换：循环隐藏全部 → 当前显示 + 标签下边线变白

### KP7.6 jQuery（7.3.1）
- 轻量级 JS 函数库：元素选取/操作、CSS 操作、事件、特效动画、DOM 遍历、AJAX
- 安装：下载 jquery-3.4.1.min.js 复制到站点目录，`<script src="...">` 引用；生产压缩版 vs 开发版
- 基本语法：`$(selector).action()`；所有代码包在 `$(document).ready(function(){...})` 中（防文档未加载完就执行），简写 `$(function(){...})`
- 选择器基于 CSS 选择器 + 扩展（`:first` vs `:first-child` 区别示例）
- HTML/CSS 方法：append/attr/css/html/remove/text；事件方法：click/dblclick/mouseenter/mouseleave/hover/keypress/blur/change/submit/focus
- 动画：hide/show/toggle/fadeIn/fadeOut/fadeToggle/slideUp/slideDown/slideToggle/animate({left:'250px',opacity:'0.5'})/delay/stop
- 复杂 UI 可用 jQuery UI（Tab、折叠面板等）
- ⚠ 技术时效：jQuery 在新项目中使用减少，但教学价值（选择器+链式调用思想）仍在；现代替代：原生 querySelector + fetch

### KP7.7 Bootstrap（7.3.2）—— 响应式教学入口
- 前端框架 = 集成预置代码的 Web 开发工具；用 Bootstrap = 在 HTML 中引用其 CSS/JS + 使用预定义类
- 安装：下载 dist 包解压改名 bootstrap 放站点目录；模板含 `<meta name="viewport" content="width=device-width, initial-scale=1">`（**响应式关键**）
- **网格系统**：响应式、移动优先、最多 12 列；container（固定宽）/container-fluid（全屏）→ row → col-*-*（第1个 *=sm/md/lg/xl 设备断点，第2个 *=列数，同行和为 12）；多类名空格分隔 `class="col-sm-3 col-md-6"`
- 格式类：display-1～4、font-weight-bold、text-left/center/right、text-uppercase、list-unstyled、list-inline、text-primary/success/danger…、bg-primary…
- 组件：nav-tabs 选项卡、navbar 可折叠导航栏（navbar-toggler + collapse）、dropdown 下拉菜单、accordion 折叠栏、carousel 轮播图
- ⚠ 教材用 4.4.1；当前为 Bootstrap 5（data-toggle→data-bs-toggle、不再依赖 jQuery），教学时可说明版本差异

### KP7.8 Vue.js（7.3.3）
- 渐进式框架，只关注视图层；直接当 JS 库引用即可入门
- 基本结构：`new Vue({ el:'#app', data:{message:'Hello Vue!'} })` + 视图 `{{ message }}`（Mustache 语法）；**响应式**：控制台改 `app.message` 页面自动更新（课堂演示亮点）
- 指令 v-*：v-bind（简写 `:`，绑属性）、v-on（简写 `@`，监听事件）、v-model（表单双向绑定）、v-html（解释为 HTML）
- methods 定义方法；`@click.prevent` 修饰符阻止默认行为

### KP7.9 AngularJS 与 React（7.3.4、7.3.5，了解层次）
- AngularJS：ng-* 指令扩展 HTML（ng-app/ng-model/ng-bind/ng-init/ng-repeat/ng-controller/ng-click）；`{{表达式}}`；三部分 View/Model/Controller + $scope + angular.module()；待办清单实例（ng-repeat + ng-submit + 数组 push/过滤）
- React：声明式 UI 库；引用 react/react-dom/babel 三个 JS；根 DOM 节点 + `ReactDOM.render()`；**JSX**（JS 中写类 HTML，表达式写 `{}` 中；样式用对象驼峰属性）；函数组件 `function HelloMessage(props){return <h1>...</h1>}`
- ⚠ 技术时效：AngularJS（1.x）已停止官方支持（2022 年初 EOL），现代教学应区分 AngularJS≠Angular；React 的 ReactDOM.render 在 React 18 已被 createRoot 取代。建议课堂以 Vue 为主、React 概念为辅，AngularJS 仅作技术演化史介绍

## 反模式
- 用 `=` 当比较（`while(i=1)` 死循环）
- switch 漏 break
- 脚本引了 src 还在 `<script>` 内写代码（被忽略）
- addEventListener 事件名写成 "onclick"（应为 "click"）
- DOM 操作写在元素渲染之前（未 ready）
- 数组当从 1 开始索引
- 用 document.write 调试（应 console.log）

## 教材练习题（考核素材）
- 判断：JS 变量区分大小写（原题"不区分"为×）；++ 是单目（√）；getElementById 只有 document 有（√，元素对象没有）；jQuery 和 Bootstrap 都提供 JS 代码库（√）
- 单选：while 与 do while 无区别（B错，do while 至少一次）；cal(2,3)=9；`getElementsByClass` 不存在（C错，应为 getElementsByClassName）
- 填空：document 对象代表当前网页；for(j=4;j>1;j--) 输出 432；JS 超链接 `location.href`
- 问答：3 种插入脚本方式；for/while/do while 对比；BOM vs DOM；访问 DOM 元素的 3+ 种方法
- 综合实践：①把 Tab 导航移植到自己的网站并改写 ②用 jQuery+Bootstrap 构建响应式网站

## 验收标准
- 能用三种方式引入脚本并说明适用场景
- 能手写 if/switch/for/while 和带参函数，预测 cal(2,3)=9 类代码输出
- 能用 getElementById + innerHTML/style 完成 DOM 交互小功能
- 能独立复现 Tab 导航
- 能用 Bootstrap 网格做出 12 列响应式布局
- 能解释 Vue 的 el/data/{{}}/v-model

## 关联
- ← ch01（Web 标准行为层预告）、ch05（表单验证场景）、ch06（style 操作）| → ch09（DW 中用 jQuery/Bootstrap）、ch10（综合项目）
