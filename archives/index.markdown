---
author: viviworld
comments: true
date: 2014-01-07 01:41:20+00:00
layout: page
link: http://www.labazhou.net/archives/
slug: archives
title: 归档
wordpress_id: 149
---

<section>
    <article  class="page type-page status-publish hentry">
        <h1 class="post-title"><a href="http://www.labazhou.net/archives/">归档</a></h1>
        <div id="smart-archives-list">
            <ul class="archive-list">
                {% for post in site.posts %}
                <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
                {% endfor %}
            </ul>    
        </div>
    </article>
</section>