[JavaScript preprocessor](http://js-preprocessor.com)
===============
Minimal preprocessing with `/*@include*/`

Previously used `/*>`. Converted to handle the more verbose `@include` to be compatible with the [preprocess](https://github.com/jsoverson/preprocess) npm library.

Usage
----
`jspp input > output`

Example
----
<table><tr>
<td>main.js
<pre>/*@include script.js */

var style = "/*@include css/style.css */";</pre></td>
<td>css/style.css
<pre>html, body {margin:0; padding:0}
/*@include http://js-preprocessor.com/example/css/child.css */
.my-style {background: #fffacc}
</pre></td>
<td><br/>css/child.css
<pre>.i-am-child {}
</pre></td>
</tr><tr>
<td><br/>script.js
<pre>var my_script;</pre></td>
</tr></table>

    $ jspp example/main.js
    var my_script;
    
    var style = "html, body {margin:0; padding:0}\
    .i-am-child {}\
    .my-style {background: #fffacc}"

JavaScript preprocessor in a wild:
[GitHub Live Preview](http://github.com/NV/github-live-preview),
[Faviconize Google](http://github.com/NV/faviconize-google.js),
[Nice Alert](http://github.com/NV/nice-alert.js).

Installation
----
[Ruby gem](http://rubygems.org/gems/jspp)

    $ gem install jspp

Testing
----

The included spec files can be run with `ruby spec/jspp_spec.rb`. As of 2014-10-21 the tests all fail due to language errors but the system appears to work when run on the example file.

Why reinvent the wheel?
----
[Sprockets](http://github.com/sstephenson/sprockets) can't include non-JS files.
JS preprocessor can.

[Juicer](http://github.com/cjohansen/juicer) don't have any analogies to `"/*> some_file */"`.
I.e., it can't include files as multiline string.
