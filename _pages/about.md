---
permalink: /about/
title: "About"
---


<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>GitHub Flavored Markdown Spec</title>
<style type="text/css">
body { font-family: Helvetica, arial, freesans, clean, sans-serif;
    line-height: 1.4;
    max-width: 48em;
    margin: auto;
    color: #333333;
    background-color: #fff;
    font-size: 13pt;
}
div#TOC ul { list-style: none; }
div.license {
  margin-top: 1em;
  font-style: italic;
  font-size: 80%;
}
h1 { font-size: 140%; font-weight: bold; border-top: 1px solid gray; padding-top: 0.5em; }
h2 { font-size: 120%; font-weight: bold; }
h3 { font-size: 110%; font-weight: bold; }
h4 { font-size: 100%; font-weight: bold; }
a.definition { font-weight: bold; }
a.toc-link {
  float: right;
  color: #ddd;
  text-decoration: none;
  font-weight: normal;
}
a.toc-link::after {
  content: "\25B2";
}
a.toc-link:hover { color: #000; }
span.space { position: relative; }
span.number:after { content: "  " }
span.space:after {
  content: "·";
  position: absolute;
  /* create a mark that indicates a space (trick from D. Greenspan) */
  top: 0px; bottom: 7px; left: 1px; right: 1px;
  color: #AAA;
}
div.example { overflow: hidden; }
p { text-align: justify; }
pre { padding: 0.5em; margin-left: 0; margin-right: 0; margin-top: 0.2em;
  margin-bottom: 0.5em; font-size: 88%; }
pre {
 white-space: pre-wrap;       /* css-3 */
 white-space: -moz-pre-wrap;  /* Mozilla, since 1999 */
 white-space: -pre-wrap;      /* Opera 4-6 */
 white-space: -o-pre-wrap;    /* Opera 7 */
 word-wrap: break-word;       /* Internet Explorer 5.5+ */
}
code { font-family: monospace; background-color: #D3E1E4; }
pre > code { background-color: transparent; }
.example { font-size: 0; /* hack to get width:50% to work on inline-block */
           padding-bottom: 6pt; }
.column pre  { font-size: 11pt; padding-left: 6pt; padding-right: 6pt;
               padding-top: 2pt; padding-bottom: 2pt; }
div.examplenum { font-size: 11pt; text-align: left; margin-bottom:10px; }
div.column { display: inline-block; width: 50%; vertical-align: top; }
.extension { background: #e0f0e0; }
div.example > div:nth-child(2) { clear:left; background-color: #D3E1E4; }
div.example > div:nth-child(3) { clear:right; background-color: #C9CaCE; }
#watermark {
 position:fixed;
 bottom:0px;
 left:0px;
 padding: 1em;
 width: 100%;
 font-size: 120%;
 opacity:0.7;
 z-index:99;
 color: white;
}
#watermark a { color: white; }
a.dingus { 
  margin-left: 1em;
  cursor: pointer;
  line-height: 30px;
  padding: 4px 7px;
  color: #FFF;
  background-color: #33C3F0;
  box-shadow: 2px 2px 2px rgba(0,0,0,.2);
  border-color: #4FCAEF;
  border-bottom: 2px #2A9EC1 solid;
  border-right: 2px #2A9EC1 solid;
}
a.footnoteRef > sup:before {
  content: "[";
}
a.footnoteRef > sup:after {
  content: "]";
}
a.footnoteRef > sup {
  vertical-align: baseline;
  font-size: 100%;
}
@media print {
  @page {
    size: auto;
    margin: 1.2in 1.2in 1.2in 1.2in;
  }
  body {
      margin: 0px;
      line-height: 1.2;
      font-size: 10pt;
    }
 .column pre  { font-size: 9pt; }
 div.examplenum { font-size: 9pt; }
 a.dingus { display: none; }
}
</style>
</head>
<body>
<h1 class="title">GitHub Flavored Markdown Spec</h1>
<div class="version">Version 0.29-gfm (2019-04-06)</div>
<div class="license">
  This formal specification is based on the
  <a href="http://spec.commonmark.org">CommonMark Spec</a> by
  <a href="http://github.com/jgm">John MacFarlane</a> and licensed under
  <a rel="license"
   href="http://creativecommons.org/licenses/by-sa/4.0/">
    <img style="vertical-align:middle" alt="Creative Commons BY-SA" style="border-width:0"
   src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png"/></a>
</div>
<div id="watermark"></div>

<div id="TOC">
<ul>
<li><a href="#introduction"><span class="number">1</span>Introduction</a>
<ul>
<li><a href="#what-is-github-flavored-markdown-"><span class="number">1.1</span>What is GitHub Flavored Markdown?</a></li>
<li><a href="#what-is-markdown-"><span class="number">1.2</span>What is Markdown?</a></li>
<li><a href="#why-is-a-spec-needed-"><span class="number">1.3</span>Why is a spec needed?</a></li>
<li><a href="#about-this-document"><span class="number">1.4</span>About this document</a></li>
</ul>
</li>
<li><a href="#preliminaries"><span class="number">2</span>Preliminaries</a>
<ul>
<li><a href="#characters-and-lines"><span class="number">2.1</span>Characters and lines</a></li>
<li><a href="#tabs"><span class="number">2.2</span>Tabs</a></li>
<li><a href="#insecure-characters"><span class="number">2.3</span>Insecure characters</a></li>
</ul>
</li>
<li><a href="#blocks-and-inlines"><span class="number">3</span>Blocks and inlines</a>
<ul>
<li><a href="#precedence"><span class="number">3.1</span>Precedence</a></li>
<li><a href="#container-blocks-and-leaf-blocks"><span class="number">3.2</span>Container blocks and leaf blocks</a></li>
</ul>
</li>
<li><a href="#leaf-blocks"><span class="number">4</span>Leaf blocks</a>
<ul>
<li><a href="#thematic-breaks"><span class="number">4.1</span>Thematic breaks</a></li>
<li><a href="#atx-headings"><span class="number">4.2</span>ATX headings</a></li>
<li><a href="#setext-headings"><span class="number">4.3</span>Setext headings</a></li>
<li><a href="#indented-code-blocks"><span class="number">4.4</span>Indented code blocks</a></li>
<li><a href="#fenced-code-blocks"><span class="number">4.5</span>Fenced code blocks</a></li>
<li><a href="#html-blocks"><span class="number">4.6</span>HTML blocks</a></li>
<li><a href="#link-reference-definitions"><span class="number">4.7</span>Link reference definitions</a></li>
<li><a href="#paragraphs"><span class="number">4.8</span>Paragraphs</a></li>
<li><a href="#blank-lines"><span class="number">4.9</span>Blank lines</a></li>
<li><span class="extension"><a href="#tables-extension-"><span class="number">4.10</span>Tables (extension)</a></span></li>
</ul>
</li>
<li><a href="#container-blocks"><span class="number">5</span>Container blocks</a>
<ul>
<li><a href="#block-quotes"><span class="number">5.1</span>Block quotes</a></li>
<li><a href="#list-items"><span class="number">5.2</span>List items</a></li>
<li><span class="extension"><a href="#task-list-items-extension-"><span class="number">5.3</span>Task list items (extension)</a></span></li>
<li><a href="#lists"><span class="number">5.4</span>Lists</a></li>
</ul>
</li>
<li><a href="#inlines"><span class="number">6</span>Inlines</a>
<ul>
<li><a href="#backslash-escapes"><span class="number">6.1</span>Backslash escapes</a></li>
<li><a href="#entity-and-numeric-character-references"><span class="number">6.2</span>Entity and numeric character references</a></li>
<li><a href="#code-spans"><span class="number">6.3</span>Code spans</a></li>
<li><a href="#emphasis-and-strong-emphasis"><span class="number">6.4</span>Emphasis and strong emphasis</a></li>
<li><span class="extension"><a href="#strikethrough-extension-"><span class="number">6.5</span>Strikethrough (extension)</a></span></li>
<li><a href="#links"><span class="number">6.6</span>Links</a></li>
<li><a href="#images"><span class="number">6.7</span>Images</a></li>
<li><a href="#autolinks"><span class="number">6.8</span>Autolinks</a></li>
<li><span class="extension"><a href="#autolinks-extension-"><span class="number">6.9</span>Autolinks (extension)</a></span></li>
<li><a href="#raw-html"><span class="number">6.10</span>Raw HTML</a></li>
<li><span class="extension"><a href="#disallowed-raw-html-extension-"><span class="number">6.11</span>Disallowed Raw HTML (extension)</a></span></li>
<li><a href="#hard-line-breaks"><span class="number">6.12</span>Hard line breaks</a></li>
<li><a href="#soft-line-breaks"><span class="number">6.13</span>Soft line breaks</a></li>
<li><a href="#textual-content"><span class="number">6.14</span>Textual content</a></li>
</ul>
</li>
<li><a href="#appendix-a-parsing-strategy">Appendix: A parsing strategy</a>
<ul>
<li><a href="#overview">Overview</a></li>
<li><a href="#phase-1-block-structure">Phase 1: block structure</a></li>
<li><a href="#phase-2-inline-structure">Phase 2: inline structure</a></li>
</ul>
</li>
</ul>

</div>

<h1 id="introduction" href="#introduction" class="definition">
<span class="number">1</span>Introduction
</h1>
<h2 id="what-is-github-flavored-markdown-" href="#what-is-github-flavored-markdown-" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">1.1</span>What is GitHub Flavored Markdown?
</h2>
<p>GitHub Flavored Markdown, often shortened as GFM, is the dialect of Markdown
that is currently supported for user content on GitHub.com and GitHub
Enterprise.</p>
<p>This formal specification, based on the CommonMark Spec, defines the syntax and
semantics of this dialect.</p>
<p>GFM is a strict superset of CommonMark. All the features which are supported in
GitHub user content and that are not specified on the original CommonMark Spec
are hence known as <strong>extensions</strong>, and highlighted as such.</p>
<p>While GFM supports a wide range of inputs, it’s worth noting that GitHub.com
and GitHub Enterprise perform additional post-processing and sanitization after
GFM is converted to HTML to ensure security and consistency of the website.</p>
<h2 id="what-is-markdown-" href="#what-is-markdown-" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">1.2</span>What is Markdown?
</h2>
<p>Markdown is a plain text format for writing structured documents,
based on conventions for indicating formatting in email
and usenet posts.  It was developed by John Gruber (with
help from Aaron Swartz) and released in 2004 in the form of a
<a href="http://daringfireball.net/projects/markdown/syntax">syntax description</a>
and a Perl script (<code>Markdown.pl</code>) for converting Markdown to
HTML.  In the next decade, dozens of implementations were
developed in many languages.  Some extended the original
Markdown syntax with conventions for footnotes, tables, and
other document elements.  Some allowed Markdown documents to be
rendered in formats other than HTML.  Websites like Reddit,
StackOverflow, and GitHub had millions of people using Markdown.
And Markdown started to be used beyond the web, to author books,
articles, slide shows, letters, and lecture notes.</p>
<p>What distinguishes Markdown from many other lightweight markup
syntaxes, which are often easier to write, is its readability.
As Gruber writes:</p>
<blockquote>
<p>The overriding design goal for Markdown’s formatting syntax is
to make it as readable as possible. The idea is that a
Markdown-formatted document should be publishable as-is, as
plain text, without looking like it’s been marked up with tags
or formatting instructions.
(<a href="http://daringfireball.net/projects/markdown/">http://daringfireball.net/projects/markdown/</a>)</p>
</blockquote>
<p>The point can be illustrated by comparing a sample of
<a href="http://www.methods.co.nz/asciidoc/">AsciiDoc</a> with
an equivalent sample of Markdown.  Here is a sample of
AsciiDoc from the AsciiDoc manual:</p>
<pre><code>1. List item one.
+
List item one continued with a second paragraph followed by an
Indented block.
+
.................
$ ls *.sh
$ mv *.sh ~/tmp
.................
+
List item continued with a third paragraph.

2. List item two continued with an open block.
+
--
This paragraph is part of the preceding list item.

a. This list is nested and does not require explicit item
continuation.
+
This paragraph is part of the preceding list item.

b. List item b.

This paragraph belongs to item two of the outer list.
--
</code></pre>
<p>And here is the equivalent in Markdown:</p>
<pre><code>1.  List item one.

    List item one continued with a second paragraph followed by an
    Indented block.

        $ ls *.sh
        $ mv *.sh ~/tmp

    List item continued with a third paragraph.

2.  List item two continued with an open block.

    This paragraph is part of the preceding list item.

    1. This list is nested and does not require explicit item continuation.

       This paragraph is part of the preceding list item.

    2. List item b.

    This paragraph belongs to item two of the outer list.
</code></pre>
<p>The AsciiDoc version is, arguably, easier to write. You don’t need
to worry about indentation.  But the Markdown version is much easier
to read.  The nesting of list items is apparent to the eye in the
source, not just in the processed document.</p>
<h2 id="why-is-a-spec-needed-" href="#why-is-a-spec-needed-" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">1.3</span>Why is a spec needed?
</h2>
<p>John Gruber’s <a href="http://daringfireball.net/projects/markdown/syntax">canonical description of Markdown’s
syntax</a>
does not specify the syntax unambiguously.  Here are some examples of
questions it does not answer:</p>
<ol>
<li>
<p>How much indentation is needed for a sublist?  The spec says that
continuation paragraphs need to be indented four spaces, but is
not fully explicit about sublists.  It is natural to think that
they, too, must be indented four spaces, but <code>Markdown.pl</code> does
not require that.  This is hardly a “corner case,” and divergences
between implementations on this issue often lead to surprises for
users in real documents. (See <a href="http://article.gmane.org/gmane.text.markdown.general/1997">this comment by John
Gruber</a>.)</p>
</li>
<li>
<p>Is a blank line needed before a block quote or heading?
Most implementations do not require the blank line.  However,
this can lead to unexpected results in hard-wrapped text, and
also to ambiguities in parsing (note that some implementations
put the heading inside the blockquote, while others do not).
(John Gruber has also spoken <a href="http://article.gmane.org/gmane.text.markdown.general/2146">in favor of requiring the blank
lines</a>.)</p>
</li>
<li>
<p>Is a blank line needed before an indented code block?
(<code>Markdown.pl</code> requires it, but this is not mentioned in the
documentation, and some implementations do not require it.)</p>
<pre><code class="language-markdown">paragraph
    code?
</code></pre>
</li>
<li>
<p>What is the exact rule for determining when list items get
wrapped in <code>&lt;p&gt;</code> tags?  Can a list be partially “loose” and partially
“tight”?  What should we do with a list like this?</p>
<pre><code class="language-markdown">1. one

2. two
3. three
</code></pre>
<p>Or this?</p>
<pre><code class="language-markdown">1.  one
    - a

    - b
2.  two
</code></pre>
<p>(There are some relevant comments by John Gruber
<a href="http://article.gmane.org/gmane.text.markdown.general/2554">here</a>.)</p>
</li>
<li>
<p>Can list markers be indented?  Can ordered list markers be right-aligned?</p>
<pre><code class="language-markdown"> 8. item 1
 9. item 2
10. item 2a
</code></pre>
</li>
<li>
<p>Is this one list with a thematic break in its second item,
or two lists separated by a thematic break?</p>
<pre><code class="language-markdown">* a
* * * * *
* b
</code></pre>
</li>
<li>
<p>When list markers change from numbers to bullets, do we have
two lists or one?  (The Markdown syntax description suggests two,
but the perl scripts and many other implementations produce one.)</p>
<pre><code class="language-markdown">1. fee
2. fie
-  foe
-  fum
</code></pre>
</li>
<li>
<p>What are the precedence rules for the markers of inline structure?
For example, is the following a valid link, or does the code span
take precedence ?</p>
<pre><code class="language-markdown">[a backtick (`)](/url) and [another backtick (`)](/url).
</code></pre>
</li>
<li>
<p>What are the precedence rules for markers of emphasis and strong
emphasis?  For example, how should the following be parsed?</p>
<pre><code class="language-markdown">*foo *bar* baz*
</code></pre>
</li>
<li>
<p>What are the precedence rules between block-level and inline-level
structure?  For example, how should the following be parsed?</p>
<pre><code class="language-markdown">- `a long code span can contain a hyphen like this
  - and it can screw things up`
</code></pre>
</li>
<li>
<p>Can list items include section headings?  (<code>Markdown.pl</code> does not
allow this, but does allow blockquotes to include headings.)</p>
<pre><code class="language-markdown">- # Heading
</code></pre>
</li>
<li>
<p>Can list items be empty?</p>
<pre><code class="language-markdown">* a
*
* b
</code></pre>
</li>
<li>
<p>Can link references be defined inside block quotes or list items?</p>
<pre><code class="language-markdown">&gt; Blockquote [foo].
&gt;
&gt; [foo]: /url
</code></pre>
</li>
<li>
<p>If there are multiple definitions for the same reference, which takes
precedence?</p>
<pre><code class="language-markdown">[foo]: /url1
[foo]: /url2

[foo][]
</code></pre>
</li>
</ol>
<p>In the absence of a spec, early implementers consulted <code>Markdown.pl</code>
to resolve these ambiguities.  But <code>Markdown.pl</code> was quite buggy, and
gave manifestly bad results in many cases, so it was not a
satisfactory replacement for a spec.</p>
<p>Because there is no unambiguous spec, implementations have diverged
considerably.  As a result, users are often surprised to find that
a document that renders one way on one system (say, a GitHub wiki)
renders differently on another (say, converting to docbook using
pandoc).  To make matters worse, because nothing in Markdown counts
as a “syntax error,” the divergence often isn’t discovered right away.</p>
<h2 id="about-this-document" href="#about-this-document" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">1.4</span>About this document
</h2>
<p>This document attempts to specify Markdown syntax unambiguously.
It contains many examples with side-by-side Markdown and
HTML.  These are intended to double as conformance tests.  An
accompanying script <code>spec_tests.py</code> can be used to run the tests
against any Markdown program:</p>
<pre><code>python test/spec_tests.py --spec spec.txt --program PROGRAM
</code></pre>
<p>Since this document describes how Markdown is to be parsed into
an abstract syntax tree, it would have made sense to use an abstract
representation of the syntax tree instead of HTML.  But HTML is capable
of representing the structural distinctions we need to make, and the
choice of HTML for the tests makes it possible to run the tests against
an implementation without writing an abstract syntax tree renderer.</p>
<p>This document is generated from a text file, <code>spec.txt</code>, written
in Markdown with a small extension for the side-by-side tests.
The script <code>tools/makespec.py</code> can be used to convert <code>spec.txt</code> into
HTML or CommonMark (which can then be converted into other formats).</p>
<p>In the examples, the <code>→</code> character is used to represent tabs.</p>
<h1 id="preliminaries" href="#preliminaries" class="definition">
<span class="number">2</span>Preliminaries
</h1>
<h2 id="characters-and-lines" href="#characters-and-lines" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">2.1</span>Characters and lines
</h2>
<p>Any sequence of <a href="#character">characters</a> is a valid CommonMark
document.</p>
<p>A <a id="character" href="#character" class="definition">character</a> is a Unicode code point.  Although some
code points (for example, combining accents) do not correspond to
characters in an intuitive sense, all code points count as characters
for purposes of this spec.</p>
<p>This spec does not specify an encoding; it thinks of lines as composed
of <a href="#character">characters</a> rather than bytes.  A conforming parser may be limited
to a certain encoding.</p>
<p>A <a id="line" href="#line" class="definition">line</a> is a sequence of zero or more <a href="#character">characters</a>
other than newline (<code>U+000A</code>) or carriage return (<code>U+000D</code>),
followed by a <a href="#line-ending">line ending</a> or by the end of file.</p>
<p>A <a id="line-ending" href="#line-ending" class="definition">line ending</a> is a newline (<code>U+000A</code>), a carriage return
(<code>U+000D</code>) not followed by a newline, or a carriage return and a
following newline.</p>
<p>A line containing no characters, or a line containing only spaces
(<code>U+0020</code>) or tabs (<code>U+0009</code>), is called a <a id="blank-line" href="#blank-line" class="definition">blank line</a>.</p>
<p>The following definitions of character classes will be used in this spec:</p>
<p>A <a id="whitespace-character" href="#whitespace-character" class="definition">whitespace character</a> is a space
(<code>U+0020</code>), tab (<code>U+0009</code>), newline (<code>U+000A</code>), line tabulation (<code>U+000B</code>),
form feed (<code>U+000C</code>), or carriage return (<code>U+000D</code>).</p>
<p><a id="whitespace" href="#whitespace" class="definition">Whitespace</a> is a sequence of one or more <a href="#whitespace-character">whitespace
characters</a>.</p>
<p>A <a id="unicode-whitespace-character" href="#unicode-whitespace-character" class="definition">Unicode whitespace character</a> is
any code point in the Unicode <code>Zs</code> general category, or a tab (<code>U+0009</code>),
carriage return (<code>U+000D</code>), newline (<code>U+000A</code>), or form feed
(<code>U+000C</code>).</p>
<p><a id="unicode-whitespace" href="#unicode-whitespace" class="definition">Unicode whitespace</a> is a sequence of one
or more <a href="#unicode-whitespace-character">Unicode whitespace characters</a>.</p>
<p>A <a id="space" href="#space" class="definition">space</a> is <code>U+0020</code>.</p>
<p>A <a id="non-whitespace-character" href="#non-whitespace-character" class="definition">non-whitespace character</a> is any character
that is not a <a href="#whitespace-character">whitespace character</a>.</p>
<p>An <a id="ascii-punctuation-character" href="#ascii-punctuation-character" class="definition">ASCII punctuation character</a>
is <code>!</code>, <code>&quot;</code>, <code>#</code>, <code>$</code>, <code>%</code>, <code>&amp;</code>, <code>'</code>, <code>(</code>, <code>)</code>,
<code>*</code>, <code>+</code>, <code>,</code>, <code>-</code>, <code>.</code>, <code>/</code> (U+0021–2F),
<code>:</code>, <code>;</code>, <code>&lt;</code>, <code>=</code>, <code>&gt;</code>, <code>?</code>, <code>@</code> (U+003A–0040),
<code>[</code>, <code>\</code>, <code>]</code>, <code>^</code>, <code>_</code>, <code>`</code> (U+005B–0060),
<code>{</code>, <code>|</code>, <code>}</code>, or <code>~</code> (U+007B–007E).</p>
<p>A <a id="punctuation-character" href="#punctuation-character" class="definition">punctuation character</a> is an <a href="#ascii-punctuation-character">ASCII
punctuation character</a> or anything in
the general Unicode categories  <code>Pc</code>, <code>Pd</code>, <code>Pe</code>, <code>Pf</code>, <code>Pi</code>, <code>Po</code>, or <code>Ps</code>.</p>
<h2 id="tabs" href="#tabs" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">2.2</span>Tabs
</h2>
<p>Tabs in lines are not expanded to <a href="#space">spaces</a>.  However,
in contexts where whitespace helps to define block structure,
tabs behave as if they were replaced by spaces with a tab stop
of 4 characters.</p>
<p>Thus, for example, a tab can be used instead of four spaces
in an indented code block.  (Note, however, that internal
tabs are passed through as literal tabs, not expanded to
spaces.)</p>
<div class="example" id="example-1">
<div class="examplenum">
<a href="#example-1">Example 1</a>
</div>
<div class="column">
<pre><code class="language-markdown">→foo→baz→→bim
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo→baz→→bim
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-2">
<div class="examplenum">
<a href="#example-2">Example 2</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span>→foo→baz→→bim
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo→baz→→bim
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-3">
<div class="examplenum">
<a href="#example-3">Example 3</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>a→a
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>ὐ→a
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;a→a
ὐ→a
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>In the following example, a continuation paragraph of a list
item is indented with a tab; this has exactly the same effect
as indentation with four spaces would:</p>
<div class="example" id="example-4">
<div class="examplenum">
<a href="#example-4">Example 4</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span>-<span class="space"> </span>foo

→bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;
&lt;p&gt;foo&lt;/p&gt;
&lt;p&gt;bar&lt;/p&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-5">
<div class="examplenum">
<a href="#example-5">Example 5</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>foo

→→bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;
&lt;p&gt;foo&lt;/p&gt;
&lt;pre&gt;&lt;code&gt;<span class="space"> </span><span class="space"> </span>bar
&lt;/code&gt;&lt;/pre&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<p>Normally the <code>&gt;</code> that begins a block quote may be followed
optionally by a space, which is not considered part of the
content.  In the following case <code>&gt;</code> is followed by a tab,
which is treated as if it were expanded into three spaces.
Since one of these spaces is considered part of the
delimiter, <code>foo</code> is considered to be indented six spaces
inside the block quote context, so we get an indented
code block starting with two spaces.</p>
<div class="example" id="example-6">
<div class="examplenum">
<a href="#example-6">Example 6</a>
</div>
<div class="column">
<pre><code class="language-markdown">&gt;→→foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;blockquote&gt;
&lt;pre&gt;&lt;code&gt;<span class="space"> </span><span class="space"> </span>foo
&lt;/code&gt;&lt;/pre&gt;
&lt;/blockquote&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-7">
<div class="examplenum">
<a href="#example-7">Example 7</a>
</div>
<div class="column">
<pre><code class="language-markdown">-→→foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;
&lt;pre&gt;&lt;code&gt;<span class="space"> </span><span class="space"> </span>foo
&lt;/code&gt;&lt;/pre&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-8">
<div class="examplenum">
<a href="#example-8">Example 8</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
→bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo
bar
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-9">
<div class="examplenum">
<a href="#example-9">Example 9</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>-<span class="space"> </span>foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span>-<span class="space"> </span>bar
→<span class="space"> </span>-<span class="space"> </span>baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;foo
&lt;ul&gt;
&lt;li&gt;bar
&lt;ul&gt;
&lt;li&gt;baz&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-10">
<div class="examplenum">
<a href="#example-10">Example 10</a>
</div>
<div class="column">
<pre><code class="language-markdown">#→Foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;Foo&lt;/h1&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-11">
<div class="examplenum">
<a href="#example-11">Example 11</a>
</div>
<div class="column">
<pre><code class="language-markdown">*→*→*→
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<h2 id="insecure-characters" href="#insecure-characters" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">2.3</span>Insecure characters
</h2>
<p>For security reasons, the Unicode character <code>U+0000</code> must be replaced
with the REPLACEMENT CHARACTER (<code>U+FFFD</code>).</p>
<h1 id="blocks-and-inlines" href="#blocks-and-inlines" class="definition">
<span class="number">3</span>Blocks and inlines
</h1>
<p>We can think of a document as a sequence of
<a id="blocks" href="#blocks" class="definition">blocks</a>—structural elements like paragraphs, block
quotations, lists, headings, rules, and code blocks.  Some blocks (like
block quotes and list items) contain other blocks; others (like
headings and paragraphs) contain <a id="inline" href="#inline" class="definition">inline</a> content—text,
links, emphasized text, images, code spans, and so on.</p>
<h2 id="precedence" href="#precedence" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">3.1</span>Precedence
</h2>
<p>Indicators of block structure always take precedence over indicators
of inline structure.  So, for example, the following is a list with
two items, not a list with one item containing a code span:</p>
<div class="example" id="example-12">
<div class="examplenum">
<a href="#example-12">Example 12</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>`one
-<span class="space"> </span>two`
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;`one&lt;/li&gt;
&lt;li&gt;two`&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<p>This means that parsing can proceed in two steps:  first, the block
structure of the document can be discerned; second, text lines inside
paragraphs, headings, and other block constructs can be parsed for inline
structure.  The second step requires information about link reference
definitions that will be available only at the end of the first
step.  Note that the first step requires processing lines in sequence,
but the second can be parallelized, since the inline parsing of
one block element does not affect the inline parsing of any other.</p>
<h2 id="container-blocks-and-leaf-blocks" href="#container-blocks-and-leaf-blocks" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">3.2</span>Container blocks and leaf blocks
</h2>
<p>We can divide blocks into two types:
<a id="container-blocks" href="#container-blocks" class="definition">container blocks</a>,
which can contain other blocks, and <a id="leaf-blocks" href="#leaf-blocks" class="definition">leaf blocks</a>,
which cannot.</p>
<h1 id="leaf-blocks" href="#leaf-blocks" class="definition">
<span class="number">4</span>Leaf blocks
</h1>
<p>This section describes the different kinds of leaf block that make up a
Markdown document.</p>
<h2 id="thematic-breaks" href="#thematic-breaks" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.1</span>Thematic breaks
</h2>
<p>A line consisting of 0-3 spaces of indentation, followed by a sequence
of three or more matching <code>-</code>, <code>_</code>, or <code>*</code> characters, each followed
optionally by any number of spaces or tabs, forms a
<a id="thematic-break" href="#thematic-break" class="definition">thematic break</a>.</p>
<div class="example" id="example-13">
<div class="examplenum">
<a href="#example-13">Example 13</a>
</div>
<div class="column">
<pre><code class="language-markdown">***
---
___
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>Wrong characters:</p>
<div class="example" id="example-14">
<div class="examplenum">
<a href="#example-14">Example 14</a>
</div>
<div class="column">
<pre><code class="language-markdown">+++
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;+++&lt;/p&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-15">
<div class="examplenum">
<a href="#example-15">Example 15</a>
</div>
<div class="column">
<pre><code class="language-markdown">===
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;===&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Not enough characters:</p>
<div class="example" id="example-16">
<div class="examplenum">
<a href="#example-16">Example 16</a>
</div>
<div class="column">
<pre><code class="language-markdown">--
**
__
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;--
**
__&lt;/p&gt;
</code></pre>
</div>
</div>
<p>One to three spaces indent are allowed:</p>
<div class="example" id="example-17">
<div class="examplenum">
<a href="#example-17">Example 17</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>***
<span class="space"> </span><span class="space"> </span>***
<span class="space"> </span><span class="space"> </span><span class="space"> </span>***
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>Four spaces is too many:</p>
<div class="example" id="example-18">
<div class="examplenum">
<a href="#example-18">Example 18</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>***
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;***
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-19">
<div class="examplenum">
<a href="#example-19">Example 19</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>***
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
***&lt;/p&gt;
</code></pre>
</div>
</div>
<p>More than three characters may be used:</p>
<div class="example" id="example-20">
<div class="examplenum">
<a href="#example-20">Example 20</a>
</div>
<div class="column">
<pre><code class="language-markdown">_____________________________________
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>Spaces are allowed between the characters:</p>
<div class="example" id="example-21">
<div class="examplenum">
<a href="#example-21">Example 21</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>-<span class="space"> </span>-<span class="space"> </span>-
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-22">
<div class="examplenum">
<a href="#example-22">Example 22</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>**<span class="space"> </span><span class="space"> </span>*<span class="space"> </span>**<span class="space"> </span>*<span class="space"> </span>**<span class="space"> </span>*<span class="space"> </span>**
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-23">
<div class="examplenum">
<a href="#example-23">Example 23</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>-<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>-<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>-
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>Spaces are allowed at the end:</p>
<div class="example" id="example-24">
<div class="examplenum">
<a href="#example-24">Example 24</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>-<span class="space"> </span>-<span class="space"> </span>-<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>However, no other characters may occur in the line:</p>
<div class="example" id="example-25">
<div class="examplenum">
<a href="#example-25">Example 25</a>
</div>
<div class="column">
<pre><code class="language-markdown">_<span class="space"> </span>_<span class="space"> </span>_<span class="space"> </span>_<span class="space"> </span>a

a------

---a---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;_<span class="space"> </span>_<span class="space"> </span>_<span class="space"> </span>_<span class="space"> </span>a&lt;/p&gt;
&lt;p&gt;a------&lt;/p&gt;
&lt;p&gt;---a---&lt;/p&gt;
</code></pre>
</div>
</div>
<p>It is required that all of the <a href="#non-whitespace-character">non-whitespace characters</a> be the same.
So, this is not a thematic break:</p>
<div class="example" id="example-26">
<div class="examplenum">
<a href="#example-26">Example 26</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>*-*
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;&lt;em&gt;-&lt;/em&gt;&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Thematic breaks do not need blank lines before or after:</p>
<div class="example" id="example-27">
<div class="examplenum">
<a href="#example-27">Example 27</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>foo
***
-<span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;foo&lt;/li&gt;
&lt;/ul&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;ul&gt;
&lt;li&gt;bar&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<p>Thematic breaks can interrupt a paragraph:</p>
<div class="example" id="example-28">
<div class="examplenum">
<a href="#example-28">Example 28</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
***
bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo&lt;/p&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;p&gt;bar&lt;/p&gt;
</code></pre>
</div>
</div>
<p>If a line of dashes that meets the above conditions for being a
thematic break could also be interpreted as the underline of a <a href="#setext-heading">setext
heading</a>, the interpretation as a
<a href="#setext-heading">setext heading</a> takes precedence. Thus, for example,
this is a setext heading, not a paragraph followed by a thematic break:</p>
<div class="example" id="example-29">
<div class="examplenum">
<a href="#example-29">Example 29</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
---
bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo&lt;/h2&gt;
&lt;p&gt;bar&lt;/p&gt;
</code></pre>
</div>
</div>
<p>When both a thematic break and a list item are possible
interpretations of a line, the thematic break takes precedence:</p>
<div class="example" id="example-30">
<div class="examplenum">
<a href="#example-30">Example 30</a>
</div>
<div class="column">
<pre><code class="language-markdown">*<span class="space"> </span>Foo
*<span class="space"> </span>*<span class="space"> </span>*
*<span class="space"> </span>Bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;Foo&lt;/li&gt;
&lt;/ul&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;ul&gt;
&lt;li&gt;Bar&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<p>If you want a thematic break in a list item, use a different bullet:</p>
<div class="example" id="example-31">
<div class="examplenum">
<a href="#example-31">Example 31</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>Foo
-<span class="space"> </span>*<span class="space"> </span>*<span class="space"> </span>*
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;Foo&lt;/li&gt;
&lt;li&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<h2 id="atx-headings" href="#atx-headings" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.2</span>ATX headings
</h2>
<p>An <a id="atx-heading" href="#atx-heading" class="definition">ATX heading</a>
consists of a string of characters, parsed as inline content, between an
opening sequence of 1–6 unescaped <code>#</code> characters and an optional
closing sequence of any number of unescaped <code>#</code> characters.
The opening sequence of <code>#</code> characters must be followed by a
<a href="#space">space</a> or by the end of line. The optional closing sequence of <code>#</code>s must be
preceded by a <a href="#space">space</a> and may be followed by spaces only.  The opening
<code>#</code> character may be indented 0-3 spaces.  The raw contents of the
heading are stripped of leading and trailing spaces before being parsed
as inline content.  The heading level is equal to the number of <code>#</code>
characters in the opening sequence.</p>
<p>Simple headings:</p>
<div class="example" id="example-32">
<div class="examplenum">
<a href="#example-32">Example 32</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span>foo
##<span class="space"> </span>foo
###<span class="space"> </span>foo
####<span class="space"> </span>foo
#####<span class="space"> </span>foo
######<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;foo&lt;/h1&gt;
&lt;h2&gt;foo&lt;/h2&gt;
&lt;h3&gt;foo&lt;/h3&gt;
&lt;h4&gt;foo&lt;/h4&gt;
&lt;h5&gt;foo&lt;/h5&gt;
&lt;h6&gt;foo&lt;/h6&gt;
</code></pre>
</div>
</div>
<p>More than six <code>#</code> characters is not a heading:</p>
<div class="example" id="example-33">
<div class="examplenum">
<a href="#example-33">Example 33</a>
</div>
<div class="column">
<pre><code class="language-markdown">#######<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;#######<span class="space"> </span>foo&lt;/p&gt;
</code></pre>
</div>
</div>
<p>At least one space is required between the <code>#</code> characters and the
heading’s contents, unless the heading is empty.  Note that many
implementations currently do not require the space.  However, the
space was required by the
<a href="http://www.aaronsw.com/2002/atx/atx.py">original ATX implementation</a>,
and it helps prevent things like the following from being parsed as
headings:</p>
<div class="example" id="example-34">
<div class="examplenum">
<a href="#example-34">Example 34</a>
</div>
<div class="column">
<pre><code class="language-markdown">#5<span class="space"> </span>bolt

#hashtag
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;#5<span class="space"> </span>bolt&lt;/p&gt;
&lt;p&gt;#hashtag&lt;/p&gt;
</code></pre>
</div>
</div>
<p>This is not a heading, because the first <code>#</code> is escaped:</p>
<div class="example" id="example-35">
<div class="examplenum">
<a href="#example-35">Example 35</a>
</div>
<div class="column">
<pre><code class="language-markdown">\##<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;##<span class="space"> </span>foo&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Contents are parsed as inlines:</p>
<div class="example" id="example-36">
<div class="examplenum">
<a href="#example-36">Example 36</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span>foo<span class="space"> </span>*bar*<span class="space"> </span>\*baz\*
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;foo<span class="space"> </span>&lt;em&gt;bar&lt;/em&gt;<span class="space"> </span>*baz*&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>Leading and trailing <a href="#whitespace">whitespace</a> is ignored in parsing inline content:</p>
<div class="example" id="example-37">
<div class="examplenum">
<a href="#example-37">Example 37</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;foo&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>One to three spaces indentation are allowed:</p>
<div class="example" id="example-38">
<div class="examplenum">
<a href="#example-38">Example 38</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>###<span class="space"> </span>foo
<span class="space"> </span><span class="space"> </span>##<span class="space"> </span>foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span>#<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h3&gt;foo&lt;/h3&gt;
&lt;h2&gt;foo&lt;/h2&gt;
&lt;h1&gt;foo&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>Four spaces are too much:</p>
<div class="example" id="example-39">
<div class="examplenum">
<a href="#example-39">Example 39</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>#<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;#<span class="space"> </span>foo
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-40">
<div class="examplenum">
<a href="#example-40">Example 40</a>
</div>
<div class="column">
<pre><code class="language-markdown">foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>#<span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;foo
#<span class="space"> </span>bar&lt;/p&gt;
</code></pre>
</div>
</div>
<p>A closing sequence of <code>#</code> characters is optional:</p>
<div class="example" id="example-41">
<div class="examplenum">
<a href="#example-41">Example 41</a>
</div>
<div class="column">
<pre><code class="language-markdown">##<span class="space"> </span>foo<span class="space"> </span>##
<span class="space"> </span><span class="space"> </span>###<span class="space"> </span><span class="space"> </span><span class="space"> </span>bar<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>###
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;foo&lt;/h2&gt;
&lt;h3&gt;bar&lt;/h3&gt;
</code></pre>
</div>
</div>
<p>It need not be the same length as the opening sequence:</p>
<div class="example" id="example-42">
<div class="examplenum">
<a href="#example-42">Example 42</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span>foo<span class="space"> </span>##################################
#####<span class="space"> </span>foo<span class="space"> </span>##
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;foo&lt;/h1&gt;
&lt;h5&gt;foo&lt;/h5&gt;
</code></pre>
</div>
</div>
<p>Spaces are allowed after the closing sequence:</p>
<div class="example" id="example-43">
<div class="examplenum">
<a href="#example-43">Example 43</a>
</div>
<div class="column">
<pre><code class="language-markdown">###<span class="space"> </span>foo<span class="space"> </span>###<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h3&gt;foo&lt;/h3&gt;
</code></pre>
</div>
</div>
<p>A sequence of <code>#</code> characters with anything but <a href="#space">spaces</a> following it
is not a closing sequence, but counts as part of the contents of the
heading:</p>
<div class="example" id="example-44">
<div class="examplenum">
<a href="#example-44">Example 44</a>
</div>
<div class="column">
<pre><code class="language-markdown">###<span class="space"> </span>foo<span class="space"> </span>###<span class="space"> </span>b
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h3&gt;foo<span class="space"> </span>###<span class="space"> </span>b&lt;/h3&gt;
</code></pre>
</div>
</div>
<p>The closing sequence must be preceded by a space:</p>
<div class="example" id="example-45">
<div class="examplenum">
<a href="#example-45">Example 45</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span>foo#
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;foo#&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>Backslash-escaped <code>#</code> characters do not count as part
of the closing sequence:</p>
<div class="example" id="example-46">
<div class="examplenum">
<a href="#example-46">Example 46</a>
</div>
<div class="column">
<pre><code class="language-markdown">###<span class="space"> </span>foo<span class="space"> </span>\###
##<span class="space"> </span>foo<span class="space"> </span>#\##
#<span class="space"> </span>foo<span class="space"> </span>\#
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h3&gt;foo<span class="space"> </span>###&lt;/h3&gt;
&lt;h2&gt;foo<span class="space"> </span>###&lt;/h2&gt;
&lt;h1&gt;foo<span class="space"> </span>#&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>ATX headings need not be separated from surrounding content by blank
lines, and they can interrupt paragraphs:</p>
<div class="example" id="example-47">
<div class="examplenum">
<a href="#example-47">Example 47</a>
</div>
<div class="column">
<pre><code class="language-markdown">****
##<span class="space"> </span>foo
****
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
&lt;h2&gt;foo&lt;/h2&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-48">
<div class="examplenum">
<a href="#example-48">Example 48</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo<span class="space"> </span>bar
#<span class="space"> </span>baz
Bar<span class="space"> </span>foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo<span class="space"> </span>bar&lt;/p&gt;
&lt;h1&gt;baz&lt;/h1&gt;
&lt;p&gt;Bar<span class="space"> </span>foo&lt;/p&gt;
</code></pre>
</div>
</div>
<p>ATX headings can be empty:</p>
<div class="example" id="example-49">
<div class="examplenum">
<a href="#example-49">Example 49</a>
</div>
<div class="column">
<pre><code class="language-markdown">##<span class="space"> </span>
#
###<span class="space"> </span>###
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;&lt;/h2&gt;
&lt;h1&gt;&lt;/h1&gt;
&lt;h3&gt;&lt;/h3&gt;
</code></pre>
</div>
</div>
<h2 id="setext-headings" href="#setext-headings" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.3</span>Setext headings
</h2>
<p>A <a id="setext-heading" href="#setext-heading" class="definition">setext heading</a> consists of one or more
lines of text, each containing at least one <a href="#non-whitespace-character">non-whitespace
character</a>, with no more than 3 spaces indentation, followed by
a <a href="#setext-heading-underline">setext heading underline</a>.  The lines of text must be such
that, were they not followed by the setext heading underline,
they would be interpreted as a paragraph:  they cannot be
interpretable as a <a href="#code-fence">code fence</a>, <a href="#atx-headings">ATX heading</a>,
<a href="#block-quotes">block quote</a>, <a href="#thematic-break">thematic break</a>,
<a href="#list-items">list item</a>, or <a href="#html-blocks">HTML block</a>.</p>
<p>A <a id="setext-heading-underline" href="#setext-heading-underline" class="definition">setext heading underline</a> is a sequence of
<code>=</code> characters or a sequence of <code>-</code> characters, with no more than 3
spaces indentation and any number of trailing spaces.  If a line
containing a single <code>-</code> can be interpreted as an
empty <a href="#list-items">list items</a>, it should be interpreted this way
and not as a <a href="#setext-heading-underline">setext heading underline</a>.</p>
<p>The heading is a level 1 heading if <code>=</code> characters are used in
the <a href="#setext-heading-underline">setext heading underline</a>, and a level 2 heading if <code>-</code>
characters are used.  The contents of the heading are the result
of parsing the preceding lines of text as CommonMark inline
content.</p>
<p>In general, a setext heading need not be preceded or followed by a
blank line.  However, it cannot interrupt a paragraph, so when a
setext heading comes after a paragraph, a blank line is needed between
them.</p>
<p>Simple examples:</p>
<div class="example" id="example-50">
<div class="examplenum">
<a href="#example-50">Example 50</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo<span class="space"> </span>*bar*
=========

Foo<span class="space"> </span>*bar*
---------
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;Foo<span class="space"> </span>&lt;em&gt;bar&lt;/em&gt;&lt;/h1&gt;
&lt;h2&gt;Foo<span class="space"> </span>&lt;em&gt;bar&lt;/em&gt;&lt;/h2&gt;
</code></pre>
</div>
</div>
<p>The content of the header may span more than one line:</p>
<div class="example" id="example-51">
<div class="examplenum">
<a href="#example-51">Example 51</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo<span class="space"> </span>*bar
baz*
====
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;Foo<span class="space"> </span>&lt;em&gt;bar
baz&lt;/em&gt;&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>The contents are the result of parsing the headings’s raw
content as inlines.  The heading’s raw content is formed by
concatenating the lines and removing initial and final
<a href="#whitespace">whitespace</a>.</p>
<div class="example" id="example-52">
<div class="examplenum">
<a href="#example-52">Example 52</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span>Foo<span class="space"> </span>*bar
baz*→
====
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;Foo<span class="space"> </span>&lt;em&gt;bar
baz&lt;/em&gt;&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>The underlining can be any length:</p>
<div class="example" id="example-53">
<div class="examplenum">
<a href="#example-53">Example 53</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
-------------------------

Foo
=
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo&lt;/h2&gt;
&lt;h1&gt;Foo&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>The heading content can be indented up to three spaces, and need
not line up with the underlining:</p>
<div class="example" id="example-54">
<div class="examplenum">
<a href="#example-54">Example 54</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span>Foo
---

<span class="space"> </span><span class="space"> </span>Foo
-----

<span class="space"> </span><span class="space"> </span>Foo
<span class="space"> </span><span class="space"> </span>===
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo&lt;/h2&gt;
&lt;h2&gt;Foo&lt;/h2&gt;
&lt;h1&gt;Foo&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>Four spaces indent is too much:</p>
<div class="example" id="example-55">
<div class="examplenum">
<a href="#example-55">Example 55</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>Foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>---

<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>Foo
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;Foo
---

Foo
&lt;/code&gt;&lt;/pre&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>The setext heading underline can be indented up to three spaces, and
may have trailing spaces:</p>
<div class="example" id="example-56">
<div class="examplenum">
<a href="#example-56">Example 56</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span>----<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo&lt;/h2&gt;
</code></pre>
</div>
</div>
<p>Four spaces is too much:</p>
<div class="example" id="example-57">
<div class="examplenum">
<a href="#example-57">Example 57</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
---&lt;/p&gt;
</code></pre>
</div>
</div>
<p>The setext heading underline cannot contain internal spaces:</p>
<div class="example" id="example-58">
<div class="examplenum">
<a href="#example-58">Example 58</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
=<span class="space"> </span>=

Foo
---<span class="space"> </span>-
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
=<span class="space"> </span>=&lt;/p&gt;
&lt;p&gt;Foo&lt;/p&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>Trailing spaces in the content line do not cause a line break:</p>
<div class="example" id="example-59">
<div class="examplenum">
<a href="#example-59">Example 59</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo<span class="space"> </span><span class="space"> </span>
-----
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo&lt;/h2&gt;
</code></pre>
</div>
</div>
<p>Nor does a backslash at the end:</p>
<div class="example" id="example-60">
<div class="examplenum">
<a href="#example-60">Example 60</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo\
----
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo\&lt;/h2&gt;
</code></pre>
</div>
</div>
<p>Since indicators of block structure take precedence over
indicators of inline structure, the following are setext headings:</p>
<div class="example" id="example-61">
<div class="examplenum">
<a href="#example-61">Example 61</a>
</div>
<div class="column">
<pre><code class="language-markdown">`Foo
----
`

&lt;a<span class="space"> </span>title=&quot;a<span class="space"> </span>lot
---
of<span class="space"> </span>dashes&quot;/&gt;
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;`Foo&lt;/h2&gt;
&lt;p&gt;`&lt;/p&gt;
&lt;h2&gt;&amp;lt;a<span class="space"> </span>title=&amp;quot;a<span class="space"> </span>lot&lt;/h2&gt;
&lt;p&gt;of<span class="space"> </span>dashes&amp;quot;/&amp;gt;&lt;/p&gt;
</code></pre>
</div>
</div>
<p>The setext heading underline cannot be a <a href="#lazy-continuation-line">lazy continuation
line</a> in a list item or block quote:</p>
<div class="example" id="example-62">
<div class="examplenum">
<a href="#example-62">Example 62</a>
</div>
<div class="column">
<pre><code class="language-markdown">&gt;<span class="space"> </span>Foo
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;blockquote&gt;
&lt;p&gt;Foo&lt;/p&gt;
&lt;/blockquote&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-63">
<div class="examplenum">
<a href="#example-63">Example 63</a>
</div>
<div class="column">
<pre><code class="language-markdown">&gt;<span class="space"> </span>foo
bar
===
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;blockquote&gt;
&lt;p&gt;foo
bar
===&lt;/p&gt;
&lt;/blockquote&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-64">
<div class="examplenum">
<a href="#example-64">Example 64</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>Foo
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;Foo&lt;/li&gt;
&lt;/ul&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>A blank line is needed between a paragraph and a following
setext heading, since otherwise the paragraph becomes part
of the heading’s content:</p>
<div class="example" id="example-65">
<div class="examplenum">
<a href="#example-65">Example 65</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
Bar
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;Foo
Bar&lt;/h2&gt;
</code></pre>
</div>
</div>
<p>But in general a blank line is not required before or after
setext headings:</p>
<div class="example" id="example-66">
<div class="examplenum">
<a href="#example-66">Example 66</a>
</div>
<div class="column">
<pre><code class="language-markdown">---
Foo
---
Bar
---
Baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
&lt;h2&gt;Foo&lt;/h2&gt;
&lt;h2&gt;Bar&lt;/h2&gt;
&lt;p&gt;Baz&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Setext headings cannot be empty:</p>
<div class="example" id="example-67">
<div class="examplenum">
<a href="#example-67">Example 67</a>
</div>
<div class="column">
<pre><code class="language-markdown">
====
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;====&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Setext heading text lines must not be interpretable as block
constructs other than paragraphs.  So, the line of dashes
in these examples gets interpreted as a thematic break:</p>
<div class="example" id="example-68">
<div class="examplenum">
<a href="#example-68">Example 68</a>
</div>
<div class="column">
<pre><code class="language-markdown">---
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;hr<span class="space"> </span>/&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-69">
<div class="examplenum">
<a href="#example-69">Example 69</a>
</div>
<div class="column">
<pre><code class="language-markdown">-<span class="space"> </span>foo
-----
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;foo&lt;/li&gt;
&lt;/ul&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-70">
<div class="examplenum">
<a href="#example-70">Example 70</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
---
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo
&lt;/code&gt;&lt;/pre&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-71">
<div class="examplenum">
<a href="#example-71">Example 71</a>
</div>
<div class="column">
<pre><code class="language-markdown">&gt;<span class="space"> </span>foo
-----
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;blockquote&gt;
&lt;p&gt;foo&lt;/p&gt;
&lt;/blockquote&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>If you want a heading with <code>&gt; foo</code> as its literal text, you can
use backslash escapes:</p>
<div class="example" id="example-72">
<div class="examplenum">
<a href="#example-72">Example 72</a>
</div>
<div class="column">
<pre><code class="language-markdown">\&gt;<span class="space"> </span>foo
------
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;&amp;gt;<span class="space"> </span>foo&lt;/h2&gt;
</code></pre>
</div>
</div>
<p><strong>Compatibility note:</strong>  Most existing Markdown implementations
do not allow the text of setext headings to span multiple lines.
But there is no consensus about how to interpret</p>
<pre><code class="language-markdown">Foo
bar
---
baz
</code></pre>
<p>One can find four different interpretations:</p>
<ol>
<li>paragraph “Foo”, heading “bar”, paragraph “baz”</li>
<li>paragraph “Foo bar”, thematic break, paragraph “baz”</li>
<li>paragraph “Foo bar — baz”</li>
<li>heading “Foo bar”, paragraph “baz”</li>
</ol>
<p>We find interpretation 4 most natural, and interpretation 4
increases the expressive power of CommonMark, by allowing
multiline headings.  Authors who want interpretation 1 can
put a blank line after the first paragraph:</p>
<div class="example" id="example-73">
<div class="examplenum">
<a href="#example-73">Example 73</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo

bar
---
baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo&lt;/p&gt;
&lt;h2&gt;bar&lt;/h2&gt;
&lt;p&gt;baz&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Authors who want interpretation 2 can put blank lines around
the thematic break,</p>
<div class="example" id="example-74">
<div class="examplenum">
<a href="#example-74">Example 74</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
bar

---

baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
bar&lt;/p&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;p&gt;baz&lt;/p&gt;
</code></pre>
</div>
</div>
<p>or use a thematic break that cannot count as a <a href="#setext-heading-underline">setext heading
underline</a>, such as</p>
<div class="example" id="example-75">
<div class="examplenum">
<a href="#example-75">Example 75</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
bar
*<span class="space"> </span>*<span class="space"> </span>*
baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
bar&lt;/p&gt;
&lt;hr<span class="space"> </span>/&gt;
&lt;p&gt;baz&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Authors who want interpretation 3 can use backslash escapes:</p>
<div class="example" id="example-76">
<div class="examplenum">
<a href="#example-76">Example 76</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
bar
\---
baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
bar
---
baz&lt;/p&gt;
</code></pre>
</div>
</div>
<h2 id="indented-code-blocks" href="#indented-code-blocks" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.4</span>Indented code blocks
</h2>
<p>An <a id="indented-code-block" href="#indented-code-block" class="definition">indented code block</a> is composed of one or more
<a href="#indented-chunk">indented chunks</a> separated by blank lines.
An <a id="indented-chunk" href="#indented-chunk" class="definition">indented chunk</a> is a sequence of non-blank lines,
each indented four or more spaces. The contents of the code block are
the literal contents of the lines, including trailing
<a href="#line-ending">line endings</a>, minus four spaces of indentation.
An indented code block has no <a href="#info-string">info string</a>.</p>
<p>An indented code block cannot interrupt a paragraph, so there must be
a blank line between a paragraph and a following indented code block.
(A blank line is not needed, however, between a code block and a following
paragraph.)</p>
<div class="example" id="example-77">
<div class="examplenum">
<a href="#example-77">Example 77</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>a<span class="space"> </span>simple
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>indented<span class="space"> </span>code<span class="space"> </span>block
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;a<span class="space"> </span>simple
<span class="space"> </span><span class="space"> </span>indented<span class="space"> </span>code<span class="space"> </span>block
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>If there is any ambiguity between an interpretation of indentation
as a code block and as indicating that material belongs to a <a href="#list-items">list
item</a>, the list item interpretation takes precedence:</p>
<div class="example" id="example-78">
<div class="examplenum">
<a href="#example-78">Example 78</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span>-<span class="space"> </span>foo

<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ul&gt;
&lt;li&gt;
&lt;p&gt;foo&lt;/p&gt;
&lt;p&gt;bar&lt;/p&gt;
&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-79">
<div class="examplenum">
<a href="#example-79">Example 79</a>
</div>
<div class="column">
<pre><code class="language-markdown">1.<span class="space"> </span><span class="space"> </span>foo

<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>-<span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;ol&gt;
&lt;li&gt;
&lt;p&gt;foo&lt;/p&gt;
&lt;ul&gt;
&lt;li&gt;bar&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;/ol&gt;
</code></pre>
</div>
</div>
<p>The contents of a code block are literal text, and do not get parsed
as Markdown:</p>
<div class="example" id="example-80">
<div class="examplenum">
<a href="#example-80">Example 80</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>&lt;a/&gt;
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>*hi*

<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>-<span class="space"> </span>one
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;&amp;lt;a/&amp;gt;
*hi*

-<span class="space"> </span>one
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Here we have three chunks separated by blank lines:</p>
<div class="example" id="example-81">
<div class="examplenum">
<a href="#example-81">Example 81</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>chunk1

<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>chunk2
<span class="space"> </span><span class="space"> </span>
<span class="space"> </span>
<span class="space"> </span>
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>chunk3
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;chunk1

chunk2



chunk3
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Any initial spaces beyond four will be included in the content, even
in interior blank lines:</p>
<div class="example" id="example-82">
<div class="examplenum">
<a href="#example-82">Example 82</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>chunk1
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>chunk2
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;chunk1
<span class="space"> </span><span class="space"> </span>
<span class="space"> </span><span class="space"> </span>chunk2
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>An indented code block cannot interrupt a paragraph.  (This
allows hanging indents and the like.)</p>
<div class="example" id="example-83">
<div class="examplenum">
<a href="#example-83">Example 83</a>
</div>
<div class="column">
<pre><code class="language-markdown">Foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;Foo
bar&lt;/p&gt;
</code></pre>
</div>
</div>
<p>However, any non-blank line with fewer than four leading spaces ends
the code block immediately.  So a paragraph may occur immediately
after indented code:</p>
<div class="example" id="example-84">
<div class="examplenum">
<a href="#example-84">Example 84</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo
&lt;/code&gt;&lt;/pre&gt;
&lt;p&gt;bar&lt;/p&gt;
</code></pre>
</div>
</div>
<p>And indented code can occur immediately before and after other kinds of
blocks:</p>
<div class="example" id="example-85">
<div class="examplenum">
<a href="#example-85">Example 85</a>
</div>
<div class="column">
<pre><code class="language-markdown">#<span class="space"> </span>Heading
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
Heading
------
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
----
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h1&gt;Heading&lt;/h1&gt;
&lt;pre&gt;&lt;code&gt;foo
&lt;/code&gt;&lt;/pre&gt;
&lt;h2&gt;Heading&lt;/h2&gt;
&lt;pre&gt;&lt;code&gt;foo
&lt;/code&gt;&lt;/pre&gt;
&lt;hr<span class="space"> </span>/&gt;
</code></pre>
</div>
</div>
<p>The first line can be indented more than four spaces:</p>
<div class="example" id="example-86">
<div class="examplenum">
<a href="#example-86">Example 86</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>bar
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
bar
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Blank lines preceding or following an indented code block
are not included in it:</p>
<div class="example" id="example-87">
<div class="examplenum">
<a href="#example-87">Example 87</a>
</div>
<div class="column">
<pre><code class="language-markdown">
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Trailing spaces are included in the code block’s content:</p>
<div class="example" id="example-88">
<div class="examplenum">
<a href="#example-88">Example 88</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>foo<span class="space"> </span><span class="space"> </span>
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;foo<span class="space"> </span><span class="space"> </span>
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<h2 id="fenced-code-blocks" href="#fenced-code-blocks" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.5</span>Fenced code blocks
</h2>
<p>A <a id="code-fence" href="#code-fence" class="definition">code fence</a> is a sequence
of at least three consecutive backtick characters (<code>`</code>) or
tildes (<code>~</code>).  (Tildes and backticks cannot be mixed.)
A <a id="fenced-code-block" href="#fenced-code-block" class="definition">fenced code block</a>
begins with a code fence, indented no more than three spaces.</p>
<p>The line with the opening code fence may optionally contain some text
following the code fence; this is trimmed of leading and trailing
whitespace and called the <a id="info-string" href="#info-string" class="definition">info string</a>. If the <a href="#info-string">info string</a> comes
after a backtick fence, it may not contain any backtick
characters.  (The reason for this restriction is that otherwise
some inline code would be incorrectly interpreted as the
beginning of a fenced code block.)</p>
<p>The content of the code block consists of all subsequent lines, until
a closing <a href="#code-fence">code fence</a> of the same type as the code block
began with (backticks or tildes), and with at least as many backticks
or tildes as the opening code fence.  If the leading code fence is
indented N spaces, then up to N spaces of indentation are removed from
each line of the content (if present).  (If a content line is not
indented, it is preserved unchanged.  If it is indented less than N
spaces, all of the indentation is removed.)</p>
<p>The closing code fence may be indented up to three spaces, and may be
followed only by spaces, which are ignored.  If the end of the
containing block (or document) is reached and no closing code fence
has been found, the code block contains all of the lines after the
opening code fence until the end of the containing block (or
document).  (An alternative spec would require backtracking in the
event that a closing code fence is not found.  But this makes parsing
much less efficient, and there seems to be no real down side to the
behavior described here.)</p>
<p>A fenced code block may interrupt a paragraph, and does not require
a blank line either before or after.</p>
<p>The content of a code fence is treated as literal text, not parsed
as inlines.  The first word of the <a href="#info-string">info string</a> is typically used to
specify the language of the code sample, and rendered in the <code>class</code>
attribute of the <code>code</code> tag.  However, this spec does not mandate any
particular treatment of the <a href="#info-string">info string</a>.</p>
<p>Here is a simple example with backticks:</p>
<div class="example" id="example-89">
<div class="examplenum">
<a href="#example-89">Example 89</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
&lt;
<span class="space"> </span>&gt;
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;&amp;lt;
<span class="space"> </span>&amp;gt;
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>With tildes:</p>
<div class="example" id="example-90">
<div class="examplenum">
<a href="#example-90">Example 90</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~
&lt;
<span class="space"> </span>&gt;
~~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;&amp;lt;
<span class="space"> </span>&amp;gt;
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Fewer than three backticks is not enough:</p>
<div class="example" id="example-91">
<div class="examplenum">
<a href="#example-91">Example 91</a>
</div>
<div class="column">
<pre><code class="language-markdown">``
foo
``
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;&lt;code&gt;foo&lt;/code&gt;&lt;/p&gt;
</code></pre>
</div>
</div>
<p>The closing code fence must use the same character as the opening
fence:</p>
<div class="example" id="example-92">
<div class="examplenum">
<a href="#example-92">Example 92</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
aaa
~~~
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
~~~
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-93">
<div class="examplenum">
<a href="#example-93">Example 93</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~
aaa
```
~~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
```
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>The closing code fence must be at least as long as the opening fence:</p>
<div class="example" id="example-94">
<div class="examplenum">
<a href="#example-94">Example 94</a>
</div>
<div class="column">
<pre><code class="language-markdown">````
aaa
```
``````
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
```
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-95">
<div class="examplenum">
<a href="#example-95">Example 95</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~~
aaa
~~~
~~~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
~~~
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Unclosed code blocks are closed by the end of the document
(or the enclosing <a href="#block-quotes">block quote</a> or <a href="#list-items">list item</a>):</p>
<div class="example" id="example-96">
<div class="examplenum">
<a href="#example-96">Example 96</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-97">
<div class="examplenum">
<a href="#example-97">Example 97</a>
</div>
<div class="column">
<pre><code class="language-markdown">`````

```
aaa
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;
```
aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-98">
<div class="examplenum">
<a href="#example-98">Example 98</a>
</div>
<div class="column">
<pre><code class="language-markdown">&gt;<span class="space"> </span>```
&gt;<span class="space"> </span>aaa

bbb
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;blockquote&gt;
&lt;pre&gt;&lt;code&gt;aaa
&lt;/code&gt;&lt;/pre&gt;
&lt;/blockquote&gt;
&lt;p&gt;bbb&lt;/p&gt;
</code></pre>
</div>
</div>
<p>A code block can have all empty lines as its content:</p>
<div class="example" id="example-99">
<div class="examplenum">
<a href="#example-99">Example 99</a>
</div>
<div class="column">
<pre><code class="language-markdown">```

<span class="space"> </span><span class="space"> </span>
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;
<span class="space"> </span><span class="space"> </span>
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>A code block can be empty:</p>
<div class="example" id="example-100">
<div class="examplenum">
<a href="#example-100">Example 100</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Fences can be indented.  If the opening fence is indented,
content lines will have equivalent opening indentation removed,
if present:</p>
<div class="example" id="example-101">
<div class="examplenum">
<a href="#example-101">Example 101</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span>```
<span class="space"> </span>aaa
aaa
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-102">
<div class="examplenum">
<a href="#example-102">Example 102</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span>```
aaa
<span class="space"> </span><span class="space"> </span>aaa
aaa
<span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
aaa
aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-103">
<div class="examplenum">
<a href="#example-103">Example 103</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
<span class="space"> </span><span class="space"> </span><span class="space"> </span>aaa
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>aaa
<span class="space"> </span><span class="space"> </span>aaa
<span class="space"> </span><span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
<span class="space"> </span>aaa
aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Four spaces indentation produces an indented code block:</p>
<div class="example" id="example-104">
<div class="examplenum">
<a href="#example-104">Example 104</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>aaa
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;```
aaa
```
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Closing fences may be indented by 0-3 spaces, and their indentation
need not match that of the opening fence:</p>
<div class="example" id="example-105">
<div class="examplenum">
<a href="#example-105">Example 105</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
aaa
<span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-106">
<div class="examplenum">
<a href="#example-106">Example 106</a>
</div>
<div class="column">
<pre><code class="language-markdown"><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
aaa
<span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>This is not a closing fence, because it is indented 4 spaces:</p>
<div class="example" id="example-107">
<div class="examplenum">
<a href="#example-107">Example 107</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
aaa
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>```
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Code fences (opening and closing) cannot contain internal spaces:</p>
<div class="example" id="example-108">
<div class="examplenum">
<a href="#example-108">Example 108</a>
</div>
<div class="column">
<pre><code class="language-markdown">```<span class="space"> </span>```
aaa
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;&lt;code&gt;<span class="space"> </span>&lt;/code&gt;
aaa&lt;/p&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-109">
<div class="examplenum">
<a href="#example-109">Example 109</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~~~~
aaa
~~~<span class="space"> </span>~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;aaa
~~~<span class="space"> </span>~~
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Fenced code blocks can interrupt paragraphs, and can be followed
directly by paragraphs, without a blank line between:</p>
<div class="example" id="example-110">
<div class="examplenum">
<a href="#example-110">Example 110</a>
</div>
<div class="column">
<pre><code class="language-markdown">foo
```
bar
```
baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;foo&lt;/p&gt;
&lt;pre&gt;&lt;code&gt;bar
&lt;/code&gt;&lt;/pre&gt;
&lt;p&gt;baz&lt;/p&gt;
</code></pre>
</div>
</div>
<p>Other blocks can also occur before and after fenced code blocks
without an intervening blank line:</p>
<div class="example" id="example-111">
<div class="examplenum">
<a href="#example-111">Example 111</a>
</div>
<div class="column">
<pre><code class="language-markdown">foo
---
~~~
bar
~~~
#<span class="space"> </span>baz
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;h2&gt;foo&lt;/h2&gt;
&lt;pre&gt;&lt;code&gt;bar
&lt;/code&gt;&lt;/pre&gt;
&lt;h1&gt;baz&lt;/h1&gt;
</code></pre>
</div>
</div>
<p>An <a href="#info-string">info string</a> can be provided after the opening code fence.
Although this spec doesn’t mandate any particular treatment of
the info string, the first word is typically used to specify
the language of the code block. In HTML output, the language is
normally indicated by adding a class to the <code>code</code> element consisting
of <code>language-</code> followed by the language name.</p>
<div class="example" id="example-112">
<div class="examplenum">
<a href="#example-112">Example 112</a>
</div>
<div class="column">
<pre><code class="language-markdown">```ruby
def<span class="space"> </span>foo(x)
<span class="space"> </span><span class="space"> </span>return<span class="space"> </span>3
end
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code<span class="space"> </span>class=&quot;language-ruby&quot;&gt;def<span class="space"> </span>foo(x)
<span class="space"> </span><span class="space"> </span>return<span class="space"> </span>3
end
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-113">
<div class="examplenum">
<a href="#example-113">Example 113</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~~<span class="space"> </span><span class="space"> </span><span class="space"> </span><span class="space"> </span>ruby<span class="space"> </span>startline=3<span class="space"> </span>$%@#$
def<span class="space"> </span>foo(x)
<span class="space"> </span><span class="space"> </span>return<span class="space"> </span>3
end
~~~~~~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code<span class="space"> </span>class=&quot;language-ruby&quot;&gt;def<span class="space"> </span>foo(x)
<span class="space"> </span><span class="space"> </span>return<span class="space"> </span>3
end
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<div class="example" id="example-114">
<div class="examplenum">
<a href="#example-114">Example 114</a>
</div>
<div class="column">
<pre><code class="language-markdown">````;
````
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code<span class="space"> </span>class=&quot;language-;&quot;&gt;&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p><a href="#info-string">Info strings</a> for backtick code blocks cannot contain backticks:</p>
<div class="example" id="example-115">
<div class="examplenum">
<a href="#example-115">Example 115</a>
</div>
<div class="column">
<pre><code class="language-markdown">```<span class="space"> </span>aa<span class="space"> </span>```
foo
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;p&gt;&lt;code&gt;aa&lt;/code&gt;
foo&lt;/p&gt;
</code></pre>
</div>
</div>
<p><a href="#info-string">Info strings</a> for tilde code blocks can contain backticks and tildes:</p>
<div class="example" id="example-116">
<div class="examplenum">
<a href="#example-116">Example 116</a>
</div>
<div class="column">
<pre><code class="language-markdown">~~~<span class="space"> </span>aa<span class="space"> </span>```<span class="space"> </span>~~~
foo
~~~
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code<span class="space"> </span>class=&quot;language-aa&quot;&gt;foo
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<p>Closing code fences cannot have <a href="#info-string">info strings</a>:</p>
<div class="example" id="example-117">
<div class="examplenum">
<a href="#example-117">Example 117</a>
</div>
<div class="column">
<pre><code class="language-markdown">```
```<span class="space"> </span>aaa
```
</code></pre>
</div>
<div class="column">
<pre><code class="language-html">&lt;pre&gt;&lt;code&gt;```<span class="space"> </span>aaa
&lt;/code&gt;&lt;/pre&gt;
</code></pre>
</div>
</div>
<h2 id="html-blocks" href="#html-blocks" class="definition">
<a href="#TOC" class="toc-link"></a><span class="number">4.6</span>HTML blocks
</h2>
<p>An <a id="html-block" href="#html-block" class="definition">HTML block</a> is a group of lines that is treated
as raw HTML (and will not be escaped in HTML output).</p>
<p>There are seven kinds of <a href="#html-block">HTML block</a>, which can be defined by their
start and end conditions.  The block begins with a line that meets a
<a id="start-condition" href="#start-condition" class="definition">start condition</a> (after up to three spaces optional indentation).
It ends with the first subsequent line that meets a matching <a id="end-condition" href="#end-condition" class="definition">end
condition</a>, or the last line of the document, or the last line of
the <a href="#container-blocks">container block</a> containing the current HTML
block, if no line is encountered that meets the <a href="#end-condition">end condition</a>.  If
the first line meets both the <a href="#start-condition">start condition</a> and the <a href="#end-condition">end
condition</a>, the block will contain just that line.</p>
<ol>
<li>
<p><strong>Start condition:</strong>  line begins with the string <code>&lt;script</code>,
<code>&lt;pre</code>, or <code>&lt;style</code> (case-insensitive), followed by whitespace,
the string <code>&gt;</code>, or the end of the line.<br />
<strong>End condition:</strong>  line contains an end tag
<code>&lt;/script&gt;</code>, <code>&lt;/pre&gt;</code>, or <code>&lt;/style&gt;</code> (case-insensitive; it
need not match the start tag).</p>
</li>
<li>
<p><strong>Start condition:</strong> line begins with the string <code>&lt;!--</code>.<br />
<strong>End condition:</strong>  line contains the string <code>--&gt;</code>.</p>
</li>
<li>
<p><strong>Start condition:</strong> line begins with the string <code>&lt;?</code>.<br />
<strong>End condition:</strong> line contains the string <code>?&gt;</code>.</p>
</li>
<li>
<p><strong>Start condition:</strong> line begins with the string <code>&lt;!</code>
followed by an uppercase ASCII letter.<br />
<strong>End condition:</strong> line contains the character <code>&gt;</code>.</p>
</li>
<li>
<p><strong>Start condition:…
