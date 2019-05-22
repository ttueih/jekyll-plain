---
title: Test math
tags: 
   - jekyll 
   - test
   - markdown
   - mathjax
date: 2019-05-20 15:06:26 +0100
---

There are two different ways to render \\( \LaTeX \\) on Jekyll, either using [**MathJaX**](https://www.mathjax.org) or [**KaTeX**](https://katex.org).
MathJaX is more popular and more powerful compared to KaTeX which is a relatively light-weight library. 
However, KaTeX is way faster than MathJaX and is recommended for posts with the large number of mathematic content.

<!--description-->

It is possible to integrate KaTeX into Jekyll using either a plugin [jekyll-katex](https://github.com/linjer/jekyll-katex)
or [replace MathJaX tag on-the-fly](https://xuc.me/blog/katex-and-jekyll/).
The problem with the first approach is that It make our Jekyll page not buildable with Github self build function.
It is beacause Github only supports a limited set of plugins due to security reason.
Although we can build our site locally and push the generated `_site` folder to Github, this is quite inconvenient to have a computer with everything set up 
just to write a small post.
The second approach seems promising since our site is still buildable with Github. The only draw-back is that we cannot use some special MathJaX features such as extensions.

Rendering speed may become an issue soon or later, but keeping everything simple is more important. Therefore, let stick to MathJaX this time.

## MathJaX
In Mathjax, there are two ways to insert math tex: `\\( \\)` for inline math and `$$  $$` for display mode.

For instance, an inline math like `\\( f(x,y) = x^2 + xy +1 \\)` will be rendered as 
\\( f(x,y) = x^2 + xy +1 \\)
and `$$ f(x,y) = \frac{x^2 + xy +1}{xy^2-1} $$ ` will give us

$$ f(x,y) = \frac{x^2 + xy +1}{xy^2-1} $$

The interesting thing about MathJaX is that there are many handy extensions.
For example:
```
$$\require{\AMScd}$$

$$\begin{CD}
A @<<< B @>>> C\\
@. @| @AAA\\
@. D @= E
\end{CD}$$
```

will allow us to use `amscd` to draw a diagram:

$$\require{\AMScd}$$
$$\begin{CD}
A @<<< B @>>> C\\
@. @| @AAA\\
@. D @= E
\end{CD}$$

More about MathJaX extensions can be found [here](http://docs.mathjax.org/en/latest/tex.html#tex-and-latex-extensions)

## Other Notes

We can use [TikzJaX](https://github.com/kisonecat/tikzjax) to render Tikz diagram on web.
The installation is simple but this solution itself is not good enough to be integrated in this site.
To handle the processing of Tikz commands and generate SVG code, the author need to run his own server which is not realiable enough. 
Another issue is that only *http* is supported at the time of this note. Therefore, the script is refused to start if we access our site with *https*

