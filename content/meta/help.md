---
title: Markdown Syntax Guide and Hugo Shortcodes
author: Gábor Parti
date: "2022-09-01"
weight: 9
description: "Description."
categories: ["technical","guide"]
tags: ["markdown","syntax"]
# menu: main:posts
plotly: true
# draft: false
# bookCollapseSection: true
# bookComments: true
# bookFlatSection: true
# bookHidden: true
bookSearchExclude: true
# bookToc: false
---

The following markdown file showcases all the features one can achieve within markdown and with Hugo shortcodes, which are featured on this website.

<!--more-->

<!-- Use this line above to create and expandable... -->

# MARKDOWN FORMAT

## Plotly

{{< load-plotly >}}

{{< plotly json="/plotly/distribution.json" height="200" >}}

<!-- works if I put files on main website -->

## Headings

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1
## H2
### H3
#### H4
##### H5
###### H6

Paragraphs are separated by enters.

## Emphasis

Italics with _underscores_. 

Bold with **asterisks**.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough with ~~two tildes~~.

Blockquotes: 
The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

> This is a blockquote with a >.

    This is a blockquote with a tab.

#### Blockquote without attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use *Markdown syntax* within a blockquote.

#### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

Horizontal line using `***`

***

#### Footnote

I have more [^9] to say.

[^9]: Footnote example.

## Lists

#### Ordered List

1. First item
2. Second item
3. Third item

#### Unordered List

* List item
* Another item
* And another item

#### Nested list

* Fruit
  * Apple
  * Orange
  * Banana
* Dairy
  * Milk
  * Cheese

## Todo

Todo lists can be written by using the standard Markdown syntax:

- [x] Write math example
  - [x] Write diagram example
- [ ] Do something else

## Links

#### Link to a page

