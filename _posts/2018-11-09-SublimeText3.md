---
layout:   post
title:    Sublime Text 3
author:   flex
comments: true
category: How to guides, tips and tricks / útmutatók, tippek és trükkök
tags:     [sublime text, how to]
---

# Sublime Text billentyű parancsok [macOS]

`Cmd` + k, `Cmd` + b

Goto Anything

`Cmd` + p

Goto line in file

`Ctrl` + g

Go to the start or end of a line
Go to end of a line: `Cmd` + ➡
Go to the start of a line: `Cmd` + ←

Go to start or end of a file
Go to the start of a file: `Cmd` + ⬆
Go to the end of a file: `Cmd` + ⬇

Go one word left or right
Go one word left: `Alt` + ←
Go one word right: `Alt` + ➡

Go up or down a line
Go up a line: ⬆
Go down a line: ⬇

Cut/Copy/Paste/Undo/Redo

Cut: `Cmd` + x
Copy: `Cmd` + c
Paste: `Cmd` + v
Undo: `Cmd` + z
Soft undo: `Cmd` + u
Redo: `Cmd` + y

Using Carets / Multiple Cursors

Adding multiple Caret s

You can start playing with carets by opening any supported file in Sources, then selecting each line by holding down `Cmd`/`Alt` and clicking wherever you would like to add a new caret.

The following steps will quickly get every line selected:

1. Click on the first line
2. While holding down `⌘` and `Option`
3. Drag your mouse through the rest of the lines

Use multiple carets from the front of a line

Use `Cmd` + ← ( `Alt` + ← for Windows/Linux) to bring all cursors to the front of the line, and then hold down `Option` while using the arrow keys to jump by word. When in front of the file name, simply type in your prefix and you’re done!

Wrap with Quotes or Brackets

Highlight the words with `Cmd` + `Shift` + `←` ( `Ctrl` + `Shift` + `←` for Windows/Linux) and type an opening quote or bracket. Dev tools will wrap each word in the selected quote or bracket.

Column selection

Carets can similarly be used for selecting custom columns of text. Hold down `Alt` and then click and drag over the region of text you would like to select. DevTools will highlight the area and you can now copy or edit it as needed.

Carets and matching words

Carets can also be used for highlighting specific words. Select a word in your editor (it can be a variable, method, or anything really). DevTools will highlight other instances of this word with a border around them.

Now use `Cmd` + `D` (or `Alt` + `D`) and DevTools will highlight and place multiple cursors on the matching words. This is particularly useful during batch rename operations. Hitting D a few more time while still holding ⌘ selects the next instance of the selection found. By hitting ⌘, then D three times, you can select three iterations of the text.

Jump to matching brackets

When working with non-complex pieces of code, you might find it tricky to find corresponding opening and closing brackets with your naked eye. `Ctrl` + `M` allows you to instantly move your cursor there. Using it twice will jump to its opening or closing counterpart.

Indentation

We know the importance of indentation. It helps keep our code readable and easy to understand. To increase or decrease the current line’s indent, use the shortcuts below:

Indent text: `Tab`
Unindent text: `Shift` + `Tab`

Quickly comment your code

If you need to comment/uncomment a piece of code, the same shortcuts you would use for this in Sublime Text also apply:

Comment text: `Cmd`/`Ctrl` + `/`
Uncomment text: `Cmd`/`Ctrl` + `/` on the same section of text.

Toggle Autocompletion

When typing values in the DevTools Sources panel, you’re presented with autocompletions as you type. If however you dismiss these and would like to manually toggle autocompletion, you can do so with:

`Ctrl` + `Space`