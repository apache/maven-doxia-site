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
|[Confluence](../modules/index.html#Confluence)|Confluence Enterprise Wiki|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)<sup>*</sup>|`confluence`|`confluence`|[`doxia-module-confluence`](../doxia/doxia-modules/doxia-module-confluence/)|`confluence`|
|[Simplified DocBook](../modules/index.html#Simplified_DocBook)|Simplified DocBook XML Standard|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`docbook`|`xml`|[`doxia-module-docbook-simple`](../doxia/doxia-modules/doxia-module-docbook-simple/)|`docbook`|
|[FML](./fml-format.html)|FAQ Markup Language|![Yes](../images/icon_success_sml.gif)|![No](../images/icon_error_sml.gif)|`fml`|`fml`|[`doxia-module-fml`](../doxia/doxia-modules/doxia-module-fml/)|`fml`|
|[Markdown](../modules/index.html#Markdown)<sup>**</sup>|Markdown markup language|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)<sup>****</sup>|`markdown`|`md`, `markdown`<sup>***</sup>|[`doxia-module-markdown`](../doxia/doxia-modules/doxia-module-markdown/)|`markdown`|
|[TWiki](../modules/index.html#TWiki)<sup>*</sup>|TWiki Structured Wiki|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`twiki`|`twiki`|[`doxia-module-twiki`](../doxia/doxia-modules/doxia-module-twiki/)|`twiki`|
|[Xdoc](./xdoc-format.html)|XML Documentation Format|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`xdoc`|`xml`|[`doxia-module-xdoc`](../doxia/doxia-modules/doxia-module-xdoc/)|`xdoc`|
|[XHTML](../modules/index.html#XHTML)|Extensible Hypertext Markup Language|![Yes](../images/icon_success_sml.gif)|![Yes](../images/icon_success_sml.gif)|`xhtml`|`xhtml`|[`doxia-module-xhtml`](../doxia/doxia-modules/doxia-module-xhtml/)|`xhtml`|

Note some modules are not included per default with the site plugin. Have a look at the available modules here: [https://repo.maven.apache.org/maven2/org/apache/maven/doxia/](https://repo.maven.apache.org/maven2/org/apache/maven/doxia/).   

If you need to add module for the maven site plugin simply add it as a dependency of the plugin 

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

<sup>*</sup> Since Doxia 1\.1 

<sup>**</sup> Since Doxia 1\.3 

<sup>***</sup> Since Doxia 1\.7 

<sup>****</sup> Since Doxia 1\.12\.0 

# Doxia Page Output Format \(deprecated\)

The following table gives an overview of the output-only page-oriented deprecated \(in Doxia 1\.11\) formats: 

|Format|Short description|Doxia Module|
|---|---|---|
|[iText](../modules/index.html#iText)|iText PDF Library|[`doxia-module-itext`](../doxia/doxia-modules/doxia-module-itext/)|
|[FO](../modules/index.html#FO)<sup>*</sup>|XSL formatting objects \(XSL-FO\)|[`doxia-module-fo`](../doxia/doxia-modules/doxia-module-fo/)|
|[LaTeX](../modules/index.html#LaTeX)|LaTeX typesetting system|[`doxia-module-latex`](../doxia/doxia-modules/doxia-module-latex/)|
|[RTF](../modules/index.html#RTF)|Microsoft Rich Text Format|[`doxia-module-rtf`](../doxia/doxia-modules/doxia-module-rtf/)|

