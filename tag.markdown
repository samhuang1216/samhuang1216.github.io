---
layout: page
title: Tags
permalink: /tag/
---


<div >
  <div class="site-tag">
    {% for tag in site.tags %}
    <a href="#{{ tag[0] | slugify }}" class="post-tag">{{ tag[0] }} ({{ tag | last | size }})</a>, &nbsp;
    {% endfor %}
  </div>
  <hr/>
  <div>
    {% for tag in site.tags %}
    <h4 id="{{ tag[0] | slugify }}">{{ tag[0] }}  ({{ tag | last | size }})</h4>
    <ul >
      {% for post in tag[1] %}
        <a  href="{{ site.baseurl }}{{ post.url }}">
      <li>
        {{ post.title }} |
      <small>{{ post.date | date_to_string }}</small>
      </li>
      </a>
      {% endfor %}
    </ul>
    {% endfor %}
  </div>
</div>

