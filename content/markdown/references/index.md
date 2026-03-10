---
title: Doxia Markup Languages References
author: 
  - Lukas Theussl
  - Vincent Siveton
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

# Doxia Markup Languages References

The following table gives an overview of the markup languages currently supported by Doxia: 

- if a _Parser_ is available for a given format, it means that you can write your documentation in this language and Doxia can generate output from it,

- if a _Sink_ is available, it means you can generate output in this format.

The source directory is the directory under which Maven expects source documents in this format \(e.g. `src/site/apt/` for Apt\), the file extension is the default file extension, and the parser id is gives the unique identifier that is used by plexus to lookup the corresponding component. 

|Format|Short description|Parser<br />\(input\)|Sink<br />\(output\)|Source Directory|File Extension|Doxia Module|Parser Id|
|---|---|---|---|---|---|---|---|
|[Apt](./apt-format.html)|Almost Plain Text|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`apt`|`apt`|[`doxia-module-apt`](../doxia/doxia-modules/doxia-module-apt/)|`apt`|
|[AsciiDoc](https://asciidoctor.org/)|[Asciidoctor Converter Doxia Module](https://docs.asciidoctor.org/maven-tools/latest/site-integration/converter-module-setup-and-configuration/)|![Yes](../images/icon_success_sml.gif)|![No](../images/icon_error_sml.gif)|`asciidoc`|`adoc`, `asciidoc`|[`asciidoctor-converter-doxia-module`](https://github.com/asciidoctor/asciidoctor-maven-plugin#maven-site-integration)|`asciidoc`|
|[AsciiDoc](https://asciidoctor.org/)|[Asciidoctor Parser Doxia Module](https://docs.asciidoctor.org/maven-tools/latest/site-integration/parser-module-setup-and-configuration/)|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`asciidoc`|`adoc`, `asciidoc`|[`asciidoctor-parser-doxia-module`](https://github.com/asciidoctor/asciidoctor-maven-plugin#maven-site-integration)|`asciidoc`|
|[FML](./fml-format.html)|FAQ Markup Language|![Yes](../images/icon_success_sml.gif)|![No](../images/icon_error_sml.gif)|`fml`|`fml`|[`doxia-module-fml`](../doxia/doxia-modules/doxia-module-fml/)|`fml`|
|[Markdown](../modules/index.html#Markdown)|Markdown markup language|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`markdown`|`md`, `markdown`|[`doxia-module-markdown`](../doxia/doxia-modules/doxia-module-markdown/)|`markdown`|
|[Xdoc](./xdoc-format.html)|XML Documentation Format|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`xdoc`|`xml`|[`doxia-module-xdoc`](../doxia/doxia-modules/doxia-module-xdoc/)|`xdoc`|
|[XHTML](../modules/index.html#XHTML)|Extensible Hypertext Markup Language|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`xhtml`|`xhtml`|[`doxia-module-xhtml`](../doxia/doxia-modules/doxia-module-xhtml/)|`xhtml`|

Note some modules are not included per default with the site plugin. Have a look at the available modules here: [https://repo.maven.apache.org/maven2/org/apache/maven/doxia/](https://repo.maven.apache.org/maven2/org/apache/maven/doxia/).   

If you need to add module for the `maven-site-plugin` simply add it as a dependency of the plugin:

```unknown
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-site-plugin</artifactId>
  <version>3.2</version>
  <dependencies>
    <dependency>
      <groupId>org.apache.maven.doxia</groupId>
      <artifactId>doxia-module-markdown</artifactId>
      <version>1.3</version>
    </dependency>
  </dependencies>
</plugin>
```

# Doxia Formats \(deprecated\)

The following table gives an overview of the deprecated formats (which used to be supported mostly as Sink in former versions of Doxia): 

|Format|Short description|Doxia Module|Deprecated Since
|---|---|---|
|iText|iText PDF Library|[`doxia-module-itext`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-itext/)|1.11
|FO|XSL formatting objects \(XSL-FO\)|[`doxia-module-fo`](../doxia-archives/doxia-1.11.1doxia-modules/doxia-module-fo/)|1.11
|LaTeX|LaTeX typesetting system|[`doxia-module-latex`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-latex/)|1.11
|RTF|Microsoft Rich Text Format|[`doxia-module-rtf`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-rtf/)|1.11
|Confluence|Confluence Enterprise Wiki|[`doxia-module-confluence`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-confluence/)|2.0
|Simplified DocBook|Simplified DocBook XML Standard|[`doxia-module-docbook-simple`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-docbook-simple/)|2.0
|TWiki|TWiki Structured Wiki|[`doxia-module-twiki`](../doxia-archives/doxia-1.11.1/doxia-modules/doxia-module-twiki/)|2.0
