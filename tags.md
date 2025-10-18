---
layout: page
title: Tags
permalink: /tags/
---

Browse posts by tag. Use the tag list to jump to a section.

{% if site.tags == empty %}
<p><em>No tags yet.</em> Add a <code>tags:</code> list to your post front matter to populate this page.</p>
{% endif %}

{% assign tags_list = site.tags | sort %}

<ul class="tag-cloud">
  {% for tag in tags_list %}
    {% assign tag_name = tag[0] %}
    <li>
      <a href="#{{ tag_name | slugify }}">{{ tag_name }}</a>
      <span class="count">({{ tag[1].size }})</span>
    </li>
  {% endfor %}
  {% if tags_list == empty %}
    <li><a href="{{ '/' | relative_url }}">Back to Home</a></li>
  {% endif %}
  </ul>

<hr />

{% for tag in tags_list %}
  {% assign tag_name = tag[0] %}
  <h2 id="{{ tag_name | slugify }}">{{ tag_name }} <span class="count">({{ tag[1].size }})</span></h2>
  {% assign posts = tag[1] | sort: 'date' | reverse %}
  <ul class="tag-posts">
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <small class="post-date">— {{ post.date | date_to_string }}</small>
      </li>
    {% endfor %}
  </ul>
  <hr />
{% endfor %}

<p><a href="{{ '/' | relative_url }}">Back to Home</a></p>

