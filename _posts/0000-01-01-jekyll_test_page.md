---
layout: post
title:  Jekyll test page 
category: Test / teszt
comments: false
tags: [web, jekyll, github]
---

<!-- break -->

<div class="rightbox" style="width: 30%;"><a class="twitter-timeline" href="https://twitter.com/FleXoft?ref_src=twsrc%5Etfw" data-tweet-limit="1" data-chrome="nofooter noborders noscrollbar transparent">Tweets by FleXoft</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script></div>

Aenean non sapien sit amet eros pulvinar rutrum. Phasellus quis gravida lorem, vulputate sollicitudin mi. Sed tempus tincidunt ipsum, sit amet pulvinar enim dictum eu. Etiam feugiat accumsan velit. Sed euismod euismod elit auctor iaculis. Curabitur eu ipsum sodales, luctus dolor non, tempus magna. Donec aliquam, magna sit amet interdum pretium, odio justo molestie mi, quis feugiat ligula tortor auctor metus. Pellentesque sapien odio, pharetra non felis in, mollis aliquet mauris.

``` shell

#! /bin/sh
echo alma
echo Hello word.
>> alma

```

Integer odio tortor, tempor at diam quis, rhoncus elementum risus. Phasellus mollis quis tortor ut tincidunt. Curabitur consequat ipsum quis nisi eleifend, vitae malesuada nunc rutrum. Aliquam sapien odio, ultricies fringilla turpis eu, elementum posuere purus. Ut iaculis ac ante vel aliquam. Nulla vel feugiat diam, vitae gravida orci. Interdum et malesuada fames ac ante ipsum primis in faucibus. Morbi semper sapien et velit rhoncus tincidunt. Sed at eros ornare, egestas diam ac, interdum sapien. Ut sapien metus, faucibus at feugiat et, luctus at urna. Morbi luctus nisi orci, quis rhoncus mi accumsan sed. Sed vulputate et risus eu rhoncus. Donec a quam id erat suscipit bibendum. Donec viverra leo a sodales luctus. Curabitur pretium diam a est condimentum pretium vel nec eros.

Added a new repo, that is, `/maps` for hosting 'full-screen'
interactive beer maps with brewery listings.

