# ExpressLogic Expressions
Hornbill ExpressLogic as a generalized expression language for matching data, this language is used in various parts of the Hornbill platform where there is a requirement to allow user configuration of data matching. Use includes areas such as email routing rules, 

Data matching and querying are central to the efficient management and utilization of data and workflows, especially in complex, data-rich environments that Hornbill is designed for. The ability to quickly and efficiently query and analyze data at scale with high throughput is crucial for system performance, especially when large transactional volume and scale is required. Hornbill ExpressLogic is a custom developed expression evaluation engine designed to work with in-memory datasets, removing the need to use more typical complex processing and expression evaluating systems such as full blown languages and even database servers.  

Hornbill ExpressLogic is data matching query language specifically developed by Hornbill to facilitate customer-definable logical decisions, often used to handle things like triggers, actions, rules and other decision-driven rules processing. The ExpressionLogic syntax is heavily influenced by SQL’s intuitive syntax, ExpressLogic expressions are written in a familiar syntax, very similar to what you would find on the right-hand side of a WHERE clause in general SQL languages, offering simplicity, familiarity and supporting simple to very complex queries.

Here’s some of the goals that drive the development of the ExpressLogic language:

* __Precision and Performance:__
    Hornbill ExpressLogic is written in modern, native C++, ensuring a clean and efficient implementation that is highly optimized for workloads with unusually high throughput and lock-free concurrent operation. 

* __Robust and Reliable:__
    Hornbill ExpressLogic is built with a priority on performance and reliability. 
   
* __Designed to be Familiar:__
    The query language syntax is inspired by the ubiquitous Structured Query Language (SQL), makes it a familiar and intuitive tool for data professionals to use and understand

* __Advanced Error Handling:__
    Errors and exceptions are handled gracefully, offering friendly guidance at design time to help users validate, diagnose and resolve issues. Hornbill ExpressLogic is designed to be robust, with internal safeguards ensuring that your data querying and matching operations proceed without a hitch. The system design favors service reliability over absolute syntax correctness. 

* __Rich and Expressive:__
    With support for a rich set of operators and numerous useful functions, Hornbill ExpressLogic caters to the widest possible data querying and evaluation needs. Whether you’re evaluating numbers, strings, or even null values, or employing complex logical constructs, ExpressLogic has the capability to enable precise, efficient queries, from the most simple to the most complex.

## Supported Syntax/Grammar
The ExpressLogic language is a declarative syntax designed for the sole purpose of querying data to find a logical match against a set of logical rules, those rules are expressed in the syntax that ExpressLogic processor understands. 

## ExpressLogic Data Types
The ExpressLogic processing engine only understands Strings, Integers, Real Numbers and Null values. 

|Type|Description|
|:--|:--|
|Null|A null (non) value|
|String|Any unicode string value|
|Number|Represents an integer or a real number|

## ExpressLogic String Literals
String literals are represented as a quoted string.  Either single quotes as used in SQL and JavaScript or double quotes as used in JavaScript, both forms are supported.  In the case of single-quoted string, the escape character should be either two successive single-quote characters (as per classical SQL syntax) or a backslash and a single quote as often found in JavaScript and other similar languages.   In the case of a double-quoted string, the escape sequence is either two successive double-quote characters, or, a backslash and a double-quote. Many SQL implementations support both of these forms, so for convenience ExpressLogic does also.

|Expression|Literal Value|
|:--|:--|
|`‘Gerry’’s’`|Gerry’s|
|`‘Gerry\’s’`|Gerry’s|
|`“Gerry””s”`|Gerry”s|
|`“Gerry\”s”`|Gerry”s|
|`‘Gerry’’’’s’`|Gerry’’s|
|`'Gerry\’\’s’`|Gerry’’s|
|`“Gerry’s”`|Gerry’s|
|`‘Gerry”s’`|Gerry”s|
|`“Gerry\\\\s”`|Gerry\s|
|`“.*\b[0-9]{5,8}\b.*”`|.*\b[0-9]{5,8}\b.*|


## ExpressLogic Number Literals
Number literals should support the decimal format, no scientific notation is required. For integer numbers, simple base10 numerals like 123 or 17 etc… for real numbers, the decimal form like 10.2 or 9.00356 should be used. 

