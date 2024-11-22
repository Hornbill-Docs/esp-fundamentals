# Hornbill Wiki Markup
For easy formatting of text in Hornbill, a subset of wiki markup can be used for decorating text with italics or bold, creating bulleted or numbered lists, and defining titles and subtitles. Wiki markup lets you quickly apply some basic formatting to your text as you type, giving it that extra touch to make it stand out.

## Section Headings
Using the equal sign (=) on either side of a word creates a section heading. The number of equal signs determines the size of the heading. Each heading is followed by a line break.

```
=Heading 1=
==Heading 2==
===Heading 3===
```

## Lists
There are three types of lists - [Bulleted](#bulleted-list), [Numbered](#numbered-list) and [Indented](#indented-list).

### Bulleted List
Start each line with an asterisk (*). Chaining multiple asterisks (*) will indent the list level even further.
```
* Start each line with an asterisk (*).
** More asterisks give deeper
*** and deeper levels.
* Line breaks <br />don't break levels.
*** But jumping levels creates empty space.
* Blank lines ends the list

Any other start ends the list.
```
#### Example
<pre>
• Start each line with an aserisk (*).
  • More asterisks give deeper
    • and deeper levels.
• Line breaks 
  don't break levels

• Blank lines end the list

Any other start ends the list
</pre>

### Numbered List
Start each line with a [number sign](http://en.wikipedia.org/wiki/Number_sign) (#). Chaining multiple number signs (#) will indent the list level even further.
```
# Start each line with a number sign (#).
## More number signs give deeper
### and deeper levels.
# Line breaks <br />don't break levels.
### But jumping levels creates empty space.
# Blank lines ends the list

Any other start also ends the list.
```
#### Example
<pre>
1. Start each line with a number sign (#).
   1. More number signs give deeper
      1. and deeper levels.
2. Line breaks 
  don't break levels.

3. Blank lines ends the list

Any other start also ends the list.
</pre>

### Indented List
This type of list is used for indenting only, and doesn't prefix the lines with any visible characters. Start each line with a colon sign (:). Chaining multiple colon signs (:) will indent the list level even further.
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

## Text Formatting
Single quotation marks ( ' ) are used to format text as either bold or italic. Typing two single quotation marks either side of some text will italicize the text. Typing three single quotation marks either side of some text will bold the text.

| Markup        | Displayed As       |
|---------------|:---------------------------------------------|
| ```''italics''``` |	<i>italics</i> |
| ```'''bold'''``` |	<b>bold</b> |
| ```<del>strike through</del>``` | <del>strike through</del> |
| ```<ins>underline</ins>``` | <ins>underline</ins> |
| ```<span style="color:red;font-size:16px;font-family:monospace">font formatting such as color and font type</span>``` |	<span style="color:red;font-size:16px;font-family:monospace">font formatting such as color and font type</span> |

## Links
Hyperlinks to other areas of Hornbill can be added. This includes the ability to provide some friendly text along with the link. These links are internal to your instance of Hornbill. The URL link will always be prefixed with https://live.hornbill.com/<your instance>/

| Markup        | Displayed As       |
|---------------|:---------------------------------------------|
| ```[[newsfeed]]``` | newsfeed |
| ```[[newsfeed\|Link to your Newsfeed]]``` |	Link to your Newsfeed |

The same concept will be available for external links using absolute URLs

| Markup        | Displayed As       |
|---------------|----------------------------------------------|
| ```[[http://community.hornbill.com]]``` | [http://community.hornbill.com](http://community.hornbill.com/) |
| ```[[Hornbill Community Forums\|http://community.hornbill.com]]``` |	[Hornbill Community Forums](http://community.hornbill.com) |

## Date Formatting
You can wrap a Date & Time value (e.g. 21-02-2020 16:10:30) with square brackets to apply the configured preferences in your Profile's Regional Settings.

For example, if the "Date Time Format" option in my Profile's Regional Settings is set to "21/02/2020 16:10", the syntax [01-01-1970 01:00:00] would result in 01/01/1970 01:00.

Another common use is using the Variable Picker in the Business Process Engine to post to a Timeline or Workspace. You can wrap the generated value (by the Variable Picker) with square brackets. For example, &[functions.pcf("askAQuestion","selectStartDate")] becomes [&[functions.pcf("askAQuestion","selectStartDate")]].

## Images
Images can be added to any text field that allows wiki markup other than Posts or Comments as they have their own mechanism for managing images.

### Syntax
```txt
[[File:filename.extension|options|caption]]

```

__Legacy Image:__
Namespace prefix is still supported as a synonym as well as Media.

### Examples

* This markup: `[[File:https://docs.hornbill.com/images/help_icon.png]]`
* Would be displayed as:
<p align="left">
    <img src="https://docs.hornbill.com/images/help_icon.png" width="50">
</p>

* This markup: `[[File:https://docs.hornbill.com/images/help_icon.png|center|caption]]` 
* Would be displayed as:
<p align="center">
    <img src="https://docs.hornbill.com/images/help_icon.png" title="caption" width="50">
</p>

* This markup: `[[File:https://docs.hornbill.com/images/help_icon.png|right|caption]]`
* Would be displayed as:
<p align="right">
    <img src="https://docs.hornbill.com/images/help_icon.png" title="caption" width="50">
</p>

## Images with Link:
Images can also be linked to a URL.

The syntax is: 

```
[[File:https://www.hornbill.com/images/logo.png|link=http://www.hornbill.com|alt=Hornbill Logo]]
```

## Symbols
| Markup        | Displayed As       |
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

## Code Snippets
A language can be passed as an option after a colon [code:SOURCE-LANGUAGE] 

These are the available languages: "bsh", "c", "cc", "cpp", "cs", "csh", "cyc", "cv", "htm", "html", "java", "js", "m", "mxml", "perl", "pl", "pm", "py", "rb", "sh", "xhtml", "xml", "xsl", "sql"

| Markup        | Displayed As       |
|---------------|:---------------------------------------------|
| [code]<br>var a = 1<br>[/code] | ```var a = 1``` |
| [code:sql]<br>SELECT *<br>FROM TABLE<br>[/code] | <pre>SELECT *<br />FROM TABLE</pre> |

## Blockquote

<pre>[blockquote]
some text
[/blockquote]</pre>

__Example__
<blockquote>
some text
</blockquote>

__More properties:__  
__actor__ - The name of the person  
__date__ - Can be a custom format or ISO date format. In the case of ISO format it will be converted to the user's local time and format based on his settings.

<pre>[blockquote|actor:Daniel|date:2015-03-06T16:46:08Z]
some text
[/blockquote]</pre>

__Example__
<blockquote>
  <p>some text</p>
  <footer>-- Daniel - 06/03/2015 4:46pm</footer>
</blockquote>

__Note:__ It is possible also to use [quote] as an alias to [blockquote]

## Horizontal Rule
| Markup        | Displayed As       |
|---------------|:---------------------------------------------|
| ```----``` | <hr style="margin: 0; margin-bottom: 10px; border: none; border-top: 1px solid #000;"> |

## Nowiki
| Markup        | Displayed As       |
|---------------|:---------------------------------------------|
| `[nowiki]<br />This is '''bold''' and this is ''italic''<br />[/nowiki]` | This is '''bold''' and this is '''italic''' |
