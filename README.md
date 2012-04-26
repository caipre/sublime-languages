Sublime-Languages
=================

The existing language files seemed overly complex, lacked comments and documentation, and occasionally
just didn't work. I'm hoping to change that by starting from scratch. Initially, there are bound to be
errors and missing pieces since I'm sure I only regularly use a small subset of the languages' features.
Over time, I'll hopefully develop language definitions that are more comprehensible, effective, and
complete.

In general, I will follow the naming conventions specified in the Textmate [language grammars][1]
documentation. This is sensible since it means existing themes will immediately support the new language
definitions. Unfortunately, the specification is vague and in some instances incomplete; where necessary,
I will use my best judgment to allow these from-scratch languages to be as readable and complete as
possible.
[1]: http://manual.macromates.com/en/language_grammars "Textmate language grammars"

### Available
* Perl

### Planned
* HTML
* XML
* CSS
* Javascript
* JSON
* Bash (Shellscript)
* Diff
* Python
* SQL

Conventions
-----------
* The files should be written in XML Plist format. The extra regex-escaping required in other markup
  formats (eg, JSON) goes against the objective of clarity and readability (though the syntax is cleaner).
* When defining new patterns, `<dict>` keys should always appear in the following order:
  * name *or* contentName
  * match
  * begin
  * beginCaptures
  * end
  * endCaptures
  * applyEndPatternLast
  * patterns
