> **⚠️ 本仓库已停止维护。**
> 主题已完整移植到新仓库 [**hiTouyingBeamer**](https://github.com/hithesis/hiTouyingBeamer)，
> 用 `\usetheme[classic]{hit}` 即可得到与本模板一致的经典观感，并持续跟进新的 TeX Live。
> 旧代码在今天的 TeX Live（2024 及以后）下已无法开箱编译：`hit-extra` 会强制加载
> 很多发行版默认不装的 `pstricks`，Fira Math 按文件名加载也已失效。请移步新仓库。

# HITBeamer


基于 [THU-Beamer-Theme](https://github.com/Trinkle23897/THU-Beamer-Theme) 删删改改而成的 :bug:

## 迁移到新仓库

[hiTouyingBeamer](https://github.com/hithesis/hiTouyingBeamer) 完整移植了本模板：
smoothbars 顶栏、两行页脚、circle 列表、编号圆球目录、`\section` / `\subsection` 后自动
插目录帧等全部保留。旧文档只需改导言区那几行，正文一般不用修改：

```latex
% 旧（本仓库）
\documentclass{beamer}
\usepackage{hit-style}
\usepackage[minted,fira,siyuan]{hit-extra}

% 新（hiTouyingBeamer）
\documentclass[aspectratio=169]{ctexbeamer} % 默认 4:3 或者显式写 aspectratio=43
\usetheme[classic]{hit}                     % classic 就是本仓库的经典效果
```

## 编译环境

已知可行的编译环境为 

* `Win11 21H1` + `TeX Live 2022`
* `Arch Linux` + TeX Live 2022`

## 字体

字体部分使用了外部字体 [`Source Han Sans SC`](https://github.com/adobe-fonts/source-han-sans/tree/release/OTF/SimplifiedChinese), [`FiraCode`](https://github.com/tonsky/FiraCode/releases) 以及 [`FiraGO`](https://bboxtype.com/downloads/FiraGO/Download_Folder_FiraGO_1001.zip), 点击字体名即可获取下载链接, 其中 `FiraCode` 只需要解压 `zip` 文件中的 `ttf` 文件夹, `FiraGO` 需要解压 `Download_Folder_FiraGO_1001.zip\Download_Folder_FiraGO_1001\Fonts\FiraGO_OTF_1001`. 下载字体后右键选择 `为所有用户安装`, 并在安装后在命令行中运行

```bash
fc-cache -fv
```

来刷新字体缓存, 即可使用这两种字体.

如果不想使用这两种字体, 可以取消 `hit-extra` 的选项 `siyuan` 和 `fira`，即

```latex
\usepackage[minted, fira, siyuan]{hit-extra}
        ↓
\usepackage[minted]{hit-extra}
```

## `minted` 宏包

本模板使用了 [`minted`](https://www.ctan.org/pkg/minted) 宏包来排版代码, 该宏包需要 `python` 与 python 模块 `pygments`. 安装方法:

1. 从 [python 官网](https://www.python.org/) 下载最新版的 `python`,
2. 在命令行运行 `pip install pygments` 安装 `pygments`,
3. 命令行运行 `pygmentize -L lexers` 来查看 `pygments` 可以渲染的语言,
4. 编译的时候记得添加编译选项 `-shell-escape`

如果是 [`Anaconda`](https://www.anaconda.com/) 用户, 可以将第 2 步中的 `pip` 改为 `conda` 来使用 `conda` 安装.

如果不想使用 `minted` 宏包, 可以取消 `hit-extra` 的 `minted` 选项以及删除 `slide.tex` 中的带 `mint` 的语句即可. 原模板同样提供了 `listings` 宏包来排版代码, 在 `slide.tex` 中同样给了[示例](https://github.com/syvshc/HITBeamer/blob/master/slide.tex#L220)

## 编译方法

命令行进入 `slide.tex` 所在的文件夹, 运行

```bash
xelatex -shell-escape slide
bibtex slide 
xelatex -shell-escape slide
xelatex -shell-escape slide
```

或者使用一步到位的 `latexmk` 命令: 运行

```bash
latexmk
```

该方法会在保存时检测文件改动并自动编译, 如果不想让它自动编译, 那么可以将命令改为

```bash
latexmk -pvc-
```

来临时抑制此功能, 或将 [latexmkrc](https://github.com/syvshc/HITBeamer/blob/master/latexmkrc) 中的

```bash
$preview_continuous_mode = 1;
```

删除来永久删除此功能.

## 开源协议

本文档遵循 LPPL (The LaTeX Project Public License) Version 1.3c  及以后的开源协议.
