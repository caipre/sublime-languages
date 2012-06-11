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

__Available languages:__ Perl

__Planned languages:__ HTML, XML, CSS, Javascript, JSON, Bash (Shellscript), Diff, Python, SQL

Conventions
-----------
* The files should be written in XML Plist format. The extra regex-escaping required in other markup
  formats (eg, JSON) goes against the objectives of clarity and readability (though the syntax is
  more concise).
* When defining new patterns, `<dict>` keys should always appear in the following order:
  * name *or* contentName
  * match
  * begin
  * end
  * beginCaptures
  * endCaptures
  * applyEndPatternLast
  * patterns
* Use tabs, not spaces

Language Features
-----------------
### Perl
* Named scopes for all [special variables](http://perldoc.perl.org/perlvar.html) under `variable.other.special`
* Distinct scopes for scalars, arrays, hashes under `variable.other.{scalar,array,hash}.perl`
* Proper handing of complex regular expressions (in progress)

### Fountain
* Complete support for syntax [as defined](http://fountain.io/syntax) on 2012-02-07.