See an example [beer map for Austria](http://openbeer.github.io/maps/at) (~200 breweries n brewpubs)
live or [check the source using](https://github.com/openbeer/maps) the mapbox.js mapping library.

# MacDown

<div class="rightbox" style="width: 35%;"><img class="shadow" src="images/flickr_thumb.png" alt="fffff" /></div>

<div class="rightbox" style="width: 15%;"><img class="shadow" src="images/flickr_thumb.png" alt="fffff" /><br><img class="shadow" src="images/flickr_thumb.png" alt="fffff" /></div>

Hello there! I’m **MacDown**, the open source Markdown editor for OS X.

Let me introduce myself.

## H2

### H3

You can specify extra HTML rendering options through the [**Rendering** preference pane](#rendering-pane).

You can customize the editor window to you liking in the [**Editor** preferences pane](#editor-pane):

You can configure various application (that's me!) behaviors in the [**General** preference pane](#general-pane).

## The Basics
Before I tell you about all the extra syntaxes and capabilities I have, I'll introduce you to the basics of standard markdown. If you already know markdown, and want to jump straight to learning about the fancier things I can do, I suggest you skip to the [**Markdown** preference pane](#markdown-pane). Lets jump right in.  

### Line Breaks
To force a line break, put two spaces and a newline (return) at the end of the line.

* This two-line bullet 
won't break

* This two-line bullet  
will break

Here is the code:

```
* This two-line bullet 
won't break

* This two-line bullet  
will break
```

### Strong and Emphasize

**Strong**: `**Strong**` or `__Strong__` (Command-B)  
*Emphasize*: `*Emphasize*` or `_Emphasize_`[^emphasize] (Command-I)

### Headers (like this one!)

    Header 1
    ========

    Header 2
    --------

or

    # Header 1
    ## Header 2
    ### Header 3
    #### Header 4
    ##### Header 5
    ###### Header 6

### Links and Email
#### Inline
Just put angle brackets around an email and it becomes clickable: <uranusjr@gmail.com>  
`<uranusjr@gmail.com>`  

Same thing with urls: <http://macdown.uranusjr.com>  
` <http://macdown.uranusjr.com>`  

Perhaps you want to some link text like this: [Macdown Website](http://macdown.uranusjr.com "Title")  
`[Macdown Website](http://macdown.uranusjr.com "Title")` (The title is optional)  


#### Reference style
Sometimes it looks too messy to include big long urls inline, or you want to keep all your urls together.  

Make [a link][arbitrary_id] `[a link][arbitrary_id]` then on it's own line anywhere else in the file:  
`[arbitrary_id]: http://macdown.uranusjr.com "Title"`
  
If the link text itself would make a good id, you can link [like this][] `[like this][]`, then on it's own line anywhere else in the file:  
`[like this]: http://macdown.uranusjr.com`  

[arbitrary_id]: http://macdown.uranusjr.com "Title"
[like this]: http://macdown.uranusjr.com  

### Images
#### Inline
`![Alt Image Text](path/or/url/to.jpg "Optional Title")`
#### Reference style
`![Alt Image Text][image-id]`  
on it's own line elsewhere:  
`[image-id]: path/or/url/to.jpg "Optional Title"`

### Lists

* Lists must be preceded by a blank line (or block element)
* Unordered lists start each item with a `*`
- `-` works too
    * Indent a level to make a nested list
	1. Ordered lists are supported.
	2. Start each item (number-period-space) like `1. `
	42. It doesn't matter what number you use, I will render them sequentially
	1. So you might want to start each line with `1.` and let me sort it out

Here is the code:

```
* Lists must be preceded by a blank line (or block element)
* Unordered lists start each item with a `*`
- `-` works too
    * Indent a level to make a nested list
	1. Ordered lists are supported.
	2. Start each item (number-period-space) like `1. `
	42. It doesn't matter what number you use, I will render them sequentially
	1. So you might want to start each line with `1.` and let me sort it out
```

### Block Quote

> <p style='margin:0px'></p> Angle brackets `>` are used for block quotes.  
Technically not every line needs to start with a `>` as long as
there are no empty lines between paragraphs.  
> Looks kinda ugly though.
> > <p style='margin:0px'></p> Block quotes can be nested.  
> > > <p style='margin:0px'></p>Multiple Levels
>
> Most markdown syntaxes work inside block quotes.
>
> * Lists
> * [Links][arbitrary_id]
> * Etc.

Here is the code:

```
> Angle brackets `>` are used for block quotes.  
Technically not every line needs to start with a `>` as long as
there are no empty lines between paragraphs.  
> Looks kinda ugly though.
> > Block quotes can be nested.  
> > > Multiple Levels
>
> Most markdown syntaxes work inside block quotes.
>
> * Lists
> * [Links][arbitrary_id]
> * Etc.
```
    
### Inline Code
`Inline code` is indicated by surrounding it with backticks:  
`` `Inline code` ``

If your ``code has `backticks` `` that need to be displayed, you can use double backticks:  
```` ``Code with `backticks` `` ````  (mind the spaces preceding the final set of backticks)

### Block Code
If you indent at least four spaces or one tab, I'll display a code block.

    print('This is a code block')
    print('The block must be preceded by a blank line')
    print('Then indent at least 4 spaces or 1 tab')
	print('Nesting does nothing. Your code is displayed Literally')

I also know how to do something called [Fenced Code Blocks](#fenced-code-block) which I will tell you about later.

### Horizontal Rules
If you type three asterisks `***` or three dashes `---` on a line, I'll display a horizontal rule:

***

### Document Formatting
The ***Smartypants*** extension automatically transforms straight quotes (`"` and `'`) in your text into typographer’s quotes (`“`, `”`, `‘`, and `’`) according to the context. Very useful if you’re a typography freak like I am. Quote and Smartypants are syntactically incompatible. If both are enabled, Quote takes precedence.


### Block Formatting

#### Table

This is a table:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

You can align cell contents with syntax like this:

| Left Aligned  | Center Aligned  | Right Aligned |
|:------------- |:---------------:| -------------:|
| col 3 is      | some wordy text |         $1600 |
| col 2 is      | centered        |           $12 |
| zebra stripes | are neat        |            $1 |

The left- and right-most pipes (`|`) are only aesthetic, and can be omitted. The spaces don’t matter, either. Alignment depends solely on `:` marks.

#### <a name="fenced-code-block">Fenced Code Block</a>

This is a fenced code block:

```
print('Hello world!')
```

You can also use waves (`~`) instead of back ticks (`` ` ``):

~~~
print('Hello world!')
~~~

### Inline Formatting

The following is a list of optional inline markups supported:

Option name         | Markup           | Result if enabled     |
--------------------|------------------|-----------------------|
Intra-word emphasis | So A\*maz\*ing   | So A<em>maz</em>ing   |
Strikethrough       | \~~Much wow\~~   | <del>Much wow</del>   |
Underline [^under]  | \_So doge\_      | <u>So doge</u>        |
Quote [^quote]      | \"Such editor\"  | <q>Such editor</q>    |
Highlight           | \==So good\==    | <mark>So good</mark>  |
Superscript         | hoge\^(fuga)     | hoge<sup>fuga</sup>   |
Autolink            | http://t.co      | <http://t.co>         |
Footnotes           | [\^4] and [\^4]: | [^4] and footnote 4   |

[^4]: You don't have to use a number. Arbitrary things like `[^footy note4]` and `[^footy note4]:` will also work. But they will *render* as numbered footnotes. Also, no need to keep your footnotes in order, I will sort out the order for you so they appear in the same order they were referenced in the text body. You can even keep some footnotes near where you referenced them, and collect others at the bottom of the file in the traditional place for footnotes. 

## Hack On

That’s about it. Thanks for listening. I’ll be quiet from now on (unless there’s an update about the app—I’ll remind you for that!).

Happy writing!

[^emphasize]: If **Underlines** is turned on, `_this notation_` will render as underlined instead of emphasized 

[^under]: If **Underline** is disabled `_this_` will be rendered as *emphasized* instead of being underlined.

[^quote]: **Quote** replaces literal `"` characters with html `<q>` tags. **Quote** and **Smartypants** are syntactically incompatible. If both are enabled, **Quote** takes precedence. Note that **Quote** is different from *blockquote*, which is part of standard Markdown.

[^math]: Internet connection required.