---
layout: post
title: 我的sublime配置
description: ""
category:
tags: ["工具"]
comments: true
---
{% include JB/setup %}

	从“视窗系统”切换到Mac后很多东西都要重新配置，当然包括常用的Sublime Text。
	之前用的是ST2，想着都要重新配置就尝试了一下ST3，发觉更好用！
	以后工作有工资了一定会买一个license的。

---

基本配置参考
---------
[Sublime Text 2 设置文件详解](http://www.feelcss.com/sublime-text-2-settings.html)  
[Sublime Text 3 学习及使用](http://blog.csdn.net/idxuanjun/article/details/13292847)  
[拼写检查](http://feliving.github.io/Sublime-Text-3-Documentation/spell_checking.html)  
[自定义主题编辑](http://tmtheme-editor.herokuapp.com/#/theme/Monokai)

	PS. 建议把代码补全的原快捷键'ctrl+space' 改为cmd+`(for mac), alt+`(for win)

Package Control 安装
-------------------
[安装指导](https://sublime.wbond.net/installation)  
简单描述就是打开ST3，然后输入**ctrl+`**(或者使用View->Show Console)，然后在粘贴页面中的代码运行即可。  

插件安装方法：  
安装完Package Control之后，打开ST3输入`cmd+shift+p`，然后在输入install即可。  

基本插件
------
1. **ConvertToUTF8**  
支持 GBK, BIG5, EUC-KR, EUC-JP, Shift_JIS 等编码的插件。
打开win下的默认编码文件必备！

2. **Bracket Highlighter**  
用于匹配括号，引号和html标签。对于很长的代码很有用。  
安装好之后，不需要设置插件会自动生效。但是为了更好的效果可以配置一下。  
[配置指南](#BracketHighlighter配置) 见附录

3. **DocBlockr**  
DocBlockr可以自动生成PHPDoc风格的注释。它支持的语言有Javascript, PHP, ActionScript, CoffeeScript, Java, Objective C, C, C++。  
比如java就是在代码比如函数前输入`/**`然后回车即可。

4. **KeymapManager**  
插件快捷键管理，快捷键ctrl+alt+k

5. Sublime CodeIntel  
代码自动提示

6. Sublime Alignment  
代码对齐，快捷键`shift+cmd+a`  
[配置](https://gist.github.com/ufologist/5590481#file-base-file-sublime-settings)  

7. Git  
比较完整了

8. SublimeTmpl  
快速生成文件模板  
[配置](http://www.fantxi.com/blog/archives/sublime-template-engine-sublimetmpl/)  

9. Highlight  
复制高亮代码的工具，当然也可以使用[在线工具](http://tool.oschina.net/highlight)

10. Color Highlighter  
把相应的颜色代码显示为颜色。  
在tool里面可以设置，建议开启highlight all, 然后可以设置样式。  
选中时可以是`filled`，highlight all的样式可以是`underline(solid)`

11. soda  
可以给ST换个皮肤

12. DashDoc  
Mac下与Dash软件配合使用，选中某个系统函数然后用快捷键`ctrl+h`进行查询

Python插件
---------
1. sublimePythonIDE 好用!
不仅有补全，而且还会做代码风格检查，强迫症养成！
补全可能是异步处理的，越用越好用。

2. sublimeREPL 
可以在sublime里面运行ipython，不过似乎没有解决中文问题。

前端开发插件
---------
1. **Emmet(Zen Coding)**  
快速生成HTML代码段的插件，强大到无与伦比。  
参考教程：  
[Sublime Text2 中Emmet(之前叫Zencoding)插件安装以及使用](http://www.blogjava.net/Hafeyang/archive/2013/01/19/emmet_fomer_zencoding_in_sublime_text_2.html)  
[分享7个超实用的Emmet（zen coding）HTML代码使用技巧](http://www.cnblogs.com/meetrice/archive/2013/01/27/2878548.html)  
[Emmet的高级功能与使用技巧](http://salonglong.com/emmet-advanced.html)  
[前端开发必备！Emmet使用手册](http://www.w3cplus.com/tools/emmet-cheat-sheet.html)  
[cheat-sheet](http://docs.emmet.io/cheat-sheet/)  

2. JsFormat  
格式化js代码，这个插件很有用，我们有时在网上看到某些效果，想查看是怎么实现的，但是代码被压缩过，很难阅读。默认快捷键：

3. Autoprefixr(Sublime Prefixr)  
Prefixr，CSS3 私有前缀自动补全插件，快捷键 

4. ColorPicker  
调色盘

5. sublime-API-Completions-Package(javascript-API-Completions)  
支持Javascript、JQuery、Twitter Bootstrap框架、HTML5标签属性提示的插件，是少数支持ST 3的后缀提示的插件，HTML5标签提示ST3自带，不过JQuery提示还是很有用处的，也可设置要提示的语言。

---
6. Goto-CSS-Declaration  
跳转到css文件该class的声明处，方便修改查看，如图下所示，注意对应的css文件要同时打开才行。

7. minifier —— css,js 压缩

Markdown插件
-----------
首先是预览，可以使用ST的插件(Markdown Preview)，也可以浏览器Chrome装插件(Markdown Preview Plus)。  
提高效率的编辑插件`MarkdownEditing`，不过我没用过，所以不评价。  

ST的语法高亮 [Monokai-custom.tmTheme](http://pan.baidu.com/share/link?shareid=1284918352&uk=4043483013)

markdown-css: [CSS stylesheets / themes for Markdown](http://mixu.net/markdown-styles/)  

markdown教程：[Markdown 语法说明 (简体中文版)](http://wowubuntu.com/markdown/)

删除的插件
--------
1. colorcoder  
可以自动给每个变量都设置不同的颜色，太花销了就删了。

待考察插件
--------
1. **SideBar Enhancements**  
这个插件改进了侧边栏，增加了许多功能。  
考察结果：好用，把文件夹直接拖到ST就是一个项目了

2. **Xdebug**  
可以安装xdebug插件，做代码调试功能。 这是大型IDE都有的功能， 小型编辑器很少能做到，但是sublime却又相应的插件能实现xdebug的功能。

3. Tag  
HTML标签补完、格式化

4. Placeholders  
故名思意，占位用，包括一些占位文字和HTML代码片段，实用。

5. Hex to HSL  
自动转换颜色值，从16进制到HSL格式，快捷键 Ctrl+Shift+U

6. TrailingSpacer  
高亮显示多余的空格和Tab

7. Clipboard-history  
粘贴板历史记录

8. Google spell check  

9. jQuery  
jQuery

10. LiveReload —— 让页面即时刷新  
这个功能我是使用Chrome的smartF5事项的。

11. Pretty JSON —— JSON美化扩展；

12. Can I Use —— 查询 CSS 属性兼容情况；

13.  AutoFileName 自动补全文件(目录)名

14. SublimeJEDI 自动补全

15. Anaconda python自动补全

参考网站
------
[Sublime Text 3 绝对神器](http://www.cnblogs.com/bananaplan/p/Sublime-Text-3-Powerful.html)  
[Sublime Text 2 使用心得](http://www.cnblogs.com/leecanz/archive/2012/03/04/2379446.html)  
[一些必不可少的Sublime Text 2插件](http://www.qianduan.net/essential-to-sublime-the-text-2-plugins.html)  
[Sublime Text 2 入门及技巧](http://lucifr.com/2011/08/31/sublime-text-2-tricks-and-tips/)  
[Sublime Text 3能用支持的插件推荐](http://dengo.org/archives/923)  
[SubLime BracketHighlighter 配置](http://www.cnblogs.com/cart55free99/p/3502025.html)  
[Python程序员的 Sublime Text 2 配置](http://cndenis.iteye.com/blog/1776192)  
*[Web Inspector：在 Sublime Text 中调试 JavaScript 代码](http://www.cnblogs.com/lhb25/archive/2013/04/18/sublime-text-debugger-javascript.html)  

附录
===
BracketHighlighter配置
----------------------

1. 通过Package Setting打开Bracket Highlighter的default setting。然后复制到它的User setting里面，再修改，当然也可以直接在default里面修改吧。  
2. 主要是把“bracket_styles”里面的每一项的color还有style都取消注释，注意在相应的位置加上逗号。  
style有三种样式：`"underline"`, `"outline"`, `"highlight"`  
3. 在你使用的主题文件后面添加一下对颜色定义的代码：  
添加到什么位置的话，自己根据文件判断一下咯  

{% highlight xml %}
<dict>
<key>name</key>
<string>Default</string>
<key>scope</key>
<string>brackethighlighter.default</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#E6E6E6</string>
        <key>background</key>
        <string>#00BFFF</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Unmatched</string>
<key>scope</key>
<string>brackethighlighter.unmatched</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#E6E6E6</string>
        <key>background</key>
        <string>#FF0000</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Bracket Curly</string>
<key>scope</key>
<string>brackethighlighter.curly</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#F7BE81</string>
        <key>background</key>
        <string>#0080FF</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Bracket Round</string>
<key>scope</key>
<string>brackethighlighter.round</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#F5D0A9</string>
        <key>background</key>
        <string>#00BFFF</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Bracket Square</string>
<key>scope</key>
<string>brackethighlighter.square</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#E6E6E6</string>
        <key>background</key>
        <string>#00FFFF</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Bracket Angle</string>
<key>scope</key>
<string>brackethighlighter.angle</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#F7FE2E</string>
        <key>background</key>
        <string>#AE81FF</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Bracket Tag</string>
<key>scope</key>
<string>brackethighlighter.tag</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#01DFD7</string>
        <key>background</key>
        <string>#BEF781</string>
    </dict>
</dict>

<dict>
<key>name</key>
<string>Single Quote | Double Quote | Regex</string>
<key>scope</key>
<string>brackethighlighter.quote</string>
<key>settings</key>
    <dict>
        <key>foreground</key>
        <string>#8054fa</string>
        <key>background</key>
        <string>#A9F5A9</string>
    </dict>
</dict>
{% endhighlight %}

下面是我的user setting的部分配置：  
{% highlight json %}
"default": {
    "icon": "dot",
    "color": "brackethighlighter.default",
    "style": "highlight"
},

"unmatched": {
    "icon": "question",
    "color": "brackethighlighter.unmatched",
    "style": "highlight" 
},
// User defined region styles
"curly": {
    "icon": "curly_bracket",
    "color": "brackethighlighter.curly",
    "style": "highlight"
},
"round": {
    "icon": "round_bracket",
    "color": "brackethighlighter.round",
    "style": "highlight"
},
"square": {
    "icon": "square_bracket",
    "color": "brackethighlighter.square",
    "style": "highlight"
},
"angle": {
    "icon": "angle_bracket",
    "color": "brackethighlighter.angle",
    "style": "underline"
},
"tag": {
    "icon": "tag",
    "color": "brackethighlighter.tag",
    "style": "outline"
},
"single_quote": {
    "icon": "single_quote",
    "color": "brackethighlighter.quote",
    "style": "highlight"
},
"double_quote": {
    "icon": "double_quote",
    "color": "brackethighlighter.quote",
    "style": "highlight"
},
"regex": {
    "icon": "regex",
    "color": "brackethighlighter.quote",
    "style": "highlight"
}
{% endhighlight %}


