# 代码块样式/主题

2016 年 6 月 22 日 由 typora.io

> 提示：要知道将这些 CSS 片段放在哪里，请参阅[添加自定义 CSS](https://support.typora.io/Add-Custom-CSS/)。

Typora 使用[CodeMirror](http://codemirror.net/)在代码栅栏中突出显示语法。Typora 中的代码栅栏`cm-s-inner`用作它们的主题类。

将 CodeMirror 主题移植到 Typora，例如[material.css](https://codemirror.net/theme/material.css)：

sdhvgdflksnv
sldoahgfjdlgv
vmfdlks

1. 复制并粘贴到主题文件夹 `base.user.css` 或`[theme].user.css`主题文件夹下，并将其 CodeMirror 主题类名称替换`cm-s-inner`为 ，例如，将原始更改`.cm-s-material`为`.cm-s-inner`.
2. 在由 CodeMirror 呈现之前，代码栅栏具有类似`<pre class="md-fences"></pre>`. 因此，请将字体系列、颜色和背景等基本样式应用到`.md-fences`选择器中。

所以最终的 CSS 将是：

```css
/** ported from https://codemirror.net/theme/material.css **/
/*

    Name:       material
    Author:     Michael Kaminsky (http://github.com/mkaminsky11)

    Original material color scheme by Mattia Astorino (https://github.com/equinusocio/material-theme)

*/

.cm-s-inner {
  background-color: #263238;
  color: rgba(233, 237, 237, 1);
}
.cm-s-inner .CodeMirror-gutters {
  background: #263238;
  color: rgb(83,127,126);
  border: none;
}
.cm-s-inner .CodeMirror-guttermarker, .cm-s-inner .CodeMirror-guttermarker-subtle, .cm-s-inner .CodeMirror-linenumber { color: rgb(83,127,126); }
.cm-s-inner .CodeMirror-cursor { border-left: 1px solid #f8f8f0; }
.cm-s-inner div.CodeMirror-selected { background: rgba(255, 255, 255, 0.15); }
.cm-s-inner.CodeMirror-focused div.CodeMirror-selected { background: rgba(255, 255, 255, 0.10); }
.cm-s-inner .CodeMirror-line::selection, .cm-s-inner .CodeMirror-line > span::selection, .cm-s-inner .CodeMirror-line > span > span::selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-inner .CodeMirror-line::-moz-selection, .cm-s-inner .CodeMirror-line > span::-moz-selection, .cm-s-inner .CodeMirror-line > span > span::-moz-selection { background: rgba(255, 255, 255, 0.10); }

.cm-s-inner .CodeMirror-activeline-background { background: rgba(0, 0, 0, 0); }
.cm-s-inner .cm-keyword { color: rgba(199, 146, 234, 1); }
.cm-s-inner .cm-operator { color: rgba(233, 237, 237, 1); }
.cm-s-inner .cm-variable-2 { color: #80CBC4; }
.cm-s-inner .cm-variable-3 { color: #82B1FF; }
.cm-s-inner .cm-builtin { color: #DECB6B; }
.cm-s-inner .cm-atom { color: #F77669; }
.cm-s-inner .cm-number { color: #F77669; }
.cm-s-inner .cm-def { color: rgba(233, 237, 237, 1); }
.cm-s-inner .cm-string { color: #C3E88D; }
.cm-s-inner .cm-string-2 { color: #80CBC4; }
.cm-s-inner .cm-comment { color: #546E7A; }
.cm-s-inner .cm-variable { color: #82B1FF; }
.cm-s-inner .cm-tag { color: #80CBC4; }
.cm-s-inner .cm-meta { color: #80CBC4; }
.cm-s-inner .cm-attribute { color: #FFCB6B; }
.cm-s-inner .cm-property { color: #80CBAE; }
.cm-s-inner .cm-qualifier { color: #DECB6B; }
.cm-s-inner .cm-variable-3 { color: #DECB6B; }
.cm-s-inner .cm-tag { color: rgba(255, 83, 112, 1); }
.cm-s-inner .cm-error {
  color: rgba(255, 255, 255, 1.0);
  background-color: #EC5F67;
}
.cm-s-inner .CodeMirror-matchingbracket {
  text-decoration: underline;
  color: white !important;
}

/**apply to code fences with plan text**/
.md-fences {
  background-color: #263238;
  color: rgba(233, 237, 237, 1);
  border: none;
}

.md-fences .code-tooltip {
  background-color: #263238;
}
```

结果是：![截图20160623_11](https://support.typora.io/media/code-block-style/Snip20160623_11.png)

您可以按照上面的示例编写自己的 CSS 样式以进行语法高亮显示。

请注意，`cm-s-inner`这只适用于代码围栏：它不会影响源代码模式下的降价语法。并非所有 CSS 属性都会应用于源代码模式下的代码栅栏。