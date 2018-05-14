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

3. 下载插件 <br/>
![插件下载](/images/插件下载.png)

4. 安装字体<br/>
下载字体点[这里](https://pan.baidu.com/s/1UkZgWqMfpaEyr4V9vWa46g) &emsp;密码: agsv
<br/>
安装字体将文件移进'>C:/windows>Font'目录下即可。
<br/>

5.加载文件<br/>
最后一步，将本目录下的doc加载到vscode里面.<br/>
具体操作如下：<br/>
`> 文件 > 将文件夹加载到工作区`&emsp; 或者是 直接将文件拖到`VsCode`里面即可

* `重要事情说三遍：Windows用户不要将路径和图片名称命名为汉字`
* `重要事情说三遍：Windows用户不要将路径和图片名称命名为汉字`
* `重要事情说三遍：Windows用户不要将路径和图片名称命名为汉字`
<br/>
ctrl+s即可编译


