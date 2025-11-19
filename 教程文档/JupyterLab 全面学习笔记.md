# JupyterLab 全面学习笔记

JupyterLab 是一个基于 Web 的、下一代的用户界面，用于 Project Jupyter。它在一个灵活且强大的用户界面中，将 Jupyter Notebook、文本编辑器、终端和自定义组件集成在一起。对于数据科学、科学计算和机器学习领域的从业者来说，JupyterLab 是一个不可或缺的工具。



#### 1. JupyterLab 的特点（与其他 IDE 的区别与优势）



传统的 IDE（如 PyCharm, VS Code）通常是为软件开发设计的，功能全面且强大，但在交互式数据探索和可视化方面，JupyterLab 提供了无与伦比的体验。

| 特性             | JupyterLab                                                   | 传统 IDE (e.g., VS Code, PyCharm)                            |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **核心理念**     | 交互式计算与探索                                             | 软件工程与项目开发                                           |
| **工作流程**     | **非线性、探索性**：以代码块（Cell）为单位执行，方便反复修改、立即查看结果，非常适合数据分析和算法调试。 | **线性、结构化**：通常需要运行整个脚本文件来查看结果，调试过程相对繁琐。 |
| **界面布局**     | **高度灵活、可定制**：模块化的界面，可以像搭积木一样自由拖拽、排列窗口（Notebook、终端、文件浏览器等）。 | **相对固定**：通常是固定的多面板布局（编辑器、文件树、终端、调试器）。 |
| **数据与可视化** | **原生支持**：直接在文档中内嵌代码、文本、数学公式、图表和富媒体输出，形成一个可分享的“计算叙事”文档。 | **分离式体验**：代码和图表通常在不同的窗口或面板中显示，不利于形成连贯的分析报告。 |
| **内核支持**     | **多语言内核**：原生支持 Python，并可通过内核支持 Julia, R, Scala 等超过40种编程语言。 | 通常专注于特定语言或需要通过插件扩展。                       |
| **扩展性**       | 强大的插件生态：拥有丰富的第三方扩展，可以增强功能，如 Git 集成、代码补全、可视化调试器等。 | 同样拥有强大的插件生态，但在数据科学领域的针对性插件可能不如 JupyterLab 丰富。 |

**JupyterLab 的核心优势总结：**

- **交互式与探索性**：这是 JupyterLab 最核心的优势。它允许你逐个单元格地执行代码，并立即看到结果，这对于数据清洗、特征工程、模型实验和可视化探索至关重要。你可以在一个文档中轻松地迭代和完善你的想法。
- **富文本叙事能力**：Jupyter Notebook（JupyterLab 的核心组件）能够将代码、运行结果、Markdown 文本、LaTeX 公式和交互式图表无缝地融合在一起。这使得创建可重复、易于分享和理解的分析报告变得异常简单。
- **灵活的工作区**：你可以根据自己的需要，同时打开和排列多个 Notebook、终端、文本文件甚至数据集预览窗口。这种灵活性使得在不同任务之间切换变得高效。
- **远程计算与云端原生**：JupyterLab 被广泛应用于远程服务器和云平台（如 Google Colab, Amazon SageMaker）。你可以在本地浏览器上操作，而计算任务则在远程强大的服务器上执行。

------



#### 2. 如何安装 JupyterLab



安装 JupyterLab 最常见和推荐的方式是通过 Conda (Anaconda/Miniconda) 或 Pip。

**方案一：使用 Anaconda (推荐给初学者和数据科学家)**

Anaconda 是一个集成了 Python 解释器、常用科学计算库和包管理工具 Conda 的发行版。它能帮你处理好复杂的依赖关系，是安装 JupyterLab 最省心的方式。

