---
title: Writing Books in Doxia
author: 
  - Trygve Laugstol
  - Vincent Siveton
date: 2012-04-13
---

<!-- Licensed to the Apache Software Foundation (ASF) under one-->
<!-- or more contributor license agreements.  See the NOTICE file-->
<!-- distributed with this work for additional information-->
<!-- regarding copyright ownership.  The ASF licenses this file-->
<!-- to you under the Apache License, Version 2.0 (the-->
<!-- "License"); you may not use this file except in compliance-->
<!-- with the License.  You may obtain a copy of the License at-->
<!---->
<!--   http://www.apache.org/licenses/LICENSE-2.0-->
<!---->
<!-- Unless required by applicable law or agreed to in writing,-->
<!-- software distributed under the License is distributed on an-->
<!-- "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY-->
<!-- KIND, either express or implied.  See the License for the-->
<!-- specific language governing permissions and limitations-->
<!-- under the License.-->

# Introduction

Doxia allows you to write books like user manuals and guides in any format supported by Doxia\. You can include the manuals directly in your generated site with links to the off\-line friendly formats like XDoc, PDF, RTF and LaTeX\.

The Xdoc output which has been rendered into this site can be viewed [here](../doxia-example-book/index.html)\.

The generated PDF is [here](../doxia-example-book/doxia-example-book.pdf) and the generated RTF [here](../doxia-example-book/doxia-example-book.rtf)\.

## How It Works

The only thing you need in addition to the content files is a simple book descriptor which specifies the ordering of the sections and the names for the chapters\.

## Creating a Book Descriptor

An XML file describes the layout of the book\.

A sample is given below:

<!-- MACRO{snippet|id=example|file=content/books/example-book.xml} -->
## Configuring Doxia Book Maven Plugin

This example illustrates how to configure the Doxia Book Maven Plugin\. It will render the book in three different formats\. By default the output will be under `target/generated-site/<format>/<book id> `\.

The currently supported format ids are: `xdoc`, `pdf`, `latex`, `rtf`, `xhtml`, `doc-book`

A sample `pom.xml` is given below:

<!-- MACRO{snippet|id=configuration|file=pom.xml} -->