[An external link](https://htmlpreview.github.io/?https://github.com/partigabor/phd-thesis-viz/blob/main/distribution_cinnamon.html)

[A relative link from one post to another post](book/introduction)

<!-- [A link to a file, needs to be on motherpage](/spice/plotly/distribution.html) --> 

[A link to heading on this page](help#figures)

## Figures 

The only correct way to insert images from static/images, but for this you need the images in the base website static folder:
```
![1](/images/diogenes.png)
```

![Image](/images/diogenes.jpg)

However, using hugo shortcode, you won't have this problem, but it only works on the main page...

```
{{\< image src="images/cardamom.png" alt="Cardamom." \>}}
```

{{< image src="images/cardamom.png" alt="Cardamom." >}}

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports them out-of-the-box.

   Name | Age
--------|------
    Bob | 27
  Alice | 23

#### Inline Markdown within tables

| Italics   | Bold     | Code[^2] |
| --------  | -------- | ------ |
| *italics* | **bold** | `code` |

[^2]: The above quote


| huh | analyzability |English|Arabic|Chinese|
|----------|---------------|-------|------|-------|
|     0    |   analyzable  |  111  |  50  |   99  |
|     1    |  unanalyzable |   39  |  32  |   20  |
|     2    |semi-analyzable|   3   |   4  |   1   |

## Code Blocks

#### Code block with backticks

```py
#Roman numerals
def roman(num: int) -> str:

    chlist = "VXLCDM"
    rev = [int(ch) for ch in reversed(str(num))]
    chlist = ["I"] + [chlist[i % len(chlist)] + "\u0304" * (i // len(chlist))
                    for i in range(0, len(rev) * 2)]
```

#### Code block indented with four spaces

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

#### Code block with Hugo's internal highlight shortcode
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

## Other Elements

#### — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.

Emoji: :heart:

https://www.webfx.com/tools/emoji-cheat-sheet/

***

# SHORTCODES


## Columns
{{< columns >}}
## One

This is one.

<--->

## Two

This is two.

{{< /columns >}}

## Buttons

Buttons are styled links that can lead to local page or external link.

```tpl
{{</* button relref="/" [class="..."] */>}}Get Home{{</* /button */>}}
{{</* button href="https://github.com/alex-shpak/hugo-book" */>}}Contribute{{</* /button */>}}
```

#### Example

{{< button relref="/" >}}Get Home{{< /button >}}
{{< button href="https://github.com/alex-shpak/hugo-book" >}}Contribute{{< /button >}}

## Hints

Hint shortcode can be used as hint/alerts/notification block.  
There are 3 colors to choose: `info`, `warning` and `danger`.

```tpl
{{</* hint [info|warning|danger] */>}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{</* /hint */>}}
```

#### Example

{{< hint info >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint warning >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint danger >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}

{{< hint cite >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}


## KaTeX

KaTeX shortcode let you render math typesetting in markdown document. See [KaTeX](https://katex.org/)

#### Example

```latex
{{</* katex [display] [class="text-center"]  */>}}
f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi
{{</* /katex */>}}
```

{{< katex display >}}
f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi
{{< /katex >}}

#### Display Mode Example

Here is some inline example: {{< katex >}}\pi(x){{< /katex >}}, rendered in the same line. And below is `display` example, having `display: block`
{{< katex display >}}
f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi
{{< /katex >}}
Text continues here.

## Details

Details shortcode is a helper for `details` html5 element. It is going to replace `expand` shortcode.

#### Example
```tpl
{{</* details "Title" [open] */>}}
## Markdown content
Lorem markdownum insigne...
{{</* /details */>}}
```
```tpl
{{</* details title="Title" open=true */>}}
## Markdown content
Lorem markdownum insigne...
{{</* /details */>}}
```

{{< details "Title" open >}}
#### Markdown content
Lorem markdownum insigne...
{{< /details >}}

## Tabs

Tabs let you organize content by context, for example installation instructions for each supported platform.

```tpl
{{</* tabs "uniqueid" */>}}
{{</* tab "MacOS" */>}} # MacOS Content {{</* /tab */>}}
{{</* tab "Linux" */>}} # Linux Content {{</* /tab */>}}
{{</* tab "Windows" */>}} # Windows Content {{</* /tab */>}}
{{</* /tabs */>}}
```

#### Example

{{< tabs "uniqueid" >}}
{{< tab "MacOS" >}}
## MacOS

This is tab **MacOS** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}

{{< tab "Linux" >}}

## Linux

This is tab **Linux** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}

{{< tab "Windows" >}}

## Windows

This is tab **Windows** content.

Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
protulit, sed sed aere valvis inhaesuro Pallas animam: qui _quid_, ignes.
Miseratus fonte Ditis conubia.
{{< /tab >}}
{{< /tabs >}}


## Mermaid Chart

[MermaidJS](https://mermaid-js.github.io/) is library for generating svg charts and diagrams from text.

{{< hint info >}}
**Override Mermaid Initialization Config**

To override the [initialization config](https://mermaid-js.github.io/mermaid/#/Setup) for Mermaid,
create a `mermaid.json` file in your `assets` folder!
{{< /hint >}}

#### Example


```tpl
{{</* mermaid [class="text-center"]*/>}}
stateDiagram-v2
    State1: The state with a note
    note right of State1
        Important information! You can write
        notes.
    end note
    State1 --> State2
    note left of State2 : This is the note to the left.
{{</* /mermaid */>}}
```


{{< mermaid >}}
stateDiagram-v2
    State1: The state with a note
    note right of State1
        Important information! You can write
        notes.
    end note
    State1 --> State2
    note left of State2 : This is the note to the left.
{{< /mermaid >}}



## Icons

Fork-Awesome Icons, use them with html inputs like this, direcly in a md file:

```html
<i class="fa fa-1x fa-rebel"></i>
```

<i class="fa fa-1x fa-rebel"></i>

https://forkaweso.me/Fork-Awesome/icons/

<a href="https://github.com/johndoe/" aria-label="Github"   >
    <i class="fa fa-2x fa-github" aria-hidden="true"></i>
</a>

<i class="fa fa-2x fa-tex" aria-hidden="true"></i>

## Gallery

{{< gallery dir="/images/cardamom/" hover-effect="slideup" />}}

{{< load-photoswipe >}}

<!-- https://github.com/liwenyip/hugo-easy-gallery -->

<!-- For later -->
<!-- https://discourse.gohugo.io/t/solved-adding-image-to-every-post/14421 -->



https://www.innoq.com/en/blog/markdown-with-zotero-workflow/


## Cite

Use CNTRL + ALT + Z to cite from Zotero

[^dalby_dangerous_2000]

[^van_wyk_culinary_2014]

[^powo]

[^ucla_medicinal_2002]

## Typography

{{< typography font="Raleway" size="32px" >}}
Raleway.
{{< /typography >}}

## Centering

{{% center %}}
Centered text
{{% /center %}}




***

> “What I like to drink most is wine that belongs to others.”<br>
> — Diogenes, 4th century BC

![Diogenes](/images/diogenes.jpg)

## References:

[^dalby_dangerous_2000]: Dalby, A. (2000). Dangerous Tastes: The Story of Spices. University of California Press. https://www.worldhistory.org/books/0520236742/
[^van_wyk_culinary_2014]: van Wyk, B.-E. (2014). Culinary Herbs and Spices of the World. University of Chicago Press, joint publication with the Royal Botanic Gardens, Kew. https://doi.org/10.7208/chicago/9780226091839.001.0001
[^powo]: POWO. (2022). Plants of the World Online (Botanical Database). Facilitated by the Royal Botanic Gardens, Kew. http://www.plantsoftheworldonline.org/
[^ucla_medicinal_2002]: Medicinal Spices Exhibit. (2002). UCLA Biomedical Library: History & Special Collections. https://unitproj.library.ucla.edu/biomed/spice/index.cfm?spicefilename=taste.txt&itemsuppress=yes&displayswitch=0
