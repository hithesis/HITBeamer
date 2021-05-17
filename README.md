# HITBeamer
基于 [THU-Beamer-Theme](https://github.com/Trinkle23897/THU-Beamer-Theme) 删删改改而成的 :bug:

## 编译环境
已知可行的编译环境为 `Win10 20H2` + `TeX Live 2021`

## 字体
字体部分使用了外部字体 [`Source Han Sans SC`](https://github.com/adobe-fonts/source-han-sans/tree/release/OTF/SimplifiedChinese) 与 [`FiraCode`](https://github.com/tonsky/FiraCode/releases), 点击字体名即可获取下载链接, 其中 `FiraCode` 只需要解压 `zip` 文件中的 `ttf` 文件夹即可. 下载字体后右键选择 `为所有用户安装`, 并在安装后在命令行中运行
```bash
fc-cache -fv
```
来刷新字体缓存, 即可使用这两种字体. 

如果不想使用这三种字体, 可以自行选择使用的字体或者直接注释 `packages.sty` 中的
```latex
\setCJKmainfont{Source Han Sans SC}
\setCJKsansfont{Source Han Sans SC}
\setmonofont{Fira Code}
```