Notes on Regexps

Basics
======

Making a regexp in Ruby: /abc/, %r{abc}, or Regexp.new(abc)
s =~ /abc/
/abc/.match(s)
/abc/ === s
case s; when /abc/ ...

def foo; "abc" =~ /abc/; end

Wildcards
=========

.   any character EXCEPT newline
?   optional
*   any number of times
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

/\w@[\w.]/
