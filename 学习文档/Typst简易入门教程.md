# Typst 极速入门指南

> **简介**：Typst 是一个现代化的排版系统，旨在替代 LaTeX。它编译速度飞快，语法像 Markdown 一样简洁，报错信息友好，且原生支持强大的脚本功能。

## 1. 环境准备

推荐使用 **VS Code** 进行开发，体验最佳。

1. **安装 CLI**：
   - Windows: `winget install typst`
   - macOS: `brew install typst`
   - Linux: (查看官方文档)
2. **编辑器插件**：
   - 在 VS Code 中安装 **Tinymist** 插件。
   - *功能*：语法高亮、自动补全、**实时预览** (点击右上角 Preview 按钮)。

## 2. Hello World & 编译流程

新建一个 `main.typ` 文件：

```
= 我的第一份文档

Hello, Typst! 这里是正文内容。
```

- **编译命令**：`typst compile main.typ`
- **实时监听**：`typst watch main.typ` (推荐，保存即更新)

## 3. 基础排版与中文配置 🇨🇳

Typst 默认字体可能无法很好地显示中文，因此**全局配置**是第一步。

### 核心配置代码

在文件最开头加入：

```
// 1. 页面设置为 A4
#set page(paper: "a4")

// 2. 字体设置：先找英文字体，再找中文字体
#set text(font: ("Times New Roman", "SimSun"), lang: "zh")

// 3. 段落首行缩进 (2字符)
#set par(first-line-indent: 2em)
```

### 文本样式

- **标题**：`= 一级`, `== 二级`, `=== 三级`
- **加粗**：`*内容*`
- **斜体**：`_内容_`
- **列表**：`- 无序`, `+ 有序`

## 4. 理工科神器：公式与代码

### 数学公式 (Math)

不用反斜杠 `\`，所见即所得。

- **行内公式**：`$` 紧贴内容 `$` (如 `$E=mc^2$`)
- **独行公式**：`$` 加空格或换行 `$`

| **语法**           | **效果**              | **说明**       |
| ------------------ | :-------------------- | -------------- |
| `1/2`              | $\frac{1}{2}$         | 分数直接写     |
| `x^2_i`            | $x_i^2$               | 上下标         |
| `alpha`            | $\alpha$              | 希腊字母直接拼 |
| `sum`, `integrate` | $\sum, \int$          | 求和与积分     |
| `arrow`, `oo`      | $\rightarrow, \infty$ | 箭头与无穷     |

**示例**：

```
$f(x) = 1/sqrt(2 pi) e^(-x^2/2)$
```

### 代码块 (Code)

支持语法高亮，类似 Markdown。

````
```python
def hello():
    print("Hello Typst")
```
````

**进阶**：显示行号与背景

```
#show raw.where(block: true): block.with(
  fill: luma(240),
  inset: 10pt,
  radius: 4pt,
)
```

## 5. 可视化：图片与表格

### 插入图片

Typst 注重可复现性，**不支持直接引用网络 URL**，需下载到本地。

```
#figure(
  image("assets/chart.png", width: 80%),
  caption: [实验结果分析图]
) <fig1>
```

> **Tip**: `<fig1>` 是标签，正文中可以用 `@fig1` 引用，会自动生成 "图 1"。

### 绘制表格 (三线表风格)

```
#table(
  columns: (1fr, 1fr), // 两列等宽
  stroke: none,        // 去掉所有线
  table.hline(),       // 顶线
  [姓名], [成绩],
  table.hline(stroke: .5pt), // 表头细线
  [张三], [90],
  table.hline(),       // 底线
)
```

## 6. 页面布局 (Layout) 

### 页眉页脚

```
#set page(
  header: [左边标题 #h(1fr) 右边日期],
  footer: context align(center, counter(page).display("1"))
)
```

### 多栏排版 (IEEE 风格)

```
#show: rest => columns(2, rest)
```

### 强制换页

```
#pagebreak()
```

## 7. 进阶：模板化思想 (封装) 

软件工程的核心是**复用**。不要在每个文件里写配置，要把样式封装成函数。

### 文件结构

```
📂 project/
├── 📄 lib.typ  (模板文件/库)
└── 📄 main.typ (正文文件)
```

### 第一步：定义模板 (`lib.typ`)

```
#let project(title: "", body) = {
  set page(paper: "a4")
  set text(font: "SimSun", lang: "zh")
  
  // 封面逻辑
  align(center, text(20pt, title))
  pagebreak()
  
  // 渲染正文
  body
}
```

### 第二步：使用模板 (`main.typ`)

```
#import "lib.typ": project

#show: project.with(title: "我的实验报告")

= 正文开始
直接写内容，不用管样式，样式全在 lib.typ 里控制。
```

## 8. 常用资源 🔗

- **官方文档**: [typst.app/docs](https://typst.app/docs) (查函数必去)
- **官方 Web App**: [typst.app](https://typst.app/) (在线编辑，免安装)
- **第三方包**: [typst.app/universe](https://typst.app/universe) (类似 npm，有很多现成的论文模板)

*最后更新时间: 2025-11-19*