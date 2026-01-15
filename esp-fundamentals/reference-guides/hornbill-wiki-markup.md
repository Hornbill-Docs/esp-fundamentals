# Hornbill Wiki Markup
For easy formatting of text in Hornbill, you can use a subset of wiki markup to add italics or bold, to create bulleted or numbered lists, and to change text size for titles and other headings. With wiki markup, you can quickly apply basic formatting to your text as you type, giving it that extra touch to make it stand out.

## Topics covered
* [Section headings](/esp-fundamentals/reference-guides/hornbill-wiki-markup#section-headings)
* [Lists](/esp-fundamentals/reference-guides/hornbill-wiki-markup#lists)
* [Text formatting](/esp-fundamentals/reference-guides/hornbill-wiki-markup#text-formatting)
* [Links](/esp-fundamentals/reference-guides/hornbill-wiki-markup#links)
* [Date formatting](/esp-fundamentals/reference-guides/hornbill-wiki-markup#date-formatting)
* [Images](/esp-fundamentals/reference-guides/hornbill-wiki-markup#images)
* [Emoticons](/esp-fundamentals/reference-guides/hornbill-wiki-markup#emoticons)
* [Code snippets](/esp-fundamentals/reference-guides/hornbill-wiki-markup#code-snippets)
* [quote](/esp-fundamentals/reference-guides/hornbill-wiki-markup#quote)
* [Blockquote](/esp-fundamentals/reference-guides/hornbill-wiki-markup#blockquote)
* [Horizontal rule](/esp-fundamentals/reference-guides/hornbill-wiki-markup#horizontal-rule)
* [Nowiki](/esp-fundamentals/reference-guides/hornbill-wiki-markup#nowiki)

## Section headings
Using the equal sign (=) on either side of a word creates a section heading. The number of equal signs determines the size of the heading. Each heading is followed by a line break.

```
=Heading 1=
==Heading 2==
===Heading 3===
```

## Lists
There are three types of lists: [bulleted](#bulleted-list), [numbered](#numbered-list), and [indented](#indented-list).

### Bulleted list
Start each line with an asterisk (\*). Chaining multiple asterisks indents the list level further.
```
* Start each line with an asterisk (*).
** More asterisks give deeper
*** and deeper levels.
* Line breaks <br />don't break levels.
*** But jumping levels creates empty space.
* Blank lines ends the list.

Any other start ends the list.
```
#### Example
<pre>
• Start each line with an asterisk (*).
  • More asterisks give deeper
    • and deeper levels.
• Line breaks 
  don't break levels.

• Blank lines end the list.

Any other start ends the list.
</pre>

### Numbered list
Start each line with a [number sign](http://en.wikipedia.org/wiki/Number_sign) (#). Chaining multiple number signs (#)  indents the list level further.
```
# Start each line with a number sign (#).
## More number signs give deeper
### and deeper levels.
# Line breaks <br />don't break levels.
### But jumping levels creates empty space.
# Blank lines end the list.

Any other start also ends the list.
```
#### Example
<pre>
1. Start each line with a number sign (#).
   1. More number signs give deeper
      1. and deeper levels.
2. Line breaks 
  don't break levels.

3. Blank lines end the list.

Any other start also ends the list.
</pre>

### Indented list
This type of list is used for indenting only, and doesn't prefix the lines with any visible characters. Start each line with a colon sign (:). Chaining multiple colon signs (:) indents the list level further.
```
No indent
: Single indent
:: Double indent
::: Triple indent
```
#### Example
<pre>
No Indent 
  Single indent  
    Double indent
      Triple indent  
</pre>

### Mixture of different types of list
```
# one
# two
#* two point one
#* two point two
# three
#: three def one
# four
#: four def one
#: this looks like a continuation
# five
## five sub 1
### five sub 1 sub 1
## five sub 2
```
#### Example
<pre>
1. one
2. two
   • two point one
   • two point two
3. three
   three def one
4. four
   four def one
   this looks like a continuation
5. five
   1. five sub 1
      1. five sub 1 sub 1
   2. five sub 2
</pre>

## Text formatting

### Bold and italic
With wiki markup, use quotation marks on either side of text as follows:
* Use two single quotation marks to italicize the text.
* Use three single quotation marks to make the text bold.

### Strike-through, underline, and font color/type
You can also use strike-through and underline formatting, as well as change the color and font type.  

To define color, use the `<span style="">` tag. Inside the style tag, you can define a specific color (#555 for gray), a named color (gray), or a Hornbill color variable (var(--hb-primary)).  
The Hornbill color variable is more flexible and will change depending on the theme you currently have (light, dark, high contrast). These colors also have a meaning, so `hb-primary` indicates importance.  
Note that the Hornbill color variables can change in the future in case of an overall style update.  

The list of Hornbill color variables you can use is the following:
* --hb-primary
* --hb-secondary
* --hb-warning
* --hb-info
* --hb-danger
* --hb-success

### Examples
| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| `''italics''` |	<i>italics</i> |
| `'''bold'''` |	<b>bold</b> |
| `<del>strike through</del>` | <del>strike through</del> |
| `<ins>underline</ins>` | <ins>underline</ins> |
| `<span style="color:red;font-size:12px;font-family:monospace">font formatting such as color and font type</span>` |	<span style="color:red;font-size:12px;font-family:monospace">font formatting such as color and font type</span> |
| `<span style="color:var(--hb-primary)">using Hornbill Color Variables</span>` |	<span style="color:red;font-size:12px;font-family:monospace">using Hornbill color variables</span> |

## Links
You can add hyperlinks to other areas of Hornbill, referenced with text. These links are internal to your instance of Hornbill. The URL link will always be prefixed with https://live.hornbill.com/<`your instance`>/

| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| `[[newsfeed]]` | <span style="color:blue">newsfeed</span>|
| `[[newsfeed\|Link to your Newsfeed]]` |	 <span style="color:blue">Link to your Newsfeed</span>|

Add external links using absolute URLs.

| Markup        | Displayed as       |
|---------------|----------------------------------------------|
| `[[https://community.hornbill.com]]` | [https://community.hornbill.com](https://community.hornbill.com/) |
| `[[https://community.hornbill.com\|Hornbill Community Forums]]` |	[Hornbill Community Forums](https://community.hornbill.com) |

## Date formatting
You can wrap a date/time value (e.g. 21-02-2020 16:10:30) with square brackets to apply the preferences that are configured in your profile's regional settings.

For example, if the *Date Time Format* option in your profile's regional settings is set to "21/02/2020 16:10", the syntax [01-01-1970 01:00:00] would result in 01/01/1970 01:00.

Another common use is using the variable picker in workflows to post to a timeline or workspace. You can wrap the value generated by the variable picker with square brackets. For example, &[functions.pcf("askAQuestion","selectStartDate")] becomes [&[functions.pcf("askAQuestion","selectStartDate")]].

## Images
You can add images to any text field that allows wiki markup. The exception to this is posts and comments, because they have their own mechanism for managing images.

The syntax is the following:
```txt
[[File:filename.extension|options|caption]]

```
Both the legacy `Image:namespace` and `Media:namespace`  prefixes are supported as a synonym for the `File:namespace` prefix.

### Examples

* This markup: `[[File:https://www.hornbill.com/images/logo.png]]`

    would be displayed as:
    <p align="left">
    <img src="https://www.hornbill.com/images/logo.png" width="200">
</p>

* This markup: `[[File:https://www.hornbill.com/images/logo.png|center|caption]]`

    would be displayed as:
    <p align="center">
    <img src="https://www.hornbill.com/images/logo.png" title="caption" width="200">
</p>

* This markup: `[[File:https://www.hornbill.com/images/logo.png|right|caption]]`
    would be displayed as:
    <p align="right">
    <img src="https://www.hornbill.com/images/logo.png" title="caption" width="200">
</p>

### Images with links
Images can also be linked to a URL.

The syntax is: 

```
[[File:https://www.hornbill.com/images/logo.png|link=http://www.hornbill.com|alt=Hornbill Logo]]
```

## Emoticons
You can use the following keyboard characters to display emoticons.
| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| :-)	| 😀 |
| :)	| 😀 |
| :D	| 😆 |
| :-(	| 😞 |
| :(	| 😞 |
| ;)	| 😉 |
| ;-)	| 😉 |
| :-o	| 😮 |
| :o	| 😮 |
| :O	| 😮 |
| :P	| 😛 |
| :p	| 😛 |
| :-bd	| 👍 |
| (y)	| 👍 |
| (yes)	| 👍 |
| (ok)	| 👍 |
| (n)	| 👎 |
| (no)	| 👎 |
| X(	| 😠 |
| ~O)	| ☕ |
| :-S	| 😕 |
| :/	| 😕 |
| :-/	| 😕 |
| 8-)	| 😎 |
| (cwl)	| 😂 |
| :\'(	| 😢 |
| :\|	| 😐 |
| :\$	| ☺ |
| :-\$	| ☺ |
| \|)	| 😴 |
| \|-)	| 😴 |
| (zip)	| 🤐 |

## Code snippets
You can include snippets formatted as generic code, or snippets of a specific programming language, using brackets and a colon as in the examples that follow.

The available languages are: "bsh", "c", "cc", "cpp", "cs", "csh", "cyc", "cv", "htm", "html", "java", "js", "m", "mxml", "perl", "pl", "pm", "py", "rb", "sh", "xhtml", "xml", "xsl", and "sql".

| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| [code]<br>var a = 1<br>[/code] | ```var a = 1``` |
| [code:sql]<br>SELECT *<br>FROM TABLE<br>[/code] | <pre>SELECT *<br />FROM TABLE</pre> |


## Quote
Add a Quote using the following syntax:

<pre>[quote]
some text
[/quote]</pre>

__Example__
<quote>
some text to quote
</quote>


## Blockquote
Add a blockquote using the following syntax:

<pre>[blockquote]
some text
[/blockquote]</pre>

__Example__
<blockquote>
some text
</blockquote>

### Additional properties for blockquotes
Add further properties to the blockquote using the following:

* **actor.** The name of the person quoted.  
* **date.** This can be a custom format or ISO date format. In the case of ISO format, it will be converted to the local time and format specified in the user's settings.

    <pre>[blockquote|actor:Daniel|date:2015-03-06T16:46:08Z]
    some text
    [/blockquote]</pre>

__Example__
<blockquote>
  <p>some text</p>
  <footer>-- Daniel - 06/03/2015 4:46pm</footer>
</blockquote>

__Note:__ As an alternative, you can use `quote` as an alias to `blockquote`.

## Horizontal rule
To add a line, use the syntax for a horizontal rule as in the following example:

| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| ```----``` | <hr style="margin: 0; margin-bottom: 10px; border: none; border-top: 1px solid #000;"> |

## Nowiki
If you want to prevent wiki markup from being parsed and executed along with all the other wiki text on a page, use `nowiki` as in the following example:
| Markup        | Displayed as       |
|---------------|:---------------------------------------------|
| `[nowiki]<br />This is '''bold''' and this is ''italic''<br />[/nowiki]` | This is '''bold''' and this is '''italic''' |
