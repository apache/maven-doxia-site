 ------
 Doxia Macros Guide
 ------
 Vincent Siveton
 ------
 2009-03-02
 ------

~~ Licensed to the Apache Software Foundation (ASF) under one
~~ or more contributor license agreements.  See the NOTICE file
~~ distributed with this work for additional information
~~ regarding copyright ownership.  The ASF licenses this file
~~ to you under the Apache License, Version 2.0 (the
~~ "License"); you may not use this file except in compliance
~~ with the License.  You may obtain a copy of the License at
~~
~~   http://www.apache.org/licenses/LICENSE-2.0
~~
~~ Unless required by applicable law or agreed to in writing,
~~ software distributed under the License is distributed on an
~~ "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
~~ KIND, either express or implied.  See the License for the
~~ specific language governing permissions and limitations
~~ under the License.

~~ NOTE: For help with the syntax of this file, see:
~~ http://maven.apache.org/doxia/references/apt-format.html

Doxia Macros Guide

 The Doxia <Core> includes macro mechanisms to facilitate the documentation writing.

 Macros are currently only supported for APT, Xdoc and FML formats. Starting with Doxia 1.7 (maven-site-plugin 3.5),
 macros are also supported for XHTML and Markdown.
 Macros are not (and probably will never be) supported by Confluence, Docbook and Twiki modules.

 A macro in an APT source file is a <<non-indented>> line that looks like this:

+----
%{macro_name|param1=value1|param2=value2|...}
+----

 An Xdoc or FML macro has the following syntax:

+----
<macro name="macro_name">
  <param name="param1" value="value1"/>
  <param name="param2" value="value2"/>
  ...
</macro>
+----

 Since Doxia 1.7, an XHTML or Markdown macro has the following syntax:

+----
<!-- MACRO{macro_name|param1=value1|param2=value2|...} -->
+----

 As of Doxia 1.7, the following macros are available:

%{toc|section=1|fromDepth=2|toDepth=2}

* {Echo Macro}

 The <Echo> macro is a very simple macro: it prints out the key and value of any supplied parameters.
 For instance, in an APT file, you could write:

+----
%{echo|param1=value1|param2=value2}
+----

 Similarly, it will be for xdoc file:

+----
<macro name="echo">
  <param name="param1" value="value1"/>
  <param name="param2" value="value2"/>
</macro>
+----

  and it will output

+----
  param1 ---> value1
  param2 ---> value2
+----

* {Snippet Macro}

 The <Snippet> macro is a very useful macro: it prints out the content of a file or a URL.
 For instance, in an APT file, you could write:

