 -----
 Doxia APT Enhancements
 -----
 Lukas Theussl
 Robert Scholte
 -----
 2013-04-06
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

Enhancements to the APT format
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  In the following we provide a list of differences/enhancements to the
  original {{{./apt-format.html}APT}} format that were incorporated in Doxia.
  Apart from some exceptions, these differences are usually
  'backwards-compatible'. That is, any document that gets correctly processed
  by Aptconvert should also
  be a valid Doxia input file and lead to identical results when processed
  by a Doxia parser.

%{toc|section=1|fromDepth=2|toDepth=2}

* {Paragraphs in list items}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  Contrary to the original APT parser, the Doxia APT parser does not
  put list items within paragraphs. Eg, the example given in the APT guide:

+---------------------------------------------------------------------------+
    * List item 1.
+---------------------------------------------------------------------------+

  will, for instance, produce the following html:

+---------------------------------------------------------------------------+
    <li>List item 1.</li>
+---------------------------------------------------------------------------+

  To get the same result as aptconvert, use

+---------------------------------------------------------------------------+
    *

      List item 1.
+---------------------------------------------------------------------------+

  which will produce:

+---------------------------------------------------------------------------+
    <li><p>List item 1.</p></li>
+---------------------------------------------------------------------------+


* {Table header cells}
~~~~~~~~~~~~~~~~~~~~~~

  Header cells are defined by an additional pipe character '|' at the beginning
  of the cell:

+---------------------------------------------------------------------------+
*-----------+-----------+
|| Header 1 || Header 2 |
*-----------+-----------+
| Cell 1    | Cell 2    |
*-----------+-----------+
+---------------------------------------------------------------------------+

  produces:

*-----------+-----------+
|| Header 1 || Header 2 |
*-----------+-----------+
| Cell 1    | Cell 2    |
*-----------+-----------+

* {Multi-lines cells in table}
~~~~~~~~~~~~~~~~~~~~~~

  Since 1.1, multi-lines cells are recognized with the character '\' at the end
  of the cells:

+---------------------------------------------------------------------------+
*-----------+-----------+
|| Header 1 || Header 2 |
*-----------+-----------+
| Cell\     | Cell 2    |
| 1         |           |
*-----------+-----------+
+---------------------------------------------------------------------------+

  produces:

*-----------+-----------+
|| Header 1 || Header 2 |
*-----------+-----------+
| Cell\     | Cell 2    |
| 1         |           |
*-----------+-----------+

* {Anchors}
~~~~~~~~~~~~~~~~~~~~~

** {Anchors for section titles}

  Contrary to the original APT format, section titles are <<not>> implicitly
  defined anchors. If you want an anchor for a section title you need to
  define it explicitly as such:

+---------------------------------------------------------------------------+
* {Anchors for section titles}
+---------------------------------------------------------------------------+

** {Anchor construction}

  Contrary to the original APT format, an anchor/link is <<not>> its text with
  all non alphanumeric characters stripped. Ideally, an anchor should be a valid
  Doxia id, ie it must begin with a letter (\[A\-Za\-z\]) and may be
  followed by any number of letters, digits (\[0\-9\]), hyphens ("\-"),
  underscores ("_"), colons (":"), and periods ("."). Any anchor that does not
  satisfy this pattern is transformed according to the following rules:

    * Any whitespace at the start and end is removed

    * If the first character is not a letter, prepend the letter 'a'

    * Any spaces are replaced with an underscore '_'

    * Any characters not matching the above pattern are stripped.

  Note in particular that case is preserved in this conversation and that APT
  anchors and links are case-sensitive. So the anchor for the section
  title in the previous example would be <<<Anchors_for_section_titles>>>.

* {Links}
~~~~~~~~~~~~~~~~~~~~~

  In <<Doxia-1.1>> the notion of a '<local>' link was introduced in addition to
  <internal> links and <external> links.

  * An <<internal>> link is a link to an anchor within the same source document.

    In the APT format used by <<Doxia-1.1>>, internal links have to be valid
    Doxia ids, as specified in the anchors section above.

    Note in particular that internal links in APT do <<not>> start with '#'.

  * A <<local>> link is a link to another document within the same site.

    In the APT format used by <<Doxia-1.1>>, local links <<have to>> start with
    either <<<./>>> or <<<../>>> to distinguish them from internal links. E.g.,

---
  {{{doc/standalone.html}Standalone}}
---

    is not valid, it should be

---
  {{{./doc/standalone.html}Standalone}}
---

    Note in particular that the following link

---
  {{{standalone.html}Standalone}}
---

    will be interpreted as an internal link (dots are valid characters in anchor names).
    Since you most likely meant to
    link to another source document, you should again prepend a "./".

  * An <<external>> link is a link that is neither local nor internal.

    An external link should be a valid {{{http://www.ietf.org/rfc/rfc2396.txt}URI}}.
    
  []  
    
  Anchors are always translated to a valid id, including escaping. In some situation this can cause issues, especially when referring to a javadoc-link.\
  Since Doxia 1.4 there is support for literal anchors, by using 2 hashed (##) instead of 1.
  This implies that the writer is responsible for using the right URL encoding!
  
---
  {{{../apidocs/groovyx/net/http/ParserRegistry.html##parseText(org.apache.http.HttpResponse)}ParserRegistry}}
---  

* {Figure extensions}
~~~~~~~~~~~~~~~~~~~~~

  Contrary to the original APT format, a figure name has to be given fully
  <<with>> extension. For instance:

+---------------------------------------------------------------------------+
[/home/joe/docs/mylogo.jpeg] Figure caption
+---------------------------------------------------------------------------+
