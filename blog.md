---
layout: default-plus
title: Blog
feed-in-sidebar: false
---

<h1>Latest Posts</h1>

{% for post in site.posts limit:10 %}
   <div class="post-preview">
   <h2 class="post-link"><a href="{{ post.url }}">{{ post.title }}</a></h2>
   <em class="post-date">First published {{ post.date | date: "%B %d, %Y" }}</em>
   <br><!--<br>
   <span>[
     {% for tag in post.tags %}
       {% capture tag_name %}{{ tag }}{% endcapture %}
       <a href="/tag/{{ tag_name }}"><code class="tag"><nobr>{{ tag_name }}</nobr></code>&nbsp;</a>
     {% endfor %}
   ]</span> -->

   {{ post.content | split:'<!--break-->' | first }}
   {% if post.content contains '<!--break-->' %}
      <a class="read-more-link" href="{{ post.url }}">Continue reading...</a>
   {% else %}
      <div class="no-read-more-padding"></div>
   {% endif %}
   </div>
{% endfor %}