+----
%{snippet|id=myid|url=http://myserver/path/to/file.txt}
+----

 In a xdoc file, it will be:

+----
<macro name="snippet">
  <param name="id" value="myid"/>
  <param name="url" value="http://myserver/path/to/file.txt"/>
</macro>
+----

 The <<<id>>> parameter is not required if you want to include the entire file.
 If you want to include only a part of a file, you should add start and end demarcators:
 any line (typically a comment) that contains the strings "<<<START>>>", "<<<SNIPPET>>>"
 and "<<<myid>>>" (where <<<myid>>> is the <<<id>>> of the snippet) is a start demarcator,
 and similarly "<<<END SNIPPET myid>>>" denotes the end of the snippet to include. For example:

  * Start and end snippets in a Java file

+----
public class MyClass
{
    // START SNIPPET: myid
    public static void main( String[] args ) throws Exception
    {
        ...
    }
    // END SNIPPET: myid
}
+----

  * Start and end snippets in a XML file

+----
<project>
...
  <build>
    <plugins>
<!-- START SNIPPET: myid -->
      <plugin>
        ...
      </plugin>
<!-- END SNIPPET: myid -->
    </plugins>
  </build>
</project>
+----

  []

*-----------+--------------+
|| Parameter || Description  |
*-----------+--------------+
| id        | The id of the snippet to include.
|           | If omitted the whole file/url will be included (since Doxia 1.1).
*-----------+--------------+
| url       | The path of the URL to include.
*-----------+--------------+
| file      | The path of the file to include (since doxia-1.0-alpha-9).
*-----------+--------------+
| verbatim  | If the content should be output as verbatim escaped text. If this is set to <<<false>>> then the content
|           | of the snippet will not be escaped. This means that you can use it like Server-Side Includes on a
|           | webserver. Default value is <<<true>>>.
*-----------+--------------+
| encoding  | The encoding of the file to read (since Doxia 1.6). If omitted the default JVM encoding will be used.
*-----------+--------------+

* {TOC Macro}

 The <TOC> macro prints a Table Of Content of a document. It is useful if you have several sections and
 subsections in your document. For instance, in an APT file, you could write:

+----
%{toc|section=2|fromDepth=2|toDepth=3}
+----

 This displays a TOC for the second section in the document, including all
 subsections (depth 2) and  sub-subsections (depth 3).

  <<Note>> that in Doxia, apt section titles are not implicit anchors
  (see {{{../references/doxia-apt.html}Enhancements to the APT format}}), so you need
  to insert explicit anchors for links to work!

 In a xdoc file, it will be:

+----
<macro name="toc">
  <param name="section" value="2"/>
  <param name="fromDepth" value="0"/>
  <param name="toDepth" value="4"/>
</macro>
+----

*-----------+--------------+
|| Parameter || Description  |
*-----------+--------------+
| section   | Display a TOC for the specified section only, or all sections if 0. Positive int, not mandatory, 0 by default.
*-----------+--------------+
| fromDepth | Minimum section depth to include in the TOC (sections are depth 1, sub-sections depth 2, etc.). Positive int, not mandatory, 0 by default.
*-----------+--------------+
| toDepth   | Maximum section depth to include in the TOC. Positive int, not mandatory, 5 by default.
*-----------+--------------+

 From <<Doxia 1.1.1>> on you may also specify any of the html base attributes
 (<i.e.> any of <<<id>>>, <<<class>>>, <<<style>>>, <<<lang>>>, <<<title>>>) as parameters, e.g.:

+----
%{toc|class=myTOC}
+----

 This can be used for styling the TOC via css.

* {SWF Macro}

 The <Swf> macro prints Shockwave Flash assets in the documentation. For instance, in an APT file,
 you could write:

+----
%{swf|src=swf/myfile.swf|id=MyMovie|width=600|height=200}
+----

 In a xdoc file, it will be:

+----
<macro name="swf">
  <param name="src" value="swf/myfile.swf"/>
  <param name="id" value="MyMovie"/>
  <param name="width" value="600"/>
  <param name="height" value="200"/>
</macro>
+----

*-----------+--------------+
|| Parameter || Description  |
*-----------+--------------+
| src       | Specifies the location (URL) of the movie to be loaded.
*-----------+--------------+
| id        | Identifies the Flash movie to the host environment (a web browser, for example) so that it can be referenced using a scripting language.
*-----------+--------------+
| width     | Specifies the width of the movie in either pixels or percentage of browser window.
*-----------+--------------+
| height    | Specifies the height of the movie in either pixels or percentage of browser window.
*-----------+--------------+
| quality   | Possible values: low, high, autolow, autohigh, best.
*-----------+--------------+
| menu      | True displays the full menu, allowing the user a variety of options to enhance or control playback. False displays a menu that contains only the Settings option and the About Flash option.
*-----------+--------------+
| loop      | Possible values: true, false. Specifies whether the movie repeats indefinitely or stops when it reaches the last frame. The default value is true if this attribute is omitted.
*-----------+--------------+
| play      | Possible values: true, false. Specifies whether the movie begins playing immediately on loading in the browser. The default value is true if this attribute is omitted.
*-----------+--------------+
| version   | Specifies the width of the movie in either pixels or percentage of browser window.
*-----------+--------------+
| allowScript | Specifies the width of the movie in either pixels or percentage of browser window.
*-----------+--------------+

 For more information, see the {{{./swf-macro.html}SWF Macro}} page.

* {SSI Macro}

 Since Doxia 1.7, the <SSI> macro prints a server side include. For instance, in an APT file,
 you could write:

+----
%{ssi|function=include|file=included-file.html}
+----

 In a xdoc file, it will be:

+----
<macro name="ssi">
  <param name="function" value="include"/>
  <param name="file" value="included-file.html"/>
</macro>
+----

*-----------+--------------+
|| Parameter || Description  |
*-----------+--------------+
| function  | The SSI function to insert.
*-----------+--------------+
| <any>     | Parameter that will be added to the SSI directive.
*-----------+--------------+
