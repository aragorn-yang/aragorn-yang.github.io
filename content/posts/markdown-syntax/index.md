---
author: Hugo Authors
title: Markdown Syntax Guide
date: 2019-03-11
draft: true
description: Sample article showcasing basic Markdown syntax and formatting for HTML elements.
categories:
  - Hugo
tags:
  - Hugo
  - markdown
math: true
---

A sample of basic Markdown syntax.

# H1 不进目录

## H2 进目录

### H3 进目录

#### H4 进目录

##### H5 不进目录

###### H6 不进目录

## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

### Blockquote without attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.

### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tables

| Name  | Age    |
| ----- | ------ |
| Bob   | **27** |
| Alice | `23`   |

## Code Blocks

### Code block with backticks

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block with Hugo's internal highlight shortcode

{{< highlight html >}}

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

### Diff code block

```diff
[dependencies.bevy]
git = "https://github.com/bevyengine/bevy"
rev = "11f52b8c72fc3a568e8bb4a4cd1f3eb025ac2e13"
- features = ["dynamic"]
+ features = ["jpeg", "dynamic"]
```

## List Types

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- List item
- Another item
- And another item

### Nested list

- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese

## Other Elements — abbr, sub, sup, kbd, mark

### abbr

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

### sub

H<sub>2</sub>O

### sup

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

### kbd

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

### mark

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.

## Rich Content

Hugo ships with
several [Built-in Shortcodes](https://gohugo.io/content-management/shortcodes/#use-hugo-s-built-in-shortcodes) for rich
content, along with a [Privacy Config](https://gohugo.io/about/hugo-and-gdpr/) and a set of Simple Shortcodes that
enable static and no-JS versions of various social media embeds.

---

### Gist

{{< gist spf13 7896402 "img.html" >}}

### `ref` and `relref`

会让两个关联页面的「相关文章」部分列出对方

> The only difference between ref and relref is whether the resulting URL is absolute (http://1.com/about/) or relative (/about/), respectively.

`relref`: relative ref [Who]({{< relref "about.md#who" >}})

`ref`: [Emoji Support]({{< ref "posts/emoji-support.md" >}})

### YouTube Privacy Enhanced Shortcode

{{< youtube ZJthWmvUzzc >}}

<br>

---

### Twitter Simple Shortcode

{{< twitter_simple 1453110110599868418 >}}
`twitter_simple` 只需要 tweet id
`tweet` 需要 user name 和 tweet id

### Twitter Shortcode

{{< tweet user="SanDiegoZoo" id="1453110110599868418" >}}

---

### Vimeo Simple Shortcode

{{< vimeo_simple 48912912 >}}
`vimeo_simple` better than `vimeo`

<br>

---

### bilibilibi Shortcode

{{< bilibili av498363026 >}}

<br>

---

### Inline CSS

<svg class="canon" xmlns="http://www.w3.org/2000/svg" overflow="visible" viewBox="0 0 496 373" height="373" width="496"><g fill="none"><path stroke="#000" stroke-width=".75" d="M.599 372.348L495.263 1.206M.312.633l494.95 370.853M.312 372.633L247.643.92M248.502.92l246.76 370.566M330.828 123.869V1.134M330.396 1.134L165.104 124.515"></path><path stroke="#ED1C24" stroke-width=".75" d="M275.73 41.616h166.224v249.05H275.73zM54.478 41.616h166.225v249.052H54.478z"></path><path stroke="#000" stroke-width=".75" d="M.479.375h495v372h-495zM247.979.875v372"></path><ellipse cx="498.729" cy="177.625" rx=".75" ry="1.25"></ellipse><ellipse cx="247.229" cy="377.375" rx=".75" ry="1.25"></ellipse></g></svg>

{{< css.inline >}}

<style>
.canon { background: white; width: 100%; height: auto; }
.emoji {
  font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
}
</style>

{{< /css.inline >}}

## Math Typesetting

A brief guide to setup KaTeX

Mathematical notation in a Hugo project can be enabled by using third party JavaScript libraries.

<!--more-->

In this example we will be using [KaTeX](https://katex.org/)

- Create a partial under `/layouts/partials/math.html`
- Within this partial reference the [Auto-render Extension](https://katex.org/docs/autorender.html) or host these scripts locally.
- Include the partial in your templates like so:

```bash
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```

- To enable KaTex globally set the parameter `math` to `true` in a project's configuration
- To enable KaTex on a per page basis include the parameter `math: true` in content files

**Note:** Use the online reference of [Supported TeX Functions](https://katex.org/docs/supported.html)

{{< math.inline >}}
{{ if or .Page.Params.math .Site.Params.math }}

<!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
{{ end }}
{{</ math.inline >}}

### Examples

{{< math.inline >}}

<p>
Inline math: \(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

Block math:

$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } }
$$
