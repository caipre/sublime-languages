Sublime-Languages
=================

The existing language files seemed overly complex, lacked readable comments and proper documentation,
and occasionally just didn't work. Worst of all, there was no clear maintainer, and updates were
non-existent. I'm hoping to change that by starting from scratch. Initially each syntax is bound to
have bugs and missing pieces, since I'm sure I only regularly use a small subset of each languages'
features. Over time, and with some community support, these will develop into language definitions
that are more comprehensible, effective, and complete.

In general, I will follow the naming conventions specified in the Textmate [language grammars][1]
documentation. This is sensible since it means existing themes will immediately support the new
language definitions. Unfortunately, the specification is vague and in some instances incomplete;
where necessary, I will use my best judgment. The goal is to be readable, complete, and flexible.
[1]: http://manual.macromates.com/en/language_grammars "Textmate language grammars"

__Available languages:__ Diff, Fountain, HDL, .hack, JSON, Perl, SQL

__Planned languages:__ HTML, XML, CSS, Javascript, Bash (Shellscript), Python, C

Installation
------------
Download the language file you want to use and place it in your Packages/User directory. The language will be available under *User -&gt; &lt;lang&gt;*

You may wish to overwrite the default language file, to avoid confusion resulting from identically named language definitions. Doing so also gives you access to any language-specific snippets kept in the `Packages/<lang>` folder. However, bear in mind that the custom files will be overwritten when updating Sublime.

Language Notes
--------------
### Diff
* Support for most features of default file

### HDL, .hack
* Basic keyword and comment support (ongoing)

### Fountain
* Complete support for syntax [as defined](http://fountain.io/syntax) on 2012-02-07.

### JSON
* Complete support for syntax [as defined](http://json.org)
* Support for most features of default file (ongoing)

### Perl
* Named scopes for all [special variables](http://perldoc.perl.org/perlvar.html) under `variable.other.special`
* Named scopes for many different [categories of functions](http://perldoc.perl.org/index-functions-by-cat.html) under `keyword.function`
* Named scopes for scalars, arrays, hashes under `variable.other.{scalar,array,hash}.perl`
* Proper handling of complex syntax (heredoc, single-quote package delimiter, regular expressions) (ongoing)

### SQL
* Named scopes for schema, table, column, column alias
* named scopes for SQL functions, by category (aggregate, data-manipulation, operator)

Conventions
-----------
* The files should be written in XML Plist format. The extra regex-escaping required in other markup
  formats (eg, JSON) goes against the objectives of clarity and readability (though the syntax is
  more concise).
* When defining patterns, necessary `<dict>` keys should always appear in the following order:
    * name *or* contentName
    * match
    * begin
    * end
    * captures
    * beginCaptures
    * endCaptures
    * applyEndPatternLast
    * patterns
* The `patterns` section should only contain precedence logic.
* The `repository` section should contain all matching logic (with entries ordered alphabetically).
* All `dict` entries should be followed by a `/* comment */` stating what is to be matched.
* All repository `key` entries should be preceded by a `/* comment */` stating what the subpatterns match.
* Separate the `patterns` and `repository` sections with 5 empty lines.
* Separate unrelated `dict` entry groups with 3 empty lines.
* Use tabs, not spaces. Set the tab width to 4 characters.

### Naming Taxonomy
The following is a guide to common scopes. Syntax definitions may deviate from this, but at the expense
of theme support. The list is not exhaustive since many languages offer unique features.
* __comment__                                    &#8212; values ignored by the language
    * line
        * `<character>`                          &#8212; `number-sign` for `# comment`, etc
    * block
        * documentation
* __constant__
    * boolean                                    &#8212; `true` and `false`
    * character                                  &#8212; values standing for characters
        * escape                                 &#8212; `\n`, `\t`, etc
    * language                                   &#8212; `undef`, `null`, `nil`, etc
    * numeric                                    &#8212; values representing numbers
* __entity__                                     &#8212; values that make up a larger part of the file
    * name
        * function                               &#8212; a function defined in the file
        * chapter
        * tag                                    &#8212; a tag name, in XML or HTML
        * attribute
    * other
        * attribute-name                         &#8212; a tag attribute
* __invalid__
    * illegal
    * deprecated
* __keyword__
    * control                                    &#8212; control flow: `if`, `else`, `continue`, etc
    * function                                   &#8212; built-in language functions
    * operator                                   &#8212; built-in language operators
* __markup__
    * bold
    * heading
    * italic
* __punctuation__
    * open
    * close
* __string__
    * quoted
        * double
        * single
        * triple
    * unquoted
    * regexp                                     &#8212; regular expressions
* __storage__
    * type                                       &#8212; `class`, `function`, `int`, `char`, etc
    * modifier                                   &#8212; `var`, `static`, `final`, `public`, etc
* __support__
    * function                                   &#8212; functions defined in another file
* __variable__                                   &#8212; when possible, identify data types under `variable.other.<type>`