1. **安装 Anaconda**:

   - 访问 [Anaconda 官网](https://www.anaconda.com/products/distribution)。
   - 下载适合你操作系统的安装包 (Python 3.x 版本)。
   - 按照图形化界面的提示完成安装。

2. **通过 Anaconda Navigator 安装**:

   - 安装好 Anaconda 后，打开 "Anaconda Navigator"（一个图形化管理界面）。
   - 在主界面上，你应该能直接看到 JupyterLab，点击 "Launch" 即可启动。如果未安装，也可以在这里点击 "Install"。

3. **通过 Conda 命令行安装**:

   - 打开你的终端（在 Windows 上是 "Anaconda Prompt"）。

   - 执行以下命令：

     

     ```bash
     # (推荐) 创建一个名为 myenv 的新环境并安装 jupyterlab
     conda create -n myenv jupyterlab
     
     # 激活新环境
     conda activate myenv
     
     # 在该环境中启动 JupyterLab
     jupyter lab
     ```

   - 或者，直接在 `base` 环境中安装/更新：

     

     ```bash
     conda install -c conda-forge jupyterlab
     ```

     (`conda-forge` 是一个社区维护的渠道，通常有最新版本的包)。

**方案二：使用 Pip (适合熟悉 Python 环境管理的用户)**

1. **确保 Python 和 Pip 已安装**。

2. **创建并激活虚拟环境 (强烈推荐)**:

   

   ```bash
   # 创建虚拟环境
   python -m venv venv
   
   # 激活虚拟环境
   # Windows
   .\venv\Scripts\activate
   # macOS / Linux
   source venv/bin/activate
   ```

3. **使用 Pip 安装 JupyterLab**:

   

   ```bash
   pip install jupyterlab
   ```

4. **启动 JupyterLab**:

   

   ```bash
   jupyter lab
   ```

------



#### 3. 如何使用 JupyterLab



启动 JupyterLab 后，它会自动在你的默认浏览器中打开一个新标签页。界面主要分为三个部分：**左侧边栏**、**主工作区**和**顶部菜单栏**。

**A. 界面概览**

- **左侧边栏 (Side Bar)**:
  - **文件浏览器** (File Browser): 浏览、创建、删除和管理你的文件和文件夹。
  - **正在运行的内核和终端** (Running Terminals and Kernels): 查看和管理当前正在运行的 Notebook 会话和终端，可以从这里关闭它们以释放资源。
  - **命令面板** (Commands): 搜索并执行 JupyterLab 中的所有命令。
  - **属性检查器** (Property Inspector): 查看和编辑 Notebook 单元格的元数据。
  - **扩展管理器** (Extension Manager): 搜索、安装和管理 JupyterLab 扩展插件。
- **主工作区 (Main Work Area)**:
  - 你的主要工作区域，可以容纳多个标签页和面板。
  - 你可以将标签页拖拽到工作区的任意位置（上、下、左、右）来创建分屏视图，实现多窗口并行工作。

**B. 核心操作：Notebook**

- **创建新的 Notebook**:
  - 在文件浏览器的 `+` 按钮处，选择 "Python 3 (ipykernel)" 或其他你已安装的内核。一个新的 `.ipynb` 文件将被创建并打开。【`.ipynb` 文件是 **Jupyter Notebook 的专用文件格式**】
- **单元格 (Cell)**: Notebook 由单元格组成，主要有两种类型：
  - **代码单元格 (Code Cell)**: 用来编写和执行代码。
  - **Markdown 单元格 (Markdown Cell)**: 用来编写格式化的文本、标题、列表、插入图片和数学公式（使用 LaTeX 语法）。
  - *切换方法*：选中单元格后按 `M` 切换到 Markdown，按 `Y` 切换回代码。
- **执行单元格**:
  - `Shift + Enter`: **执行**当前单元格，并**选中下一个**单元格（最常用）。
  - `Ctrl + Enter`: **执行**当前单元格，但**停留在当前**单元格。
  - `Alt + Enter`: **执行**当前单元格，并在**下方插入一个新**单元格。
- **命令模式与编辑模式**:
  - **编辑模式 (Edit Mode)**: 单元格边框为**绿色**，此时你在单元格内输入的是代码或文本。按 `Enter` 键进入。
  - **命令模式 (Command Mode)**: 单元格边框为**蓝色**，此时你按下的键会被视为快捷命令（如复制、粘贴）。按 `Esc` 键进入。
- **常用快捷键 (命令模式下)**:
  - `A`: 在当前单元格**上**方(Above)插入一个新单元格。
  - `B`: 在当前单元格**下**方(Below)插入一个新单元格。
  - `D, D` (按两次D): **删除**当前单元格。
  - `C`: **复制**当前单元格。
  - `X`: **剪切**当前单元格。
  - `V`: **粘贴**单元格。
  - `Z`: **撤销**删除单元格。
  - `H`: 显示所有**快捷键列表**。

**C. 其他实用功能**

- **终端 (Terminal)**:
  - 你可以像使用系统原生终端一样，在 JupyterLab 中直接打开一个终端窗口。点击 Launcher 界面的 "Terminal" 图标即可创建。
- **文件操作**:
  - 可以直接在 JupyterLab 中创建、编辑各种文本文件（`.py`, `.md`, `.txt`, `.csv` 等）。
  - 对于 CSV 等表格数据，双击文件可以在主工作区以清晰的表格形式预览。
- **魔术命令 (Magic Commands)**:
  - 在代码单元格中，以 `%` 或 `%%` 开头的特殊命令。
  - `%timeit`: 测量**单行代码**的平均执行时间。
  - `%%timeit`: 测量**整个单元格代码**的执行时间。
  - `%matplotlib inline`: 让 Matplotlib 绘制的图表直接内嵌在 Notebook 中显示。
  - `%load`: 加载一个外部脚本文件到单元格中。
  - `%lsmagic`: 列出所有可用的魔术命令。
- **安装扩展**:
  - 点击左侧边栏的拼图图标 (Extension Manager)。
  - 搜索你想要的插件，例如 `jupyterlab-git` (Git集成), `@jupyterlab/debugger` (可视化调试器), `toc` (自动生成目录)。
  - 点击 "Install" 安装。安装后可能需要重新构建 JupyterLab (`jupyter lab build`) 并刷新页面。

