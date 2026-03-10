---
title: Frequently Asked Questions
---

<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
--><a id="top"></a>
# Frequently Asked Questions

1. [How to handle style in the APT markup language?](#How_to_handle_style_in_the_APT_markup_language)
1. [How to export in PDF?](#How_to_export_in_PDF)
1. [Why XML based sinks don&apos;t generate nicely formatted documents?](#Why_XML_based_sinks_don_t_generate_nicely_formatted_documents)
1. [Where are the Maven Doxia XSD schemas files?](#doxia-xsd)
1. [How to define character entities in Doxia XML files with XSD?](#doxia-character-entities)
<dl>
<a id="How_to_handle_style_in_the_APT_markup_language"></a><dt>How to handle style in the APT markup language?</dt>
<dd> 

APT does not support style. If you need more control you should use <a href="references/xdoc-format.html">xdoc</a> instead. 

<a href="#top">[top]</a>

***

</dd>
<a id="How_to_export_in_PDF"></a><dt>How to export in PDF?</dt>
<dd> 

There are two modules available that can be used to generate pdf output: an <a href="/doxia/doxia/doxia-modules/doxia-module-itext/">iText module</a> that uses the <a href="http://www.lowagie.com/iText/" class="externalLink">iText</a> framework, and a <a href="/doxia/doxia/doxia-modules/doxia-module-fo/">FO</a> module, that can be used e.g. in conjunction with <a href="http://xmlgraphics.apache.org/fop/" class="externalLink">Apache FOP</a> to generate a pdf. Unfortunately, the iText team has discontinued the XML to PDF functionalities, so probably only the fo module is going to be supported in the future. 

For Maven there is a <a href="/plugins/maven-pdf-plugin/">pdf plugin</a> available. 

<a href="#top">[top]</a>

***

</dd>
<a id="Why_XML_based_sinks_don_t_generate_nicely_formatted_documents"></a><dt>Why XML based sinks don't generate nicely formatted documents?</dt>
<dd> 

We decided to keep pretty printing out of the core modules. So, XML based sinks like Xdoc or XHTML are intentionally unformatted. You could always do this after the document generation or directly by creating a specialized end-user sink (see <a href="https://issues.apache.org/jira/browse/DOXIA-255" class="externalLink">DOXIA-255</a>). 

<a href="#top">[top]</a>

***

</dd>
<a id="doxia-xsd"></a><dt>Where are the Maven Doxia XSD schemas files?</dt>
<dd> 

The Doxia XSD files are located here: 

<dl>

<dt>Xdoc XSD 2.0</dt>

<dd><a href="/xsd/xdoc-2.0.xsd">https://maven.apache.org/xsd/xdoc-2.0.xsd</a></dd>

<dt>FML XSD 1.0.1</dt>

<dd><a href="/xsd/fml-1.0.1.xsd">https://maven.apache.org/xsd/fml-1.0.1.xsd</a></dd>

<dt>Book XSD 1.0</dt>

<dd><a href="/xsd/book-1.0.0.xsd">https://maven.apache.org/xsd/book-1.0.0.xsd</a></dd>

<dt>Document XSD 1.0.1</dt>

<dd><a href="/xsd/document-1.0.1.xsd">https://maven.apache.org/xsd/document-1.0.1.xsd</a></dd>

<dt>Decoration XSD 1.0</dt>

<dd><a href="/xsd/decoration-1.0.0.xsd">https://maven.apache.org/xsd/decoration-1.0.0.xsd</a></dd>

</dl>

Your favorite IDE probably supports XSD schema's for Xdoc and FML files. You need to specify the following: <pre><code>&lt;document xmlns=&quot;http://maven.apache.org/XDOC/2.0&quot;
  xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
  xsi:schemaLocation=&quot;http://maven.apache.org/XDOC/2.0 http://maven.apache.org/xsd/xdoc-2.0.xsd&quot;&gt;
  ...
&lt;/document&gt;</code></pre> <pre><code>&lt;faqs xmlns=&quot;http://maven.apache.org/FML/1.0.1&quot;
  xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
  xsi:schemaLocation=&quot;http://maven.apache.org/FML/1.0.1 http://maven.apache.org/xsd/fml-1.0.1.xsd&quot;&gt;
  ...
&lt;/faqs&gt;</code></pre> <pre><code>&lt;book xmlns=&quot;http://maven.apache.org/BOOK/1.0.0&quot;
  xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
  xsi:schemaLocation=&quot;http://maven.apache.org/BOOK/1.0.0 http://maven.apache.org/xsd/book-1.0.0.xsd&quot;&gt;
  ...
&lt;/book&gt;</code></pre> <pre><code>&lt;document xmlns=&quot;http://maven.apache.org/DOCUMENT/1.0.1&quot;
  xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
  xsi:schemaLocation=&quot;http://maven.apache.org/DOCUMENT/1.0.1 http://maven.apache.org/xsd/document-1.0.1.xsd&quot;
  outputName=&quot;...&quot;&gt;
  ...
&lt;/document&gt;</code></pre> <pre><code>&lt;project xmlns=&quot;http://maven.apache.org/DECORATION/1.0.0&quot;
  xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
  xsi:schemaLocation=&quot;http://maven.apache.org/DECORATION/1.0.0 http://maven.apache.org/xsd/decoration-1.0.0.xsd&quot;&gt;
  ...
&lt;/project&gt;</code></pre> 

<b>Note</b>: for performance reasons, all XSDs/DTDs use a cache in ${java.io.tmpdir}. 

<a href="#top">[top]</a>

***

</dd>
<a id="doxia-character-entities"></a><dt>How to define character entities in Doxia XML files with XSD?</dt>
<dd> 

Since it is not possible to define character entity references (like &amp;copy;) in XSDs (unlike DTDs), each XML file should have a &lt;!DOCTYPE&gt; to define the character entity set. 

For instance, you could add the following in your Xdoc XML files to be similar to XHTML 1.0 Transitional dtd: <pre><code>&lt;!DOCTYPE document [
  &lt;!-- These are the entity sets for ISO Latin 1 characters for the XHTML --&gt;
  &lt;!ENTITY % HTMLlat1 PUBLIC &quot;-//W3C//ENTITIES Latin 1 for XHTML//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml-lat1.ent&quot;&gt;
  %HTMLlat1;
  &lt;!-- These are the entity sets for special characters for the XHTML --&gt;
  &lt;!ENTITY % HTMLsymbol PUBLIC &quot;-//W3C//ENTITIES Symbols for XHTML//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml-symbol.ent&quot;&gt;
  %HTMLsymbol;
  &lt;!-- These are the entity sets for symbol characters for the XHTML --&gt;
  &lt;!ENTITY % HTMLspecial PUBLIC &quot;-//W3C//ENTITIES Special for XHTML//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml-special.ent&quot;&gt;
  %HTMLspecial;
]&gt;
&lt;document xmlns=&quot;http://maven.apache.org/XDOC/2.0&quot;
xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
xsi:schemaLocation=&quot;http://maven.apache.org/XDOC/2.0 http://maven.apache.org/xsd/xdoc-2.0.xsd&quot;&gt;
...
&lt;/document&gt;</code></pre> 

<b>Note</b>: if CDATA is used to specify entity, Doxia will replace &amp; by &amp;amp; (i.e &quot;&lt;![CDATA[&amp;iexcl;]]&gt;&quot; becomes &quot;&amp;amp;iexcl;&quot;). 

<a href="#top">[top]</a>

</dd>
</dl>