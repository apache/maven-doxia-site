 -----
 Doxia Developers Centre
 -----
 Vincent Siveton
 ------
 2008-03-02
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

Create a New Doxia Macro

 You need to add the following {{{https://codehaus-plexus.github.io/plexus-containers/plexus-component-metadata/}plexus-component-metadata plugin}}
 configuration to generate the correct Plexus <component.xml> file from annotations
 for the project containing your macro:

+----
<project>
  ...
  <build>
    ...
    <plugins>
      <plugin>
        <groupId>org.codehaus.plexus</groupId>
        <artifactId>plexus-component-metadata</artifactId>
        <executions>
          <execution>
            <goals>
              <goal>generate-metadata</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      ...
    </plugins>
  ...
  </build>
  ...
</project>
+----

 You should implement the <AbstractMacro> class:

+----
import org.apache.maven.doxia.macro.AbstractMacro;

/**
 * @plexus.component role="org.apache.maven.doxia.macro.Macro" role-hint="my"
 */
public class MyMacro
    extends AbstractMacro
{
...
    public void execute( Sink sink, MacroRequest request )
        throws MacroExecutionException
    {
        String myValue = (String) request.getParameter( "myParam" );
...
    }
...
}
+----

 To use it, you need to write the following markups:

  * APT

+----
%{my|myParam=myValue} <!-- my is the macro name defined by role-hint -->
+----

  * XDoc

+----
<macro name="my"> <!-- my is the required macro name defined by role-hint -->
  <param name="myParam" value="myValue"/>
</macro>
+----

  []

* {References}

  * {{{../modules/index.html}Doxia Modules Guide}}

  * {{{../macros/index.html}Doxia Macros Guide}}

  * {{{../doxia/apidocs/index.html}Doxia API Reference}}

  * {{{../doxia-sitetools/apidocs/index.html}Doxia Sitetools API Reference}}

  * {{{/plugin-developers/cookbook/plexus-plugin-upgrade.html}Upgrading from Plexus Javadoc Tags to Plexus Java Annotations}}

  []
