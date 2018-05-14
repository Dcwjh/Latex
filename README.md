# Latex+vscode编写江南大学毕业论文

## 简单介绍模板的使用<br/>

1. 下载软件
* Latex:&ensp; [官网](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe)&ensp;| 
&ensp;[清华镜像](http://mirror.ctan.org/systems/texlive/Images/texlive2018.iso)
2. 准备工作
工作区设置 <br/>
`> .vscode > setting.json > 工作区设置` ：
```tex
{
    "latex-workshop.latex.tools": [
        {
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdfxe",
                "%DOC%"
            ],
            "name": "Step 1: latexmk"
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "toolchain",
            "tools": [
                "Step 1: latexmk"
            ]
        }
    ],
    "latex-workshop.view.pdf.viewer": "tab",
    "editor.renderControlCharacters": true,
    "workbench.activityBar.visible": false,
    "workbench.statusBar.visible": false,
    "workbench.startupEditor": "newUntitledFile",
    "editor.minimap.enabled": false,
    "explorer.confirmDelete": false
}
```
![工作区设置](/images/工作区设置.png)

3. 下载插件
![插件下载](插件下载.png)
