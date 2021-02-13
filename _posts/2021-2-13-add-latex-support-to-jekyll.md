---
layout: post
title: 让 Jekyll 支持LaTex数学公式（MathJax v3）
date: 2021-2-13
categories:
- 技术笔记
tags:
- github
- latex
typora-root-url: ../
---

# 前言

最近在GitHub上建站，使用了[cotes2020](https://github.com/cotes2020/jekyll-theme-chirpy)的Jekyll网页模版。模版很好用😄，但是美中不足的是不支持LaTex数学公式。因为最近几篇博客里使用了LaTex，于是开始DIY。

Google了许多解决方案，发现基本都是使用MathJax v2版本。虽然也能使用，但是不折腾毋宁死的我就是想用最新的MathJax v3。于是一段冒险之旅开始了。

# LaTex公式

用LaTex写过数学公式的同学都知道，行内公式用`$ 一些公式 $`，公式块用`$$`包围。

比如公式：

$$
ax^2 + bx + c = 0
$$

公式块的代码就是

```latex
$$
ax^2 + bx + c = 0
$$
```

# MathJax v3

[MathJax](https://www.mathjax.org/#gettingstarted)是一个JS的数学公式实现，支持LaTex语法。我们一般在HTML里引用就可以在页面里添加公式支持啦。这里我们只使用最新MathJax v3。

只需要在HTML的`<head>`标签里加入：

```html
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
```

[polyfill](https://polyfill.io/v3/)看了一下，是用来对老浏览器做支持的。如果不需要，也可以不引入。

### 行内公式配置

将脚本嵌入之后，默认的行内标签是`\( 一个公式 \)`，这并不符合使用LaTex的习惯，所以需要做一下配置，让其支持`$`符号。参照MathJax的[配置文档](http://docs.mathjax.org/en/latest/options/input/tex.html#option-descriptions)，我们在html文件里加入：[<sup>1</sup>](#ref1)

```html
<script> 
MathJax = {
  tex: {
    inlineMath: [['$', '$']],
    processEscapes: true
  }
};
</script>
```

这里`MathJax = {}`是MathJax v3的配置对象

- `inlineMath`参数可以配置行内公式块的分隔符（delimiters），这里我们配置成美元符号`$`。这样就更符合我们的使用习惯啦。

- `processEscapes`参数配置我们在页面里是否需要转义，一般我们会设置为`true`，这样在页面里我们就可以使用`\$`来正常打印美元标志，而不会被识别成分隔符。
- MathJax还支持更多配置，具体可以参考文档。

# 集成到 Jekyll

接下来我们把MathJax集成到Jekyll模版引擎。

首先需要确认Jekyll的默认markdown解析器为kramdown。去`_config.yaml`里看看吧。

然后，我们有几种方案：[<sup>2</sup>](#ref2)

- 直接嵌入到博客markdown文件的开头里。这样只能让单篇文章支持公式。
- 嵌入到`<head>`中，让全站支持公式。添加到Jekyll目录下的`_layouts/head.html`文件里就可以了，一般模版都会有这个文件。
- 嵌入到`post.html`，仅让post页面支持公式。只需要把公式块添加到`_layouts/post.html`文件中。一般模版也会有这个文件。

因为我想把影响控制到最小，所以使用了第三个方案。最终我把代码块添加到了`post.html`的文件末尾。

配置好以后，所有引用post这个layout的md文件都可以支持公式了，很开心。

随心所欲地在博客里写公式吧！

# 参考文献

<span id="ref1">1.[Mathjax inline mode not rendering - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/27633/mathjax-inline-mode-not-rendering)</span>

<span id="ref2">2.一个GitHub大神对将MathJax集成到Jekyll的建议，注意是MathJax v2 https://github.com/github/pages-gem/issues/307#issuecomment-289536076</span>