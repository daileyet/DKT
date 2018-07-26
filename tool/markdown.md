# Markdown

## Overview

**Markdown** is created by [Daring Fireball](http://daringfireball.net/), the original guideline is [here](http://daringfireball.net/projects/markdown/syntax). Its syntax, however, varies between different parsers or editors. You also can refer to [GitHub Flavored Markdown](https://github.com/daileyet/DKT/tree/184b520353d3beaef05dc9cd6497af095799aca5/tool/GFM/README.md)

Please note that HTML fragments in markdown source will be recognized but not parsed or rendered. Also, there may be small reformatting on the original markdown source code after saving.

## Block Elements

### Paragraph and line breaks

A paragraph is simply one or more consecutive lines of text. In markdown source code, paragraphs are separated by more than one blank lines.

Press `Shift` + `Return` to create a single line break. However, most markdown parser will ignore single line break, to make other markdown parsers recognize your line break, you can leave two whitespace at the end of the line, or insert `<br/>`.

### Headers

Headers use 1-6 hash characters at the start of the line, corresponding to header levels 1-6. For example:

```text
# This is an H1

## This is an H2

###### This is an H6
```

### Blockquotes

Markdown uses email-style &gt; characters for block quoting. They are presented as:

```text
> This is a blockquote with two paragraphs. This is first paragraph.
>
> This is second pragraph.Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.



> This is another blockquote with one paragraph. There is three empty line to seperate two blockquote.
```

### Lists

Input `* list item 1` will create an un-ordered list, the `*` symbol can be replace with `+` or `-`.

Input `1. list item 1` will create an ordered list, their markdown source code is like:

```text
## un-ordered list
*   Red
*   Green
*   Blue

## ordered list
1.  Red
2.     Green
3.    Blue
```

### Task List

Task lists are lists with items marked as either \[ \] or \[x\] \(incomplete or complete\). For example:

```text
- [ ] a task list item
- [ ] list syntax required
- [ ] normal **formatting**, @mentions, #1234 refs
- [ ] incomplete
- [x] completed
```

You can change the complete/incomplete state by click the checkbox before the item.

### Code Blocks

Using fences is easy: Input \`\`\` and press `return`. Add an optional language identifier after \`\`\` and we'll run it through syntax highlighting:

```text
Here's an example:

​
```

function test\(\) { console.log\("notice the blank line before this function?"\); } ​\`\`\`

syntax highlighting: ​`ruby require 'redcarpet' markdown = Redcarpet.new("Hello World!") puts markdown.to_html ​`

```text
### Tables

Input `| First Header  | Second Header |` and press `return` key will create a table with two column.

In markdown source code, they look like:

``` markdown
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

You can also include inline Markdown such as links, bold, italics, or strikethrough.

Finally, by including colons : within the header row, you can define text to be left-aligned, right-aligned, or center-aligned:

```text
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

A colon on the left-most side indicates a left-aligned column; a colon on the right-most side indicates a right-aligned column; a colon on both sides indicates a center-aligned column.

### Horizontal Rules

Input `***` or `---` on a blank line and press `return` will draw a horizontal line.

## Span Elements

Span elements will be parsed and rendered right after your typing. Moving cursor in middle of those span elements will expand those elements into markdown source. Following will explain the syntax of those span element.

### Links

Markdown supports two style of links: inline and reference.

In both styles, the link text is delimited by \[square brackets\].

To create an inline link, use a set of regular parentheses immediately after the link text’s closing square bracket. Inside the parentheses, put the URL where you want the link to point, along with an optional title for the link, surrounded in quotes. For example:

```text
This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.
```

will produce:

This is \[an example\]\(\[[http://example.com/"Title\]\(http://example.com/"Title\)"\](http://example.com/"Title]%28http://example.com/"Title%29"\)\) inline link. \(`<p>This is <a href="http://example.com/" title="Title">`\)

[This link](http://example.net/) has no title attribute. \(`<p><a href="http://example.net/">This link</a> has no`\)

#### Internal Links

**You can set the href to headers**, which will create a bookmark that allow you to jump to that section after clicking. For example:

Command\(on Windows: Ctrl\) + Click [This link](markdown.md#block-elements) will jump to header `Block Elements`. To see how to write that, please move cursor or click that link with `⌘` key pressed to expand the element into markdown source.

#### Reference Links

Reference-style links use a second set of square brackets, inside which you place a label of your choosing to identify the link:

```text
This is [an example][id] reference-style link.

Then, anywhere in the document, you define your link label like this, on a line by itself:
```

In typora, they will be rendered like:

This is [an example](http://example.com/) reference-style link.

The implicit link name shortcut allows you to omit the name of the link, in which case the link text itself is used as the name. Just use an empty set of square brackets — e.g., to link the word “Google” to the google.com web site, you could simply write:

```text
[Google][]
And then define the link:
```

### Images

Image looks similar with links, but it requires an additional `!` char before the start of link. Image syntax looks like this:

```text
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
```

### Emphasis

Markdown treats asterisks \(`*`\) and underscores \(`_`\) as indicators of emphasis. Text wrapped with one `*` or `_` will be wrapped with an HTML `<em>` tag. E.g:

```text
*single asterisks*

_single underscores_
```

output:

_single asterisks_

_single underscores_

GFM will ignores underscores in words, which is commonly used in code and names, like this:

> wow\_great\_stuff
>
> do\_this\_and\_do\_that\_and\_another\_thing.

To produce a literal asterisk or underscore at a position where it would otherwise be used as an emphasis delimiter, you can backslash escape it:

```text
\*this text is surrounded by literal asterisks\*
```

### Strong

double \*’s or \_’s will be wrapped with an HTML `<strong>` tag, e.g:

```text
**double asterisks**

__double underscores__
```

output:

**double asterisks**

**double underscores**

Typora recommends to use `**` symbol.

### Code

To indicate a span of code, wrap it with backtick quotes \(\`\). Unlike a pre-formatted code block, a code span indicates code within a normal paragraph. For example:

```text
Use the `printf()` function.
```

will produce:

Use the `printf()` function.

### Strikethrough

GFM adds syntax to create strikethrough text, which is missing from standard Markdown.

`~~Mistaken text.~~` becomes ~~Mistaken text.~~

### Underline

Underline is powered by raw HTML.

`<u>Underline</u>` becomes Underline.

\[GFM\]: [https://help.github.com/articles/github-flavored-markdown/](https://help.github.com/articles/github-flavored-markdown/)

