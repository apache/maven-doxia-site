 ------
 Doxia - SWF Macro
 ------
 The Maven Team
 ------
 2007-05-17
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

SWF Macro

 The SWF macro enables users of APT to put SWF (Flash) assets in their documentation.

 Flash assets typically need to be wrappered in <<<object>>> and <<<embed>>> tags and can have
 a variety of parameters.  Below is a typical example:

+----
<object classid='clsid:D27CDB6E-AE6D-11cf-96B8-444553540000'
    codebase='http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,29,0'
    width='400' height='400' id='MyMovie'>
    <param name='movie' value='myfile.swf'>
    <param name='quality' value='high'>
    <param name='menu' value='false'>
    <param name='loop' value='0'>
    <embed src='myfile.swf' width='400' height='400' loop='0' quality='high'
    pluginspage='http://www.macromedia.com/go/getflashplayer'
    type='application/x-shockwave-flash' menu='false'></embed>
</object>
+----

  In order to use a *.swf in your APT file, use the basic syntax:

+----
%{swf|src=swf/myfile.swf|id=MyMovie|width=600|height=200}
+----

  For which <<<src>>> is the required parameter.  Make sure to put your *.swf file into
  the <</resources>> folder so that it will get copied to /target when running the <<<mvn site>>> task.

  You can use more advanced parameters to control the output, as per below:

+----
%{swf|src=swf/myfile.swf|id=MyMovie|width=600|height=200|version=9|allowScript=always}
+----

  For a full listing of parameters and their values see the Adobe knowledge base:

  {{{http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_12701}http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_12701}}

*Parameters and Defaults

  Currently the following parameters are available through the macro.  If no value is placed within a parameter, the
  value will default to the following:

  * id = "swf"

  * width = "400"

  * height = "400"

  * quality = "high"

  * menu = "false"

  * loop = "0"

  * play = "true"

  * version = "9,0,45,0"

  * allowScript = "sameDomain"

  []

  Note:  There is some provided shorthand for versions, i.e. - version=6 - becomes version=6,0,29,0.

  <TODO:>  only shorthand for 6 and 9 are functional.  Need to find standard long
  version for other types.
