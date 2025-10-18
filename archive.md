---
layout: page
title: Archive
permalink: /archive/
---

Browse all posts from the start. The first 10 entries were written over one weekend with the aim of sharing them with friends and family to help them understand me better. 

---

<div class="posts">
  {% assign sorted_posts = site.posts | sort: 'date' %}
  {% for post in sorted_posts %}
  <div class="post">
    <h2 class="post-title">
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h2>
    <span class="post-date">{{ post.date | date_to_string }}</span>
    {{ post.excerpt | strip_html | truncatewords: 30 }}
    <br />
    <a href="{{ post.url }}" class="read-more">&gt; Read more</a>
    <hr />
  </div>
  {% endfor %}
</div>

[Back to Home]({{ site.baseurl }})
