# CSS学习

>层叠样式表 (Cascading Style Sheets，缩写为 CSS），是一种 **样式表** 语言，用来**描述 HTML 文档的呈现**（**美化内容**）。
>
>书写位置：**title 标签下方添加 style 双标签，style 标签里面书写 CSS 代码**。
>
>```css
><title>CSS 初体验</title>
><style>
>  /* 选择器 { } */
>  p {
>    /* CSS 属性 */
>    color: red;
>  }
></style>
>
><p>体验 CSS</p>
>```
>
>**提示**：属性名和属性值成对出现 → 键值对。 

## CSS基础

### CSS引入方式

* **内部**样式表：学习使用
  * CSS 代码写在 style 标签里面

```html
<style>
....
</style>
```

* **外部**样式表：开发使用
  * CSS 代码写在单独的 CSS 文件中（**.css**）
  * 在 HTML 使用 link 标签引入

```html
<link rel="stylesheet" href="./my.css">
```

* **行内**样式：配合 JavaScript 使用
  * CSS 写在标签的 style 属性值里

```html
<div style="color: red; font-size:20px;">这是 div 标签</div>
```



### 选择器

> 选择器用来查找标签，设置样式

#### 标签选择器

```html
<style>
  p {
    color: red;
  }
</style>
```

- 标签选择器：使用**标签名**作为选择器 → 选中**同名标签设置相同的样式**,例如：p, h1, div, a, img......

- 标签选择器无法差异化同名标签的显示效果

#### 类选择器

```html
<style>
  /* 定义类选择器 */
  .red {
    color: red;
  }
</style>

<!-- 使用类选择器 -->
<div class="red">这是 div 标签</div>
<div class="red size">div 标签</div>
```

- **作用**：差异化 设置标签的显示效果
- 类名**自定义**，不要用纯数字或中文，尽量用英文命名
- 一个类选择器**可以供多个标签使用**
- **一个标签可以使用多个类名**，类名之间用**空格**隔开
- **开发习惯**：类名见名知意，多个单词可以用 - 连接，例如：news-hd。

#### id选择器

```html
<style>
  /* 定义 id 选择器 */
  #red {
    color: red;
  }
</style>

<!-- 使用 id 选择器 -->
<div id="red">这是 div 标签</div>
```

- **作用**：查找标签，差异化设置标签的显示效果。
- **场景**：id 选择器一般**配合 JavaScript** 使用，很少用来设置 CSS 样式

- **规则**：同一个 id 选择器在一个页面只能使用一次。

#### 通配符选择器

```html
* {
  color: red;
}
```

- 作用：查找页面**所有**标签，设置相同样式。

- 通配符选择器： ***，不需要调用**，浏览器自动查找页面所有标签，设置相同的样式

- 经验：通配符选择器可以用于**清除标签的默认样式**，例如：标签默认的外边距、内边距



### 文字控制属性

| 关键词            | 含义         |
| ----------------- | ------------ |
| `font-size`       | 字体大小     |
| `font-weight`     | 字体粗细     |
| `line-height`     | 行高         |
| `text-indent`     | 文本缩进     |
| `text-align`      | 文本对齐方式 |
| `text-decoration` | 文本修饰线   |
| `color`           | 文字颜色     |

#### 字体大小

* 属性名：**font-size**
* 属性值：文字尺寸，PC 端网页最常用的单位 **px**

```css
p {
  font-size: 30px;
}
```

> 经验：谷歌浏览器默认字号是16px。

#### 字体样式

作用：清除文字默认的倾斜效果

属性名：**font-style**

属性值

* 正常（不倾斜）：**normal** 
* 倾斜：**italic**

#### 行高

作用：设置多行文本的间距

属性名：line-height

属性值

* 数字 + px
* 数字（当前标签font-size属性值的倍数）

```css
line-height: 30px;


/* 当前标签字体大小为16px */
line-height: 2;
```

> 行高的测量方法：从一行文字的最顶端（最底端）量到下一行文字的最顶端（最底端）。 

##### 单行文字垂直居中

垂直居中技巧：**行高属性值等于盒子高度属性值**

注意：该技巧适用于单行文字垂直居中效果

```css
div {
  height: 100px;
  background-color: skyblue;

  /* 注意：只能是单行文字垂直居中 */
  line-height: 100px;
}
```

#### 字体族

属性名：**font-family**

属性值：字体名

```css
font-family: 楷体;
```

> 拓展（了解）：font-family属性值可以书写多个字体名，各个字体名用逗号隔开，执行顺序是从左向右依次查找
>
> *  font-family 属性最后设置一个字体族名，网页开发建议使用无衬线字体



```css
font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif;
```

#### font复合属性

使用场景：设置网页文字公共样式 

复合属性：属性的简写方式，**一个属性对应多个值的写法**，各个属性值之间用**空格**隔开。

**font: 是否倾斜  是否加粗  字号/行高 字体（必须按顺序书写）**

```css
div {
  font: italic 700 30px/2 楷体;
}
```

> [!NOTE]
>
> 注意：字号和字体值必须书写，否则 font 属性不生效 。

#### 文本缩进

属性名：**text-indent**

属性值：

* 数字 + px
* **数字 + em**（推荐：**1em = 当前标签的字号大小**）

```css
p {
  text-indent: 2em;
}
```

#### 文本对齐方式

作用：控制内容水平对齐方式

属性名：**text-align**

```css
text-align: center;
```

> text-align本质是控制内容的对齐方式，属性要设置给内容的父级。 

```html
<style>
  div {
    text-align: center;
  }
</style>

<div>
  <img src="./images/1.jpg" alt="">
</div>
```

#### 文本修饰线

属性名： **text-decoration**

| 属性值       | 效果   |
| ------------ | ------ |
| none         | 无     |
| underline    | 下划线 |
| line-through | 删除线 |
| overline     | 上划线 |

#### color文字颜色

| 颜色表示方式   | 属性值        | 说明                                 | 使用场景 |
| -------------- | ------------- | ------------------------------------ | -------- |
| 颜色关键字     | 颜色英文单词  | red、green、blue、...                | 学习测试 |
| rgb表示法      | rgb(r,g,b)    | r,g,b表示红绿蓝三种颜色，取值：0-255 |          |
| rgba表示法     | rgba(r,g,b,a) | a表示透明度，取值：0~1               | 开发使用 |
| 十六进制表示法 | #RRGGBB       | #000000,#ffcc00,简写：#000,#fc0      | 开发使用 |

>提示：只要属性值为颜色，都可以使用上述四种颜色表示方式，例如：背景色。 



### 调试工具

> 使用浏览器调试工具

作用：检查、调试代码；帮助程序员发现代码问题、解决问题

1. 打开调试工具

* 浏览器窗口内任意位置 / 选中标签 → 鼠标右键 → 检查
* F12

2. 使用调试工具



### 复合选择器

#### 后代选择器

后代选择器：**选中某元素的所有后代元素**。

选择器写法：父选择器 子选择器 { CSS 属性}，父子选择器之间用**空格**隔开。

```html
<style>
  div span {
    color: red;
  }
</style>
<span> span 标签</span>
<div>
  <span>这是 div 的儿子 span</span >
</div>
```

#### 子代选择器

子代选择器：选中某元素的子代元素（**最近的子级**）。

选择器写法：父选择器 > 子选择器 { CSS 属性}，父子选择器之间用 **>** 隔开。

```html
<style>
  div > span {
    color: red;
  }
</style>

<div>
  <span>这是 div 里面的 span</span>
  <p>
    <span>这是 div 里面的 p 里面的 span</span>
  </p>
</div>
```

#### 并集选择器

并集选择器：选中**多组标签**设置**相同**的样式。

选择器写法：选择器1, 选择器2, …, 选择器N { CSS 属性}，选择器之间用 **,** 隔开。

```html
<style>
  div,
  p,
  span {
    color: red;
  }
</style>

<div> div 标签</div>
<p>p 标签</p>
<span>span 标签</span>
```

#### 交集选择器

交集选择器：选中**同时满足多个条件**的元素。

选择器写法：选择器1选择器2 { CSS 属性}，选择器之间连写，没有任何符号。

```html
<style>
  p.box {
  color: red;
}
</style>

<p class="box">p 标签，使用了类选择器 box</p>
<p>p 标签</p>
<div class="box">div 标签，使用了类选择器 box</div>
```

> [!NOTE]
>
> 注意：如果交集选择器中有标签选择器，标签选择器必须书写在最前面。

#### 伪类选择器

伪类选择器：伪类表示元素**状态**，选中元素的某个状态设置样式。

鼠标悬停状态：**选择器:hover { CSS 属性 }**

```html
<style>
  a:hover {
    color: red;
  }
  .box:hover {
    color: green;
  }
</style>

<a href="#">a 标签</a>
<div class="box">div 标签</div>
```

#### 超链接伪类

| 选择器   | 作用           |
| -------- | -------------- |
| :link    | 访问前         |
| :visited | 访问后         |
| :hover   | 鼠标悬停       |
| :active  | 点击时（激活） |

> [!NOTE]
>
> 提示：如果要给超链接设置以上四个状态，需要按 LVHA 的顺序书写。
>
> 经验：工作中，一个 a 标签选择器设置超链接的样式， hover状态特殊设置

```css
a {
  color: red;
}

a:hover {
  color: green;
}
```

#### 结构伪类选择器 

作用：根据元素的**结构关系**查找元素。 

| 选择器              | 说明                 |
| ------------------- | -------------------- |
| E:first-child       | 查找第一个E元素      |
| E:last-child        | 查找最后一个E元素    |
| E:nth-child(N)      | 查找第N个E元素       |
| E:nth-child(`公式`) | 按照公式逻辑查找元素 |

```css
li:first-child {
  background-color: green;
}
```

**:nth-child(公式)** 

| 功能                | 公式      |
| ------------------- | --------- |
| 偶数标签            | 2n        |
| 奇数标签            | 2n+1;2n-1 |
| 找到5的倍数的标签   | 5n        |
| 找到第5个以后的标签 | n+5       |
| 找到第5个以前的标签 | -n+5      |

> 提示：公式中的n取值从 **0** 开始。 

#### 伪元素选择器 

作用：创建**虚拟元素**（伪元素），用来**摆放装饰性的内容**。 

![1680321533901](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680321533901.png)

| 选择器    | 说明                            |
| --------- | ------------------------------- |
| E::before | 在E元素里面最前面添加一个伪元素 |
| E::after  | 在E元素里面最后面添加一个伪元素 |

```css
div::before {
  content: "before 伪元素";
}
div::after {
  content: "after 伪元素";
}
```

注意点：

* 必须设置 **content: “”属性**，用来 设置伪元素的内容，如果没有内容，则**引号留空**即可
* 伪元素默认是**行内**显示模式
* **权重和标签选择器相同**





> [!CAUTION]
>
> I:
>
> ```css
> .bottom .item .active {
> 
> }
> ```
>
> II:
>
> ```css
> .bottom .item.active{
> 
> }
> ```
>
> 上面两种选择器的意义不同：
>
> I:类bottom里面有一个类为item的元素里面有一个类为active的类
>
> II:类bottom里面有一个类为item active的类







### CSS特性

> CSS特性：化简代码 / 定位问题，并解决问题
>
> - 继承性
> - 层叠性
> - 优先级

#### 继承性

继承性：子级默认继承父级的**文字控制属性**。

| 描述         | 属性            |
| ------------ | --------------- |
| 字体大小     | font-size       |
| 字体粗细     | font-weight     |
| 字体倾斜     | font-style      |
| 行高         | line-height     |
| 字体族       | font-family     |
| 字体复合属性 | font            |
| 文本缩进     | text-indent     |
| 文本对齐     | text-align      |
| 修饰线       | text-decoration |
| 颜色         | color           |

> [!NOTE]
>
> 注意：如果标签有默认文字样式会继承失败。 例如：a 标签的颜色、标题的字体大小。

#### 层叠性

特点：

- 相同的属性会覆盖：**后面的 CSS 属性覆盖前面的 CSS 属性**
- 不同的属性会叠加：**不同的 CSS 属性都生效**

```html
<style>
  div {
    color: red;
    font-weight: 700;
  }
  div {
    color: green;
    font-size: 30px;
  }
</style>

<div>div 标签</div>
```

> 注意：选择器类型相同则遵循层叠性，否则按选择器优先级判断。

#### 优先级

优先级：也叫权重，当一个标签**使用了多种选择器时**，基于不同种类的选择器的**匹配规则**。

```html
<style>
  div {
    color: red;
  }
  .box {
    color: green;
  }
</style>

<div class="box">div 标签</div>
```

##### 基础选择器

规则：选择器**优先级高的样式生效**。

公式：**通配符选择器 < 标签选择器 < 类选择器 < id选择器 < 行内样式 < !important**

 **（选中标签的范围越大，优先级越低）**

##### 复合选择器-叠加

叠加计算：如果是复合选择器，则需要**权重叠加**计算。

公式：（每一级之间不存在进位）

<span style="font-weight:bold; color:#CC0000;">（行内样式，id选择器个数，类选择器个数，标签选择器个数）</span>

规则：

- 从左向右依次比较选个数，同一级个数多的优先级高，如果个数相同，则向后比较
- **!important 权重最高**
- 继承权重最低



### Emmet 写法

Emmet写法：代码的**简写**方式，输入缩写 VS Code 会自动生成对应的代码。

- HTML标签

| 说明         | 标签结构                                     | Emmet         |
| ------------ | -------------------------------------------- | ------------- |
| 类选择器     | `<div class="box"></div>`                    | `标签名.类名` |
| id选择器     | `<div id="box"></div>`                       | `标签名#id名` |
| 同级标签     | `<div></div><p></p>`                         | `div+p`       |
| 父子级标签   | `<div><p></p></div>`                         | `div>p`       |
| 多个相同标签 | `<span>1</span><span>2</span><span>3</span>` | `span*3`      |
| 有内容的标签 | `<div>内容</div>`                            | `div{内容}`   |

- CSS：大多数简写方式为属性单词的**首字母**

| 说明      | CSS属性                                          | Emmet           |
| --------- | ------------------------------------------------ | --------------- |
| 宽度      | `width`                                          | `w`             |
| 宽度500px | `width:500px`                                    | `w500`          |
| 背景色    | `background-color`                               | `bgc`           |
| 多个属性  | `width:200px;height:100px;background-color:#fff` | `w200+h100+bgc` |



### 背景属性

#### 背景图

网页中，使用背景图实现装饰性的图片效果。

- 属性名：**background-image**（bgi）
- 属性值：url(背景图 URL)

```css
div {
  width: 400px;
  height: 400px;

  background-image: url(./images/1.png);
}
```

> 提示：背景图默认有**平铺（复制）效果**。

#### 平铺方式

属性名：**background-repeat**（bgr）

| 属性值    | 效果             |
| --------- | ---------------- |
| no-repeat | 不平铺           |
| repeat    | 平铺**（默认）** |
| repeat-x  | 水平方向平铺     |
| repeat-y  | 垂直方向平铺     |

```css
div {
  width: 400px;
  height: 400px;
  background-color: pink;
  background-image: url(./images/1.png);

  background-repeat: no-repeat;
}
```

#### 背景图位置

属性名：**background-position**（bgp）

属性值：水平方向位置 垂直方向位置

- 关键字

| 关键字 | 位置 |
| ------ | ---- |
| left   | 左侧 |
| right  | 右侧 |
| center | 居中 |
| top    | 顶部 |
| bottom | 底部 |

- 坐标
  - 水平：正数向右；负数向左
  - 垂直：正数向下；负数向上

```css
div {
  width: 400px;
  height: 400px;
  background-color: pink;
  background-image: url(./images/1.png);
  background-repeat: no-repeat;

  background-position: center bottom;
  background-position: 50px -100px;
  background-position: 50px center;
}
```

> [!NOTE]
>
> 提示：
>
> - 关键字取值方式写法，可以颠倒取值顺序
> - 可以只写一个关键字，另一个方向默认为居中；数字只写一个值表示水平方向，垂直方向为居中

#### 背景图缩放

作用：设置背景图大小

属性名：**background-size**（bgz）

常用属性值：

- 关键字
  - cover：等比例缩放背景图片以完全覆盖背景区，可能背景图片部分看不见
  - contain：等比例缩放背景图片以完全装入背景区，可能背景区部分空白
- 百分比：根据盒子尺寸计算图片大小
- 数字 + 单位（例如：px）

```css
div {
  width: 500px;
  height: 400px;
  background-color: pink;
  background-image: url(./images/1.png);
  background-repeat: no-repeat;
  
  background-size: cover;
  background-size: contain;
}
```

> [!NOTE]
>
> 提示：工作中，**图片比例与盒子比例相同**，使用 cover 或 contain 缩放背景图效果相同。

#### 背景图固定

作用：背景不会随着元素的内容滚动。

属性名：**background-attachment**（bga）

属性值：**fixed**

```css
body {
  background-image: url(./images/bg.jpg);
  background-repeat: no-repeat;
  background-attachment: fixed;
}
```

#### 背景复合属性

属性名：**background**（bg）

属性值：背景色 背景图 背景图平铺方式 背景图位置/背景图缩放 背景图固定（**空格隔开各个属性值，不区分顺序**）

```css
div {
  width: 400px;
  height: 400px;

  background: pink url(./images/1.png) no-repeat right center/cover;
}
```



### 显示模式

每个HTML 标签都具有 display 属性，通过修改 display 属性的值，可以修改标签的显示模式

| 属性值       | 效果               |
| ------------ | ------------------ |
| block        | 设置为 块级 元素   |
| inline-block | 设置为 行内块 元素 |
| inline       | 设置为 行内 元素   |
| none         | 隐藏元素，不占空间 |
| flex         | 设置为 弹性布局    |
| grid         | 设置为 网格布局    |
|              |                    |

#### 块级元素

特点：

- 独占一行
- 宽度默认是父级的100%
- 添加宽高属性生效

常见块级元素：

- div
- h1-h6
- table
- dd、dl、dt
- ol
- form
- ul、li
- p
- hr

```html
<article>, <aside>, <blockquote>, <canvas>, <fieldset>, <figcaption>, <figure>, <footer>, <header>, <main>, <nav>, <noscript>,  <pre>, <section>, <address>
```



#### 行内元素

特点：

- 不换行，一行可以显示多个
- 设置宽高属性不生效，宽高尺寸由内容撑开
- 只能包含文本和其他行内元素

常见行内元素：

- span

- a
- br
- i
- strong
- label
- script

```html
<abbr>, <b>, <bdi>, <bdo>, <cite>, <code>, <data>, <datalist>, 
<em>, <kbd>, <mark>, <q>, <s>, <samp>, <select>, <small>, <sub>, <sup>, <time>, <u>, <var>
```



#### 行内块元素

特点：

- 不会换行，一行可以显示多个
- 设置宽高属性生效，宽高尺寸由内容撑开

常见行内块元素：

- img
- input
- button
- textarea
- select
- video









## 盒子模型

> 作用：布局网页，摆放盒子和内容。

### 盒子模型的组成

* 内容区域 – width & height
* 内边距 – padding（出现在内容与盒子边缘之间）
* 边框线 – border 
* 外边距 – margin（出现在盒子外面）

```css
div {
  margin: 50px;
  border: 5px solid brown;
  padding: 20px;
  width: 200px;
  height: 200px;
  background-color: pink;
}
```

![1680330928735](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680330928735.png)

![1680330935635](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680330935635.png)





### 边框线

#### 四个方向边框线

属性名：**border**（bd）

属性值：边框线粗细  线条样式  颜色（不区分顺序）

| 属性值 | 线条样式 |
| ------ | -------- |
| solid  | 实线     |
| dashed | 虚线     |
| dotted | 点线     |

```css
div {
  border: 5px solid brown;
  width: 200px;
  height: 200px;
  background-color: pink;
}
```

#### 单方向边框线 

属性名：**border-方位名词**（bd+方位名词首字母，例如，bdl）

属性值：边框线粗细  线条样式  颜色（不区分顺序）

```css
div {
  border-top: 2px solid red;
  border-right: 3px dashed green;
  border-bottom: 4px dotted blue;
  border-left: 5px solid orange;
  width: 200px;
  height: 200px;
  background-color: pink;
}
```



### 内边距 

作用：设置 内容 与 盒子边缘 之间的距离。

* 属性名：padding / padding-方位名词

```css
div {
  /* 四个方向 内边距相同 */
  padding: 30px;
  /* 单独设置一个方向内边距 */
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 40px;
  padding-left: 80px;
  width: 200px;
  height: 200px;
  background-color: pink;
}
```

> 提示：添加 padding 会撑大盒子。

* padding 多值写法

| 取值个数 | 示例                           | 含义                                   |
| -------- | ------------------------------ | -------------------------------------- |
| 一个值   | `padding: 10px`                | 四个方向内边距均为10px                 |
| 四个值   | `padding: 10px 20px 40px 80px` | 上：10px；右：20px；下：40px；左：80px |
| 三个值   | `padding: 10px 40px 80px`      | 上：10px；左右：40px；下：80px         |
| 两个值   | `padding: 10px 80px`           | 上下：10px；左右：80px；               |

> 技巧：从**上**开始**顺时针**赋值，当前方向没有数值则与**对面取值相同**。 

#### 尺寸计算

![1680331322935](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680331322935.png)

默认情况：盒子尺寸 = 内容尺寸 + border 尺寸 + 内边距尺寸

结论：给盒子加 border / padding 会撑大盒子

解决：

* 手动做减法，减掉 border / padding 的尺寸
* 內减模式：**box-sizing: border-box**



### 外边距 

作用：拉开两个盒子之间的距离

属性名：**margin**

提示：与 padding 属性值写法、含义相同

#### 外边距问题——合并现象

场景：**垂直**排列的兄弟元素，上下 **margin** 会**合并**

现象：取两个 margin 中的**较大值生效**

![1680331672628](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680331672628.png)

```css
.one {
  margin-bottom: 50px;
}
.two {
  margin-top: 20px;
}
```

#### 外边距问题——外边距塌陷

场景：父子级的标签，子级的添加 **上外边距** 会产生**塌陷**问题

现象：**导致父级一起向下移动**

```css
.son {
  margin-top: 50px;
  width: 100px;
  height: 100px;
  background-color: orange;
}
```

![1680333860271](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680333860271.png)

解决方法：

* 取消子级margin，父级设置padding
* 父级设置 overflow: hidden
* 父级设置 border-top

#### 行内元素 – 内外边距问题 

场景：行内元素添加 margin 和 padding，无法改变元素垂直位置

解决方法：给行内元素添加 **line-height** 可以改变垂直位置

```css
span {
  /* margin 和 padding 属性，无法改变垂直位置 */
  margin: 50px;
  padding: 20px;
  /* 行高可以改变垂直位置 */
  line-height: 100px;
}
```



### 版心居中

![1680331503466](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680331503466.png)

左右 margin 值 为 auto（盒子要有宽度）

```css
div {
  margin: 0 auto;
  width: 1000px;
  height: 200px;
  background-color: pink;
}
```



### 清除默认样式 

![1680331558304](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680331558304.png)

清除标签默认的样式，比如：默认的内外边距。 

![1680331580746](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680331580746.png)

```css
/* 清除默认内外边距 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
/* 清除列表项目符号 */
li {
  list-style: none;
}
```



### 元素溢出

作用：控制溢出元素的内容的显示方式。

属性名：**overflow**

| 属性值 | 效果                                       |
| ------ | ------------------------------------------ |
| hidden | 溢出隐藏                                   |
| scroll | 溢出滚动（无论是否溢出，都显示滚动条位置） |
| auto   | 溢出滚动（溢出才显示滚动条位置）           |



### 圆角

作用：设置元素的外边框为圆角。

属性名：**border-radius**

属性值：数字+px / 百分比

提示：属性值是圆角半径

![1680334014390](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680334014390.png)



* 多值写法

| 取值个数 | 示例                                 | 含义                                           |
| -------- | ------------------------------------ | ---------------------------------------------- |
| 一个值   | `border-radius: 10px`                | 四个角均为10px                                 |
| 四个值   | `border-radius: 10px 20px 40px 80px` | 左上：10px；右上：20px；右下：40px；左下：80px |
| 三个值   | `border-radius: 10px 40px 80px`      | 左上：10px；右上+左下：40px；右下：80px        |
| 两个值   | `border-radius: 10px 80px`           | 左上+右下：10px；右上+左下：80px；             |

> 技巧：从左上角开始顺时针赋值，当前角没有数值则与对角取值相同。 

* 正圆形状：给正方形盒子设置圆角属性值为 **宽高的一半 / 50%**

```css
img {
  width: 200px;
  height: 200px;
  
  border-radius: 100px;
  border-radius: 50%;
}
```

![1680334083567](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680334083567.png)

* 胶囊形状：给长方形盒子设置圆角属性值为 盒子高度的一半 

```css
div {
  width: 200px;
  height: 80px;
  background-color: orange;
  border-radius: 40px;
}
```

![1680334136242](D:/Desktop/前端学习/资料/Day01-10基础班课程资料/基础班课程资料/笔记/day05/assets/1680334136242.png)



### 盒子阴影

作用：给元素设置阴影效果

属性名：**box-shadow**

属性值：X 轴偏移量  Y 轴偏移量  模糊半径  扩散半径  颜色  内外阴影

注意： 

* X 轴偏移量 和 Y 轴偏移量 必须书写
* 默认是外阴影，内阴影需要添加 inset

```css
div {
  width: 200px;
  height: 80px;
  background-color: orange;
  box-shadow: 2px 5px 10px 0 rgba(0, 0, 0, 0.5) inset;
}
```





# Flex布局

> 目标：熟练使用 Flex 完成结构化布局

### 标准流

标准流也叫文档流，指的是标签在页面中**默认的排布规则**，例如：块元素独占一行，行内元素可以一行显示多个。 

![1680334840709](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day06\assets\1680334840709.png)

### 浮动

#### 基本使用

作用：让块元素水平排列。

属性名：**float**

属性值

* **left**：左对齐
* **right**：右对齐

```html
<style>
  /* 特点：顶对齐；具备行内块显示模式特点；浮动的盒子会脱标 */
  .one {
    width: 100px;
    height: 100px;
    background-color: brown;

    float: left;
  }

  .two {
    width: 200px;
    height: 200px;
    background-color: orange;

    /* float: left; */

    float: right;
  }
</style>

<div class="one">one</div>
<div class="two">two</div>
```

特点：

* 浮动后的盒子**顶对齐**
* 浮动后的盒子具备**行内块**特点
* 浮动后的盒子**脱标**，**不占用标准流的位置**

#### 产品区域布局

![1680335016853](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day06\assets\1680335016853.png)

**代码示例：**

- HTML标签

```html
<!-- 版心：左右，右面：8个产品 → 8个 li -->
<div class="product">
  <div class="left"></div>
  <div class="right">
    <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>
</div>
```

- CSS样式

```html
<style>
  * {
    margin: 0;
    padding: 0;
  }

  li {
    list-style: none;
  }

  .product {
    margin: 50px auto;
    width: 1226px;
    height: 628px;
    background-color: pink;
  }

  .left {
    float: left;
    width: 234px;
    height: 628px;
    background-color: skyblue;
  }

  .right {
    float: right;
    width: 978px;
    height: 628px;
    background-color: brown;
  }

  .right li {
    float: left;
    margin-right: 14px;
    margin-bottom: 14px;
    width: 234px;
    height: 300px;
    background-color: orange;
  }

  /* 第四个li和第八个li 去掉右侧的margin */
  .right li:nth-child(4n) {
    margin-right: 0;
  }

  /* 细节：如果父级宽度不够，浮动的盒子会掉下来 */
</style>
```

#### 清除浮动

场景：浮动元素会脱标，如果**父级没有高度**，**子级无法撑开父级高度**（可能导致页面布局错乱）

解决方法：**清除浮动**（清除浮动带来的影响）

场景搭建:

![1680335081694](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day06\assets\1680335081694.png)

```html
<style>
  .top {
    margin: 10px auto;
    width: 1200px;
    /* height: 300px; */
    background-color: pink;
  }

  .left {
    float: left;
    width: 200px;
    height: 300px;
    background-color: skyblue;
  }

  .right {
    float: right;
    width: 950px;
    height: 300px;
    background-color: orange;
  }

  .bottom {
    height: 100px;
    background-color: brown;
  }

</style>

<div class="top">
  <div class="left"></div>
  <div class="right"></div>
</div>
<div class="bottom"></div>
```

##### 额外标签法

在**父元素内容的最后**添加一个**块级**元素，设置 CSS 属性 **clear: both** 

```html
<style>
.clearfix {
  clear: both;
}
</style>

<div class="father">
  <div class="left"></div>
  <div class="right"></div>
  <div class="clearfix"></div>
</div>
```

##### 单伪元素法

1. 准备 after 伪元素

```css
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

2. 父级使用 clearfix 类

```html
<div class="father clearfix"></div>
```

##### 双伪元素法

1. 准备 after 和 before 伪元素

```css
/* before 解决外边距塌陷问题 */
/* 双伪元素法 */
.clearfix::before,
.clearfix::after {
  content: "";
  display: table;
}

/* after 清除浮动 */
.clearfix::after {
  clear: both;
}
```

2. 父级使用 clearfix 类

```html
<div class="father clearfix"></div>
```

##### overfow法

```css
.father {
  margin: 10px auto;
  width: 1200px;
  /* height: 300px; */
  background-color: pink;

  overflow: hidden;
}
```





### Flex布局

Flex 布局也叫**弹性布局**，是浏览器**提倡的布局模型**，非常适合**结构化**布局，提供了强大的空间分布和对齐能力。

Flex 模型不会产生浮动布局中脱标现象，布局网页更简单、更灵活。

![1680335815005](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day06\assets\1680335815005.png)

#### Flex组成

设置方式：给**父**元素设置 **display: flex**，子元素可以自动挤压或拉伸

组成部分：

* 弹性容器
* 弹性盒子
* 主轴：默认在**水平**方向
* 侧轴 / 交叉轴：默认在**垂直**方向

![1680335870554](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day06\assets\1680335870554.png)

#### 主轴对齐方式

属性名：**justify-content**

| 属性值        | 效果                                               |
| ------------- | -------------------------------------------------- |
| flex-start    | 默认值，弹性盒子从起点开始依次排列                 |
| flex-end      | 弹性盒子从终点开始依次排列                         |
| center        | 弹性盒子沿主轴居中排列                             |
| space-between | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子之间 |
| space-around  | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子两侧 |
| space-evenly  | 弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等 |

#### 侧轴对齐方式

* align-items：当前弹性容器内**所有**弹性盒子的侧轴对齐方式（给**弹性容器**设置）
* align-self：单独控制**某个弹性盒子**的侧轴对齐方式（给**弹性盒子**设置）

| 属性值     | 效果                                                         |
| ---------- | ------------------------------------------------------------ |
| stretch    | 弹性盒子沿着侧轴线被拉伸至铺满容器（弹性盒子没有设置侧轴方向尺寸则默认拉伸） |
| center     | 弹性盒子沿侧轴居中排列                                       |
| flex-start | 弹性盒子从起点开始依次排列                                   |
| flex-end   | 弹性盒子从终点开始依次排列                                   |

#### 修改主轴方向

**主轴默认在水平方向，侧轴默认在垂直方向**

属性名：**flex-direction**

| 属性值         | 效果                       |
| -------------- | -------------------------- |
| row            | 水平方向，从左向右（默认） |
| column         | 垂直方向，从上向下         |
| row-reverse    | 水平方向，从右向左         |
| column-reverse | 垂直方向，从下向上         |

#### 弹性伸缩比

作用：控制弹性盒子的主轴方向的尺寸。

属性名：**flex**

属性值：整数数字，表示占用**父级剩余尺寸的份数**。

#### 弹性盒子换行

弹性盒子可以自动挤压或拉伸，默认情况下，所有弹性盒子都在一行显示。

属性名：**flex-wrap**

属性值

* wrap：换行
* nowrap：不换行（默认）

#### 行内对齐方式

属性名：**align-content** 

| 属性值        | 效果                                               |
| ------------- | -------------------------------------------------- |
| flex-start    | 默认值，弹性盒子从起点开始依次排列                 |
| flex-end      | 弹性盒子从终点开始依次排列                         |
| center        | 弹性盒子沿主轴居中排列                             |
| space-between | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子之间 |
| space-around  | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子两侧 |
| space-evenly  | 弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等 |

> 注意：该属性对**单行**弹性盒子模型**无效**。 







## CSS高级

### 定位

作用：灵活的改变盒子在网页中的位置

实现：

1.定位模式：position

2.边偏移：设置盒子的位置

* left
* right
* top
* bottom

#### 相对定位

**position: relative**

特点：

* 不脱标，占用自己原来位置
* 显示模式特点保持不变
* 设置边偏移则相对自己原来位置移动

```css
div {
  position: relative;
  top: 100px;
  left: 200px;
}	
```

#### 绝对定位

**position: absolute**

使用场景：子级绝对定位，父级相对定位（**子绝父相**）

特点：

* 脱标，不占位
* 显示模式具备行内块特点
* 设置边偏移则相对最近的已经定位的祖先元素改变位置
* 如果祖先元素都未定位，则相对浏览器可视区改变位置

```css
.father {
  position: relative;
}

.father span {
  position: absolute;
  top: 0;
  right: 0;
}
```

#### 定位居中

![1680340142857](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340142857.png)

实现步骤：

1. 绝对定位
2. 水平、垂直边偏移为 50%
3. 子级向左、上移动自身尺寸的一半

* 左、上的外边距为 –尺寸的一半
* transform: translate(-50%, -50%)

```css
img {
  position: absolute;
  left: 50%;
  top: 50%;

  /* margin-left: -265px;
  margin-top: -127px; */

  /* 方便： 50% 就是自己宽高的一半 */
  transform: translate(-50%, -50%);
}
```

#### 固定定位

**position: fixed**

场景：元素的位置在网页滚动时不会改变

特点：

* 脱标，不占位
* 显示模式具备行内块特点
* 设置边偏移相对浏览器窗口改变位置

```css
div {
  position: fixed;
  top: 0;
  right: 0;

  width: 500px;
}
```

#### 堆叠层级z-index

![1680340281795](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340281795.png)

默认效果：按照标签书写顺序，后来者居上

作用：设置定位元素的层级顺序，改变定位元素的显示顺序

属性名：**z-index**

属性值：**整数数字**（默认值为0，取值越大，层级越高）

```css
.box1 {
  background-color: pink;
  /* 取值是整数，默认是0，取值越大显示顺序越靠上 */
  z-index: 1;
}

.box2 {
  background-color: skyblue;
  left: 100px;
  top: 100px;

  z-index: 2;
}
```



### CSS精灵

CSS 精灵，也叫 **CSS Sprites**，是一种网页**图片应用处理方式**。把网页中**一些背景图片**整合到**一张图片**文件中，再**background-position** 精确的定位出背景图片的位置。

![1680340401800](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340401800.png)

优点：减少服务器被请求次数，减轻服务器的压力，提高页面加载速度

![1680340411600](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340411600.png)

实现步骤：

1. 创建盒子，**盒子尺寸**与**小图**尺寸**相同**
2. 设置盒子**背景图**为精灵图
3. 添加 **background-position** 属性，改变**背景图位置**

​       3.1 使用 PxCook 测量小图片**左上角坐标**

​       3.2 取**负数**坐标为 background-position 属性值（向左上移动图片位置）



#### 案例-京东服务

![1680340481861](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340481861.png)

**HTML结构**

```html
<div class="service">
  <ul>
    <li>
      <h5></h5>
      <p>品类齐全，轻松购物</p>
    </li>
    <li>
      <h5></h5>
      <p>多仓直发，极速配送</p>
    </li>
    <li>
      <h5></h5>
      <p>正品行货，精致服务</p>
    </li>
    <li>
      <h5></h5>
      <p>天天低价，畅选无忧</p>
    </li>
  </ul>
</div>
```

**CSS样式**

```html
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  li {
    list-style: none;
  }

  .service {
    margin: 100px auto;
    width: 1190px;
    height: 42px;
    /* background-color: pink; */
  }

  .service ul {
    display: flex;
  }

  .service li {
    display: flex;
    padding-left: 40px;
    width: 297px;
    height: 42px;
    /* background-color: skyblue; */
  }

  .service li h5 {
    margin-right: 10px;
    width: 36px;
    height: 42px;
    /* background-color: pink; */
    background: url(./images/sprite.png) 0 -192px;
  }

  .service li:nth-child(2) h5 {
    background-position: -41px -192px;
  }

  .service li:nth-child(3) h5 {
    background-position: -82px -192px;
  }

  .service li:nth-child(4) h5 {
    background-position: -123px -192px;
  }

  .service li p {
    font-size: 18px;
    color: #444;
    font-weight: 700;
    line-height: 42px;
  }
</style>
```

### 字体图标

![1680340562425](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340562425.png)

字体图标：**展示的是图标，本质是字体**

作用：在网页中添加**简单的、颜色单一**的小图标

优点

* **灵活性**：灵活地修改样式，例如：尺寸、颜色等
* **轻量级**：体积小、渲染快、降低服务器请求次数
* **兼容性**：几乎兼容所有主流浏览器
* **使用方便**：先下载再使用

#### 下载字体

[iconfont-阿里巴巴矢量图标库](https://www.iconfont.cn/collections/detail?spm=a313x.user_detail.i1.dc64b3430.110d3a81Q0Q2Bd&cid=44573)

iconfont 图标库：<https://www.iconfont.cn/> 

登录 → 素材库 → 官方图标库 → 进入图标库 → 选图标，加入购物车 → 购物车，添加至项目，确定 → 下载至本地 

![1680340665988](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340665988.png)

#### 使用字体

1. 引入字体样式表（iconfont.css） 

![1680340697011](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340697011.png)

2. 标签使用字体图标类名
   * iconfont：字体图标基本样式（字体名，字体大小等等）
   * icon-xxx：图标对应的类名

![1680340718890](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340718890.png)

#### 上传矢量图

作用：项目特有的图标上传到 iconfont 图标库，生成字体

![1680340775611](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340775611.png)

上传步骤：上传 → 上传图标 → 选择 svg 矢量图，打开 → 提交 → 系统审核



### CSS修饰属性

#### 垂直对齐方式 

![1680340838945](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340838945.png)

属性名：vertical-align

![1680340829633](D:\Desktop\前端学习\资料\Day01-10基础班课程资料\基础班课程资料\笔记\day08\assets\1680340829633.png)

#### 过渡

作用：可以为一个元素在不同状态之间切换的时候添加**过渡效果**

属性名：**transition（复合属性）**

属性值：**过渡的属性  花费时间 (s)**

提示：

* 过渡的属性可以是具体的 CSS 属性
* 也可以为 all（两个状态属性值不同的所有属性，都产生过渡效果）
* transition 设置给元素本身

```css
img {
  width: 200px;
  height: 200px;
  transition: all 1s;
}

img:hover {
  width: 500px;
  height: 500px;
}
```

#### 透明度opacity

作用：设置**整个元素的透明度**（包含背景和内容）

属性名：opacity

属性值：0 – 1

* 0：完全透明（元素不可见）
* 1：不透明
* 0-1之间小数：半透明

#### 光标类型cursor

作用：鼠标悬停在元素上时指针显示样式

属性名：cursor

| 属性值  | 效果                         |
| ------- | ---------------------------- |
| default | 默认值，通常是箭头           |
| pointer | 小手效果，提示用户可以点击   |
| text    | 工字形，提示用户可以选择文字 |
| move    | 十字光标，提示用户可以移动   |



## 项目实践经验

### CSS书写顺序

**先清除默认样式**

1. 盒子模型属性
2. 文字样式
3. 圆角、阴影等修饰属性

**从大到小**———使得网页加载速度优化



## CSS补充学习

设置块大小时

```css
.box {
	width:100vw;   /* 宽度为浏览器视口的100%大小 */
    height:100vh;  /* 高度为浏览器视口的100%大小 */
}
```

