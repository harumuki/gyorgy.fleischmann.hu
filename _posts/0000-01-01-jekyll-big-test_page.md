---
layout: post
title: Jekyll test page 2
comments: false
category: Test / teszt
tags: [web, development, html, jekyll]
---

<!-- break -->

<div class="rightbox" style="width: 25%;">
<p style='margin:0px'></p>
<p>Ez pedig 1 jobb oldali text 
<br>
lesz asasasa asaasas

sddssdsdsds
</p></div>

ToDo:
 * GitHub teszt
 * lábléc doboz
 * fejléc linkek
 * dokumentum fejléc kategória és tag linkek
 * fótó browser
 * fotó grid
 * hivatkozások
 * mediaplayer (mp3, mp4, youtube, soundcloud)
 * bal/jobb text doboz
 * syntax highlight doboz
 * terminal doboz style
 * css tisztítás

<audio controls>
  <source src="mp3/horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>

<iframe width="100%" height="300" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/98992518&amp;color=%23ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true"></iframe>

<iframe class="shadow" width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/98992518&amp;color=%2300cc11&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true"></iframe>

## Mit tud a jelenlegi CSS:

 * Terminal

<pre class="terminal">WWWText <strong>skdslksd</strong>
iiiiii</pre>

* Fejlécek

# H1 

## H2

### H3

#### H4

##### H5

* Iniciáléval kezdődő bejegyzés

Lásd fentebb.

* YouTube videók beágyazása

<div class="videocontainer"><iframe src="https://www.youtube.com/embed/OLdWTOgIGF8" frameborder="0" allowfullscreen class="iframeshadow" width="1024" height="576"></iframe></div>

 * syntax highlight lehetőség

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
var s = "JavaScript syntax highlighting";
alert(s);
var s = "JavaScript syntax highlighting";
alert(s);
var s = "JavaScript syntax highlighting";
alert(s);
var s = "JavaScript syntax highlighting";
alert(s);
``` 
<hr>
 
 * listák készítése
 * Lists must be preceded by a blank line (or block element)

 - sddsd
 - dsdskdjsk
 
 * Unordered lists start each item with a `*`
 - `-` works too
    * Indent a level to make a nested list
	1. Ordered lists are supported.
	2. Start each item (number-period-space) like `1. `
	42. It doesn't matter what number you use, I will render them sequentially
	1. So you might want to start each line with `1.` and let me sort it out

 * táblázatok kezelése

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

 * idézetek

 > <p style='margin:0px'></p>Angle brackets `>` are used for block quotes.  
Technically not every line needs to start with a `>` as long as
there are no empty lines between paragraphs.  
> Looks kinda ugly though.
> > <p style='margin:0px'></p>Block quotes can be nested.  
> > > <p style='margin:0px'></p>Multiple Levels
>
> Most markdown syntaxes work inside block quotes.
>
> * Lists
> * [Links][arbitrary_id]
> * Etc.
> 

 * Hivatkozások kezelése

I bet you'd like more information about this sentence [^1].

[^1]: <p style='margin:0px'></p>Well lucky for you, I've included more information in footnote form.

## Inline Formatting

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

[^4]: <p style='margin:0px'></p>You don't have to use a number. Arbitrary things like `[^footy note4]` and `[^footy note4]:` will also work. But they will *render* as numbered footnotes. Also, no need to keep your footnotes in order, I will sort out the order for you so they appear in the same order they were referenced in the text body. You can even keep some footnotes near where you referenced them, and collect others at the bottom of the file in the traditional place for footnotes. 

## Hack On

That’s about it. Thanks for listening. I’ll be quiet from now on (unless there’s an update about the app—I’ll remind you for that!).

Happy writing!

egy teszt lista:

 - alma
 - körte

[^emphasize]: <p style='margin:0px'></p>If **Underlines** is turned on, `_this notation_` will render as underlined instead of emphasized 
[^under]: <p style='margin:0px'></p>If **Underline** is disabled `_this_` will be rendered as *emphasized* instead of being underlined.
[^quote]: <p style='margin:0px'></p>**Quote** replaces literal `"` characters with html `<q>` tags. **Quote** and **Smartypants** are syntactically incompatible. If both are enabled, **Quote** takes precedence. Note that **Quote** is different from *blockquote*, which is part of standard Markdown.
[^math]: Internet connection required.

asassa