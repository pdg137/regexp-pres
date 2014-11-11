Notes on Regexps

Basics
======

Making a regexp in Ruby: /abc/, %r{abc}, or Regexp.new(abc)
s =~ /abc/
/abc/.match(s)
/abc/ === s
case s; when /abc/ ...
s[/abc/]
s.index(/abc/)

def foo; "abc" =~ /abc/; end

Wildcards
=========

.   any character EXCEPT newline
?   optional
*   any number of times
+   1+ times
{n} exactly n times
{n,m} {,m} {n,} etc.
[]  character class
\w  word [a-zA-Z0-9_]
\W  not word [^a-zA-Z0-9_]
\d  digit [0-9]
\D  not digit [^0-9]
\s  whitespace [ \t\r\n\f]
\S  not whitespace [^ \t\r\n\f]

Note: Ruby Regexps are aware of charsets!
(Thanks to the Oniguruma regular expression library.)

Example: does this regexp match email addresses?

%r{\w+@[\w.]+}.match "bob@gmail.com"

Anchors
=======

^  beginning of line
$  end of line
\A beginning of string
\z end of string
\Z end of chomped string
\b word boundary
\B non-word boundary

Groups & backreferences
=======================

/(.*)\1/ - matches "abcabc", "efef", etc.

MatchData
=========

Returned by .match or found in the $~ LOCAL. (Really, it's local!)

match[0] - the matched string (also $&)
match[n] - the nth group (also $1, $2, etc.)

Use with other methods
======================
String#sub, String#gsub
String#scan
String#split

Fancy stuff
===========

Zero-width assertions:
(?=...) positive lookahead
(?!...) negative lookahead
(?<=..) positive lookbehind
(?<!..) negative lookbehind

Laziness: ?

Problems
========

Convert Last, First to First Last.
Identify numbers divisible by five.
Identify numbers divisible by three. (Hard)
Select sentences: "Here is a sentence. Here is another sentence. And so on."
COrrect TWo INitial CAps BUT NOT THIS.

