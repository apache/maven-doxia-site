<?xml version="1.0" encoding="UTF-8"?>

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

<document xmlns="http://maven.apache.org/XDOC/2.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/XDOC/2.0 http://maven.apache.org/xsd/xdoc-2.0.xsd">

  <properties>
    <title>The FML (FAQ Markup Language) format</title>
    <author email="ltheussl_AT_apache_DOT_org">Lukas Theussl</author>
  </properties>

  <body>
    <section name="The FML format">
      <subsection name="Overview">
        <p>
          An 'fml' (FAQ Markup Language) is an XML document conforming to a small and simple set of tags.
          The format was first used in the <a href="http://maven.apache.org/maven-1.x/">Maven 1</a>,
          version of the <a href="http://maven.apache.org/maven-1.x/plugins/faq/">FAQ plugin</a>.
        </p>
      </subsection>

      <subsection name="The FML format">
        <p>
          Below the root element <code>faqs</code> there are one or more <code>part</code> elements.
          Each <code>part</code> element has a <code>title</code> and contains one or more <code>faq</code> elements.
          Each <code>faq</code> element has a <code>question</code> and an <code>answer</code> element.
          The contents of <code>title</code>, <code>question</code> and <code>answer</code> are parsed with the <a href="xdoc-format.html">XDoc parser</a>.
          The full documentation is available at <a href="../doxia/doxia-modules/doxia-module-fml/xsddoc/index.html">here</a>.
        </p>
      </subsection>

      <subsection name="FML Sample">
        <p>
          The following is a sample FML document:
        </p>
        <source><![CDATA[<?xml version="1.0" encoding="UTF-8"?>
<faqs xmlns="http://maven.apache.org/FML/1.0.1"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/FML/1.0.1 http://maven.apache.org/xsd/fml-1.0.1.xsd"
  title="Frequently Asked Questions"
  toplink="false">

  <part id="general">
    <title>General</title>

    <faq id="whats-foo">
      <question>
        What is Foo?
      </question>
      <answer>
        <p>some markup goes here</p>

        <source>some source code</source>

        <p>some markup goes here</p>
      </answer>
    </faq>

    <faq id="whats-bar">
      <question>
        What is Bar?
      </question>
      <answer>
        <p>some markup goes here</p>
      </answer>
    </faq>
  </part>

  <part id="install">

    <title>Installation</title>

    <faq id="how-install">
      <question>
        How do I install Foo?
      </question>
      <answer>
        <p>some markup goes here</p>
      </answer>
    </faq>

  </part>

</faqs>
]]></source>

      </subsection>
    </section>

    <section name="Validation">
      <p>
        Doxia is able to validate your fml files as described
        <a href="../doxia/doxia-modules/doxia-module-fml/using-fml-xsd.html">here</a>.
      </p>
    </section>

  </body>
</document>
