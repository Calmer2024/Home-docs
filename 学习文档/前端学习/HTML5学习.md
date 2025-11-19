# HTML5学习

> HTML 超文本标记语言——HyperText Markup Language

## HTML框架

```html
<html>
  <head>
    <title>网页标题</title>
  </head>
  <body>
    网页主体
  </body>
</html>
```

* html：整个网页
* head：网页头部，用来存放给浏览器看的信息，例如 CSS
  * title：网页标题
* body：网页主体，用来存放给用户看的信息，例如图片、文字

> [!NOTE]
>
> VS Code 可以快速生成骨架：在 HTML 文件（.html）中，!（英文）配合 Enter / Tab 键

## 注释

```html	
<!-- 我是 HTML 注释 -->
```

## 标题

```html
<h1>一级标题</h1>   <!-- 独占一行 -->
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
```

> [!NOTE]
>
> h1 标签在一个网页中只能用一次，用来放新闻标题或网页的 logo

## 段落

```html
<p>段落</p>   <!-- 独占一行 -->
```

## 换行和水平线

```html
<br>
<hr>
```

## 文本格式化

```html
<!-- 加粗 -->
<strong></strong>
<b></b>
<!-- 倾斜 -->
<em></em>
<i></i>
<!-- 下划线 -->
<ins></ins>
<u></u>
<!-- 删除线 -->
<del></del>
<s></s>

<!-- 常用上面一种格式 -->
```

## 图像

```html
<!-- 基本格式与属性参数 --> 
<img src="图片的URL" alt="图片未能正常加载时显示的文字" title="光标悬浮时显示文字">
```

## 路径

概念：路径指的是查找文件时，从**起点**到**终点**经历的**路线**。 

**相对路径：**

查找方式：从**当前文件位置**出发查找目标文件

特殊符号：

