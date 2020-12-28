---
layout: page
title: Rya Downloads
description: Project Downloads page
group: nav-right
---
<!--
{% comment %}
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
{% endcomment %}
-->
{% include JB/setup %}

## {{ site.data.project.name }} Downloads

If you are interested in helping out, please join our developers list [{{site.data.project.dev_list}}](mailto:{{site.data.project.dev_list_subscribe}}?subject=subscribe to Rya dev list) by sending an email to [{{site.data.project.dev_list_subscribe}}](mailto:{{site.data.project.dev_list_subscribe}}?subject=subscribe to Rya dev list).

{{ site.data.project.name }} is released as a source artifact, and [also through Maven](https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.apache.rya%22).

### Source releases

Release          | Date       | Download | Notes
:--------------- | :--------- | :------- | :----
{% for post in site.categories.release %}{% comment %}

{% endcomment %}{% if post.filename contains "incubating" %}{% comment %}
{% endcomment %}{% assign theName = site.data.project.incubator_slash_name %}{% comment %}
{% endcomment %}{% else %}{% comment %}
{% endcomment %}{% assign theName = site.data.project.unix_name %}{% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %}{% if post.fullVersion %}{% comment %}
{% endcomment %}{% assign v = post.fullVersion %}{% comment %}
{% endcomment %}{% else %}{% comment %}
{% endcomment %}{% capture v %}apache-{{ site.data.project.unix_name }}-{{ post.version }}{% endcapture %}{% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %}{% if forloop.index0 < 1 %}{% comment %}
{% endcomment %}{% capture p %}https://www.apache.org/dyn/closer.lua/{{ theName }}/{{ v }}{% endcapture %}{% comment %}
{% endcomment %}{% capture d %}https://www.apache.org/dist/{{ theName }}/{{ v }}{% endcapture %}{% comment %}
{% endcomment %}{% else %}{% comment %}
{% endcomment %}{% capture p %}https://archive.apache.org/dist/{{ theName }}/{{ v }}{% endcapture %}{% comment %}
{% endcomment %}{% capture d %}https://archive.apache.org/dist/{{ theName}}/{{ v }}{% endcapture %}{% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %} <a href="{{ post.url }}">{{ post.version }}</a>{% comment %}
{% endcomment %} | {{ post.date | date_to_string }}{% comment %}
{% endcomment %} | {% if post.filename %}{% comment %}
{% endcomment %} [zip]( {{ p }}/{{ post.filename }}.zip){% comment %}  
{% endcomment %} [pgp]( {{ d }}/{{ post.filename }}.zip.asc ){% comment %}
{% endcomment %}{% if post.version == "3.2.10" %} [sha1]({{ d }}/{{ post.filename }}.zip.sha1){% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %}{% if post.version != "3.2.10" %} [sha512]({{ d }}/{{ post.filename }}.zip.sha512){% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %}{% endif %}{% comment %}
{% endcomment %} | [Release notes]({{ post.releaseNotes | liquify }})
{% endfor %}
<br>
Download a source distribution in <!-- either *tar* or --> *zip* format,
and [verify](https://www.apache.org/dyn/closer.cgi#verify)
using the corresponding *pgp* signature (using the committer file in [KEYS](https://www.apache.org/dist/{{ site.data.project.unix_name }}/KEYS)).
If you cannot do that, the *sha512* hash file may be used to check that the
download has completed okay.


For fast downloads, current source distributions are hosted on mirror servers;

Older source distributions are in the
[archive](https://archive.apache.org/dist/{{ site.data.project.unix_name }}/).
 
If a download from a mirror fails, retry, and the second download will likely
succeed.


For security, hash and signature files are always hosted at
[Apache](https://www.apache.org/dist/{{ site.data.project.unix_name }}).