## ExpressLogic Null Literal Value
The NULL value should be expressed as NULL and I case-insensitive so (Null, NULL, null etc are all valid),  as it is in SQL statements.  NULL values will support the = (==) and != operators for comparison.  NULL is only ever equal to the literal NULL or a variable (identifier) that contains a NULL value.  A NULL value is one that is present but has not been assigned any value. In the case of a String value, NULL and empty string do not equate to the same thing.

## ExpressLogic Logical Connectives
|Operator|Operator Priority|Description|
|:--|:--|:--|
|`AND` (or && or ‘and’ or ‘And’)|1|Logical AND connective|
|`OR` (or \|\| or ‘or’ or ‘Or’)|2|Logical OR connective|

## ExpressLogic Logical Operators
|Operator&nbsp;&nbsp;&nbsp;|Description|
|:--|:--|
|`=`|Equality operator: checks of l-Value and r-Value are equal, irrespective of case. This is typical in SQL systems.<br><br>`(’Harry’ = ‘HARRY’) = true`<br><br>`(’HARRY’ == ‘HARRY’) = true`|
|`==`|Same behavior as the Single Equals Equality operator but in the case of a string, this will be a case-sensitive comparison<br><br>`(’Harry’ == ‘HARRY’) = false`<br><br>`(’HARRY’ == ‘HARRY’) = true`|
|`<`|Less than operator|
|`>`|Greater than operator|
|`<=`|Less than or equal to operator|
|`>=`|Greater than or equal to operator|
|`<> (or !=)`|Not equal to operator|
|`()`|Operator precedence, nestable to any number of levels, follow normal rules found in SQL<br><br>`a = b OR (c = d AND (1 < 4 OR 2 > 5))`|
|`LIKE`|SQL-style LIKE operator in expressions.  An example would be: -<br><br>`a LIKE b`<br>`‘a’ LIKE ‘b’`<br><br>The like operation should support the SQL style % prefix and postfix wildcard, so ‘a%’ starts with,  or ‘%a’ ends with. Matches should be case-insensitive|
|`IN`|SQL-style IN operator, for example<br><br>`‘a’ IN (‘b’, ‘c’, ‘d’)`<br><br>The IN operation should do checks in an case-insensitive form.|
|`NOT`|SQL-style NOT operator in expressions.  Examples would be <br><br>`a NOT LIKE b`<br>`NOT 1`<br>`1 NOT IN (1,2,3)`<br><br>The NOT operator will invert the logical result of the expression to its right. 

## ExpressLogic Data Types Comparison Behavior
When comparing two values, it’s likely that in some cases the user writing the expression might compare a string to a number.  Rather than fail in this case, what the expression evaluation will do is attempt to convert the string value to a number, but only if the string only contains characters that can be converted to a number, and then do a numeric comparison.  If the string contains characters that are not numerals, then the number value is converted to a string, and a string comparison is performed instead. The reasoning behind this behavior is to make the expressions as easy as possible to use.

## ExpressLogic Functions
Functions can take any number of arguments and will a single return value.  Arguments can be literal values, identifier (variable) values or the return value from another function.  For example:- 

```SQL
someFunction(myFunction(a), 99) == 4
```

This is the basic syntax one would typically expect to find in SQL or JavaScript type languages.

Function names are case sensitive meaning my_function and My_function would be treated as twe separate and unique functions.

Here are a list of basic functions supported by ExpressLogic.  Please be aware that this list of functions may be extended by specific areas through the system that make use of the ExpressLogic engine.  These functions are common to all areas where the ExpressLogic engine is used