* **/** 表示进入某个文件夹里面          → 文件夹名/
* **. ** 表示当前文件所在文件夹           → ./
* **..** 表示当前文件的上一级文件夹 → ../   

**绝对路径：**

查找方式：Windows 电脑从盘符出发；Mac 电脑从根目录（/）出发

```html
<img  src="C:\images\mao.jpg">
```

> [!NOTE]
>
> 1. Windows 默认是 \ ，其他系统是 /，建议统一写为 / 
> 2. 特殊的绝对路径 → 文件的在线网址：<https://www.itheima.com/images/logo.png> "，应用场景：网页底部**友情链接**

## 超链接标签

```html
<a href="https://www.baidu.com/">跳转到百度</a>

<!-- 跳转到本地文件：相对路径查找 --> 
<!-- target="_blank" 新窗口跳转页面 --> 
<a href="./01-标签的写法.html" target="_blank">跳转到01-标签的写法</a>

<!-- 开发初期，不知道超链接的跳转地址，href属性值写#，表示空链接，不会跳转 -->
<a href="#">空链接</a>
```

## 音频

```html
<!-- 在 HTML5 里面，如果属性名和属性值完全一样，可以简写为一个单词 -->
<audio src="./media/music.mp3" controls loop autoplay></audio>
```

**常用属性**

| 属性     | 作用             | 特殊说明                                   |
| -------- | ---------------- | ------------------------------------------ |
| src      | 音频URL          | 支持格式：MP3、Ogg、Wav                    |
| controls | 显示音频控制面板 |                                            |
| loop     | 循环播放         |                                            |
| autoplay | 自动播放         | 为了提升用户体验，浏览器一般会禁用自动播放 |

## 视频

```html
<!-- 在浏览器中，想要自动播放，必须有 muted 属性 -->
<video src="./media/vue.mp4" controls loop muted autoplay></video>
```

**常用属性**

| 属性     | 作用             | 特殊说明                                   |
| -------- | ---------------- | ------------------------------------------ |
| src      | 视频URL          | 支持格式：MP4、WebM、Ogg                   |
| controls | 显示视频控制面板 |                                            |
| loop     | 循环播放         |                                            |
| muted    | 静音播放         |                                            |
| autoplay | 自动播放         | 为了提升用户体验，浏览器仅支持静音自动播放 |



## 列表 

### 无序列表

```html
<ul>
  <li>第一项</li>
  <li>第二项</li>
  <li>第三项</li>
  ……
</ul>
```

- 作用：布局排列整齐的**不需要规定顺序**的区域。

- 标签：ul 嵌套 li，ul 是无序列表，li 是列表条目。

> [!NOTE]
>
> * ul 标签里面只能包裹 li 标签
> * li 标签里面可以包裹任何内容

### 有序列表

```html
<ol>
  <li>第一项</li>
  <li>第二项</li>
  <li>第三项</li>
  ……
</ol>
```

- 作用：布局排列整齐的**需要规定顺序**的区域。

- 标签：ol 嵌套 li，ol 是有序列表，li 是列表条目。

### 定义列表

```html
<dl>
  <dt>列表标题</dt>
  <dd>列表描述 / 详情</dd>
   ……
</dl>
```

> [!NOTE]
>
> * dl 里面只能包含dt 和 dd
> * dt 和 dd 里面可以包含任何内容



## 表格

### 基本使用

| 标签名 | 说明           |
| ------ | -------------- |
| table  | 表格           |
| tr     | 行             |
| th     | **表头**单元格 |
| td     | **内容**单元格 |

```html
<table border="1">
  <tr>
    <th>姓名</th>
    <th>语文</th>
    <th>数学</th>
    <th>总分</th>
  </tr>
  <tr>
    <td>张三</td>
    <td>99</td>
    <td>100</td>
    <td>199</td>
  </tr>
  <tr>
    <td>李四</td>
    <td>98</td>
    <td>100</td>
    <td>198</td>
  </tr>
  <tr>
    <td>总结</td>
    <td>全市第一</td>
    <td>全市第一</td>
    <td>全市第一</td>
  </tr>
</table>
```

- 标签：table 嵌套 tr，tr 嵌套 td / th
- 提示：在网页中，**表格默认没有边框线**，使用 **border 属性**可以为表格添加边框线。

### 表格结构标签

> 表格结构标签可以省略

| 标签名 | 含义     | 特殊说明     |
| ------ | -------- | ------------ |
| thead  | 表格头部 | 表格头部内容 |
| tbody  | 表格主体 | 主要内容区域 |
| tfoot  | 表格底部 | 汇总信息区域 |

### 合并单元格

**合并单元格的步骤：**

1. 明确合并的目标
2. 保留**最左最上**的单元格，添加属性（取值是**数字**，表示需要**合并的单元格数量**）
   * **跨行合并**，保留最上单元格，添加属性 **rowspan**
   * **跨列合并**，保留最左单元格，添加属性 **colspan**
3. 删除其他单元格

```html
<table border="1">
  <thead>
    <tr>
      <th>姓名</th>
      <th>语文</th>
      <th>数学</th>
      <th>总分</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>张三</td>
      <td>99</td>
      <td rowspan="2">100</td>
      <td>199</td>
    </tr>
    <tr>
      <td>李四</td>
      <td>98</td>
      <!-- <td>100</td> -->
      <td>198</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>总结</td>
      <td colspan="3">全市第一</td>
      <!-- <td>全市第一</td>
      <td>全市第一</td> -->
    </tr>
  </tfoot>
</table>
```

> [!NOTE]
>
> 注意：不能跨表格结构标签合并单元格（thead、tbody、tfoot）。



## 表单

> **作用**：收集用户信息
>
> **使用场景**：
>
> * 登录页面
> * 注册页面
> * 搜索区域

### input 标签

```html
<input type="..." >
```

| type 属性值 | 说明                     |
| ----------- | ------------------------ |
| text        | 文本框，用于输入单行文本 |
| password    | 密码框                   |
| radio       | 单选框                   |
| checkbox    | 多选框                   |
| file        | 上传文件                 |
| search      | 有删除搜索内容按钮       |

### input 标签占位文本

```html
<input type="..." placeholder="提示信息">
```

> [!NOTE]
>
> 占位文本：提示信息，文本框和密码框都可以使用

### 单选框

| 属性名  | 作用     | 特殊说明                               |
| ------- | -------- | -------------------------------------- |
| name    | 控件名称 | 控件分组，同组中只能选一个（单选功能） |
| checked | 默认选中 |                                        |

```html
<input type="radio" name="gender" checked> 男
<input type="radio" name="gender"> 女
```

> [!NOTE]
>
> name属性值自定义

### 上传文件

```html
<input type="file" multiple>
```

默认情况下，文件上传表单控件只能上传一个文件，添加 multiple 属性可以实现文件多选功能

### 多选框

```html
<input type="checkbox" checked> 敲前端代码
```

多选框也叫复选框，默认选中：checked

### 下拉菜单

标签：select 嵌套 option，select 是下拉菜单整体，option是下拉菜单的每一项

```html
<select>
  <option>北京</option>
  <option>上海</option>
  <option>广州</option>
  <option>深圳</option>
  <option selected>武汉</option>
</select>
```

默认显示第一项，**selected** 属性实现**默认选中**功能。

### 文本域

作用：多行输入文本的表单控件

```html
<textarea>默认提示文字</textarea>
```

> [!NOTE]
>
> * 实际开发中，使用 CSS 设置 文本域的尺寸
> * 实际开发中，一般禁用右下角的拖拽功能

### label标签

作用：网页中，某个标签的说明文本

经验：用 label 标签绑定文字和表单控件的关系，增大表单控件的点击范围

* **写法一**
  * label 标签只包裹内容，不包裹表单控件
  * 设置 label 标签的 for 属性值 和表单控件的 id 属性值相同

```html
<input type="radio" id="man">
<label for="man">男</label>
```

* **写法二**
  * 使用 label 标签包裹文字和表单控件，不需要属性 


```html
<label><input type="radio"> 女</label>
```

> [!NOTE]
>
> 支持 label 标签增大点击范围的表单控件：文本框、密码框、上传文件、单选框、多选框、下拉菜单、文本域等等。

### 按钮

```html
<button type="">按钮</button>
```

| type 属性值 | 说明                                           |
| ----------- | ---------------------------------------------- |
| submit      | 提交按钮，点击后可以提交数据到后台（默认）     |
| reset       | 重置按钮，点击后将表单控件恢复默认值           |
| button      | 普通按钮，默认没有功能，一般配合JavaScript使用 |

```html
<!-- form 表单区域 -->
<!-- action="" 发送数据的地址 -->
<form action="">
  用户名：<input type="text">
  <br><br>
  密码：<input type="password">
  <br><br>

  <!-- 如果省略 type 属性，功能是 提交 -->
  <button type="submit">提交</button>
  <button type="reset">重置</button>
  <button type="button">普通按钮</button>
</form>
```

> [!NOTE]
>
> 按钮需配合 form 标签（表单区域）才能实现对应的功能。

### form标签

HTML 的 `<form>` 标签用于创建用户输入的交互式表单，是网页与用户进行数据交互的核心组件。

---

**基本作用**

- **数据收集**：通过表单内的输入控件（如文本框、下拉框、按钮等）收集用户输入。
- **数据提交**：将用户输入的数据发送到服务器（通过 HTTP GET 或 POST 方法）。
- **客户端验证**：利用 HTML5 或 JavaScript 对输入数据进行初步校验。

**基本结构**

```html
<form action="/submit-url" method="POST" enctype="application/x-www-form-urlencoded">
  <!-- 表单控件（如 input、textarea、select 等） -->
  <input type="text" name="username" required>
  <button type="submit">提交</button>
</form>
```
- **`action`**：指定提交数据的服务器端 URL（后端接口）。
- **`method`**：定义数据提交的 HTTP 方法（`GET` 或 `POST`）。
  - `GET`：数据通过 URL 参数传递（可见，适合非敏感数据）。
  - `POST`：数据通过请求体传递（不可见，适合敏感数据或大量数据）。
- **`enctype`**：定义数据编码方式，常见值：
  - `application/x-www-form-urlencoded`（默认，普通文本数据）。
  - `multipart/form-data`（文件上传时必须使用）。

**常见表单控件**

- **输入控件**
  - **`<input>`**：根据 `type` 属性生成不同类型的输入：


```html
<input type="text" name="username" placeholder="用户名">       <!-- 文本输入 -->
<input type="password" name="password">                      <!-- 密码输入 -->
<input type="email" name="email" required>                  <!-- 邮箱（HTML5） -->
<input type="number" name="age" min="18" max="100">         <!-- 数字（HTML5） -->
<input type="date" name="birthday">                         <!-- 日期选择（HTML5） -->
<input type="file" name="avatar" accept="image/*">           <!-- 文件上传 -->
<input type="checkbox" name="subscribe" checked>            <!-- 复选框 -->
<input type="radio" name="gender" value="male">             <!-- 单选框 -->
<input type="submit" value="提交">                          <!-- 提交按钮 -->
```

- **其他控件**

  - **`<textarea>`**：多行文本输入：

  ```html
  <textarea name="message" rows="4" cols="50"></textarea>
  ```

  - **`<select>`**：下拉选择框：

  <select name="country">
    <option value="cn">中国</option>
    <option value="us">美国</option>
  </select>

  - **`<button>`**：按钮（默认 `type="submit"`，可设置为 `type="button"` 避免提交）。




**HTML5 增强特性**

**输入类型扩展**

新增 `type` 类型，提升用户体验和验证能力：
- `type="email"`：强制邮箱格式。
- `type="url"`：强制 URL 格式。
- `type="tel"`：电话号码（移动端会弹出数字键盘）。
- `type="color"`：颜色选择器。

**验证属性**

- **`required`**：字段必填。
- **`pattern`**：正则表达式校验（如手机号格式）。
- **`min`/`max`**：数值或日期范围限制。
- **`minlength`/`maxlength`**：输入长度限制。



**示例：登录表单**

```html
<form action="/login" method="POST" id="login-form">
  <label>邮箱：<input type="email" name="email" required></label>
  <label>密码：<input type="password" name="password" minlength="8" required></label>
  <button type="submit">登录</button>
</form>

<script>
  document.getElementById("login-form").addEventListener("submit", async (e) => {
    e.preventDefault();
    const formData = new FormData(e.target);
    const response = await fetch("/login", {
      method: "POST",
      body: formData
    });
    if (response.ok) {
      window.location.href = "/dashboard";
    }
  });
</script>
```

### 


## 语义化

### 无语义的布局标签

作用：布局网页（划分网页区域，摆放内容）

* div：独占一行
* span：不换行

```html
<div>div 标签，独占一行</div>
<span>span 标签，不换行</span>
```

### 有语义的布局标签

| 标签名  | 语义       |
| ------- | ---------- |
| header  | 网页头部   |
| nav     | 网页导航   |
| footer  | 网页底部   |
| aside   | 网页侧边栏 |
| section | 网页区块   |
| article | 网页文章   |



## 字符实体

| 显示结果 | 描述   | 实体名称 |
| -------- | ------ | -------- |
|          | 空格   | `&nbsp;` |
| <        | 小于号 | `&lt`    |
| >        | 大于号 | `&gt`    |









## HTML事件属性

HTML元素有事件属性，例如

onclick\onchange\onmouseover

等属性；

同时由于 **HTML内联事件处理**  所以HTML元素的事件属性可以直接接受JS代码，当事件触发时，浏览器会将其作为JS代码执行

代码示例

```html
<button onclick="document.getElementById('myImage').src='/i/eg_bulbon.gif'">开灯</button>
```





## HTML style属性

HTML元素具有stlye属性，且在style属性中可以直接书写css代码来控制样式

- 但像<meta> <title> 这样的非可见元素 不支持 style

代码示例

```html
<div style="background-color: yellow;">黄色背景</div>
<h1 style="text-align: center;">居中的标题</h1>
```

HTML元素的style属性的优先级>HTML内部<style>标签设置的style属性>HTML外部.css文件中设置的style属性


