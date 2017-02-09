---
author: viviworld
comments: true
date: 2014-01-07 01:41:20+00:00
layout: page
link: http://www.labazhou.net/archives/
slug: archives
title: 列表
wordpress_id: 149
---

<div id="smart-archives-list">
            <ul class="archive-list">
                {% for post in site.posts %}
                <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
                {% endfor %}
            </ul>    
        </div>