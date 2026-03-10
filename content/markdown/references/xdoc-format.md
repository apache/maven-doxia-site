---
title: The Xdoc format
author: 
  - Lukas Theussl
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
-->

# Content

<a id="Content"></a> 

<!-- MACRO{toc|fromDepth=1|toDepth=2} -->

# The XDoc format

<a id="The_XDoc_format"></a> <a id="Overview"></a> 
## Overview

An &apos;xdoc&apos; is an XML document conforming to a small and simple set of tags. Xdoc was the primary documentation format in [Maven 1](http://maven.apache.org/maven-1.x/), Maven 2 largely replaced this by [Apt](apt-format.html), but xdoc is still supported. 

Historically, the xdoc format can be traced back to the [Anakia](http://velocity.apache.org/anakia/devel/) format, as once used by the [Apache Jakarta](http://jakarta.apache.org/) project then moved to [Velocity](http://velocity.apache.org/). 

The Maven 1 Xdoc plugin introduced a few additions to the Anakia format, they are highlighted in the [plugin](http://maven.apache.org/maven-1.x/plugins/xdoc/reference/xdocs.html) documentation. 

<a id="The_XDoc_xsd"></a> 
## The XDoc xsd

The full documentation is available [here](../doxia/doxia-modules/doxia-module-xdoc/xsddoc/index.html). 

<a id="XDoc_Sample"></a> 
## XDoc Sample

The following is a sample XDoc document: 

```unknown
<?xml version="1.0" encoding="UTF-8"?>
<document xmlns="http://maven.apache.org/XDOC/2.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/XDOC/2.0 http://maven.apache.org/xsd/xdoc-2.0.xsd">

  <properties>
    <title>Page Title</title>
    <author email="user@company.com">John Doe</author>
  </properties>

  <!-- Optional HEAD element, which is copied as is into the XHTML <head> element -->
  <head>
    <meta ... />
  </head>

  <body>

    <!-- The body of the document contains a number of sections -->
    <section name="section 1">

      <!-- Within sections, any XHTML can be used -->
      <p>Hi!</p>

      <!-- in addition to XHTML, any number of subsections can be within a section -->
      <subsection name="subsection 1">
        <p>Subsection!</p>
      </subsection>

    </section>

    <section name="other section">

      <!-- You can also include preformatted source blocks in the document -->
      <source>
code line 1
code line 2
      </source>

    </section>

  </body>

</document>
```

<a id="The_source_tag"></a> 
## The &lt;source&gt; tag

`<source>` tags are special. Anything within this tag is rendered within a &quot;verbatim box&quot; as pre-formatted text. If you are embedding other XML/XHTML markup within the source tags, then you need to place a CDATA section within the source section. Example: 

```unknown
<source><![CDATA[ content here <a href="">foo</a>]]></source>
```

<a id="Additional_sectioning"></a> 
## Additional sectioning

Doxia will produce `<h2>` and `<h3>` headings for `<section>` and `<subsection>` elements, respectively. It is therefore perfectly valid to put some sub-headings \(`<h4>`, `<h5>`, `<h6>`\) inside a subsection. For instance, 

```unknown
<h4>A subsubsection</h4>
```

will produce: 

#### A subsubsection

<a id="Referencing_sections_and_subsections"></a> 
## Referencing sections and subsections

The core doxia modules do **not** construct anchors from section/subsection names. If you want to reference a section, you should either provide an explicit anchor: 

```unknown
<a name="Section1"/>
<section name="Section">

  <a name="SubSection1"/>
  <subsection name="SubSection">
  </subsection>

</section>
```

or use an `id` attribute for section and subsections \(note that `id`&apos;s have to be unique within one xdoc source document\): 

```unknown
<section name="Section" id="Section1">

  <subsection name="SubSection" id="SubSection1">
  </subsection>

</section>
```

**Note** that this differs from previous behavior, where anchors were constructed from section/subsection names, replacing special characters by underscores. This behavior presents two shortcomings: 

- If two sections or subsections have identical names \(within one source document\), you will get an ambiguity when referencing them. Also the resulting html document will not be valid XHTML. For other output formats \(eg pdf\), it might even be impossible to generate the target document. 

- For long section titles, this leads to rather cumbersome anchor names. 

If automatic anchor generation is desired for a particular output format, it should be implemented / overridden by the corresponding low-level Sink. 

# Validation

<a id="Validation"></a> 

Doxia is able to validate your xdoc files as described [here](../doxia/doxia-modules/doxia-module-xdoc/using-xdoc-xsd.html). 

Here is a list of common mistakes to be aware of: 

<a id="Dont_nest_block_level_elements"></a> 
## Don&apos;t nest block level elements

Wrong:

```unknown
<p>
  Here's a list:
  <ul>
    <li>item 1</li>
    <li>item 2</li>
  </ul>
  of things to do.
</p>
```

Correct:

```unknown
<p>
  Here's a list:
</p>
<ul>
  <li>item 1</li>
  <li>item 2</li>
</ul>
<p>
  of things to do.
</p>
```

Typical block level elements are list elements, `<table>`, `<source>`, `<div>`, `<p>` and `<pre>`. 

<a id="Put_inline_elements_inside_block_level_elements"></a> 
## Put inline elements inside block level elements

Wrong:

```unknown
<section name="Downloads">
  <a href="downloads.html">Downloads</a>
</section>
```

Correct:

```unknown
<section name="Downloads">
  <p>
    <a href="downloads.html">Downloads</a>
  </p>
</section>
```

Typical inline elements are `<a>`, `<strong>`, `<code>`, `<font>`, `<br>` and `<img>`. 

<a id="Right_order_of_elements_in_properties"></a> 
## Right order of elements in &lt;properties&gt;

The `<title>` element has to come before `<author>`. 

<a id="Dont_put_source_inside_paragraphs"></a> 
## Don&apos;t put &lt;source&gt; inside paragraphs

Wrong:

```unknown
<p>
  The following command executes the program:
  <source>java -jar CoolApp.jar</source>
</p>
```

Correct:

```unknown
<p>
  The following command executes the program:
</p>
<source>java -jar CoolApp.jar</source>
```

However, you may put `<source>` elements inside list items or table rows. 