|Functon|Desxription|
|:--|:--|
|LEFT|Return the leftmost number of characters specified. <br><br>For example: <br><br>`LEFT('The Dog', 3) = 'The'`|
|MID|Same as SUBSTRING()|
|SUBSTRING|Return a substring starting from the specified position.<br><br>`SUBSTRING(string, pos)`<br><br>`SUBSTRING (string, pos, length)`<br><br>For example:<br><br>`SUBSTRING('The Dog', 5) = 'Dog'`<br><br>`SUBSTRING('The Dog', 5, 2) = 'Do'`|
|RIGHT|Returns the rightmost ‘length’ characters from the ‘string’<br><br>`RIGHT(string, length)`<br><br>For example: -<br><br>`RIGHT('The Dog', 2) = 'og'`|
|TOKEN|Assumes that whitespace is a token separator, this function will return the token specified. The line and token_pos values are zero based, so to obtain the first word in the first line, line=0 and token=0<br><br>`TOKEN(string, line, token_pos)`<br><br>For example: -<br><br>`TOKEN('The big dog jumped', 0, 0) = 'The'`<br><br>`TOKEN('The big dog jumped', 0, 1) = 'big'`<br><br>`TOKEN('The big dog jumped', 0, 2) = 'dog'`<br><br>|
|CONCAT|Takes any number of arguments and concatenates them all together returning a string.<br><br>For example: -<br><br>`CONCAT(‘The’, ‘ ‘, 'Dog') = 'The Dog'`|
|REGEX_MATCH|Returns a true/false depending on the outcome of the regular expression match against the supplied string.<br><br>`REGEX_MATCH('String to match', 'regex to test')`<br><br>This function uses modified ECMAScript regular expression grammar. Please see the following site for more information: [https://en.cppreference.com/w/cpp/regex/ecmascript](https://en.cppreference.com/w/cpp/regex/ecmascript)<br><br>Example of a routing rule matching a request reference in the email subject:<br><br>`REGEX_MATCH(subject, '.*\b[a-zA-Z]{2}[0-9]{8}\b.*')`|
|REGEX_SUBSTR|Returns a substring of the provided ‘string’ based on the provided regular expression.<br><br>`REGEX_SUBSTR('string', 'regex')`<br><br>This function uses modified ECMAScript regular expression grammar. Please see the following site for more information: [https://en.cppreference.com/w/cpp/regex/ecmascript](https://en.cppreference.com/w/cpp/regex/ecmascript)|
|STRING_REPLACE|Replaces all occurrences of needle with haystack and returns the resultant string: <br><br>`STRING_REPLACE('needle', 'haystack', 'string')`|
|CONTAINS|Checks to see if a string contains another string: <br><br>`CONTAINS('needle', 'haystack')`|
|TIME|Returns an IS08601 formatted string representing either the current date time, or the date/time based on an EPOCH value.  <br><br>`TIME()` returns the current time</br><br>`TIME(12345678)` returns the ISO8601 formatted date time based on the supplied EPOCH time|
|EPOCH|The inverse of the TIME() function, will take the time in ISO8601 format and return an EPOCH time.  If no time specified, then returns the current time.   <br><br>`EPOCH()` returns the current time</br><br>`EPOCH('2020-04-05 12:22:33')` returns the EPOCH time based on the supplied ISO8601 formatted date time|
|BITCHECK|Returns true if the specified bit, in the bits number is set. <br><br>`BITCHECK(bits, bit_position)`<br><br>`BITCHECK(15, 1)` returns true|

## ExpressLogic Identifiers
Identifiers	always evaluate to a (named) value.  An identifier is functionally equivalent to a variable in a typical programming language.

Identifier should adhere to the following rules for allowable characters: - 

- Identifier (variable) names can range from 1 to 255 characters.
- All names must begin with a letter of the alphabet or an underscore (_).
- After the first initial letter, Identifier names can also contain letters and numbers or further underscores.  
- Identifier names are case sensitive.
- No spaces or special characters other than a period '.' are allowed in Identifier names.
- You cannot use any keyword (a reserved word in the expression syntax) as an Identifier name. 
- Added in v1.9 - identifiers can include names that include a dot-separated notation, for example a.b.c.d would be a valid identifier name.

## ExpressLogic Expressions
Using the above syntax, expressions will behave as you would expect expressions in behave in SQL.  An expression can be in two basic forms, the first is a three-component expression consisting of an lValue an operator and an rValue. The values can be either identifiers (variables) or literal string or number values

    lValue <logical-operator> rValue

The second form is a single value, like the following: -

    someValue

Expressions like `1 == 0` would evaluate to false. Expressions can be chained using logical connectives AND and OR.  Braces `( )` can be used to alter the natural order of precedence of the connected expressions. Expressions are typically evaluated in Left-to-Right order, and connectives prioritize `AND` over `OR` as is typical in SQL.

## ExpressLogic Function & Identifier Name Conflicts
A function is identified as a function because of open/close parentheses following the function name.  When processing an expression function names would take priority over literal names.  If any name conflicts to arise these will throw runtime or validation errors

