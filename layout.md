---

layout: page
title: Layout
subtitle: How to effectively organize and lay out content
use-site-title: true
bigimg: /img/Hero_Layout.jpg
categories: [LayoutMain]

---

<div class="posts-list">

{% for category in site.categories %}
{% if category[0] == 'Layout' %}
{% for post in category[1] %}

 <article class="post-preview">
   <a href="{{ post.url | prepend: site.baseurl }}">
  <h2 class="post-title">{{ post.title }}</h2>

  {% if post.subtitle %}
  <h3 class="post-subtitle">
    {{ post.subtitle }}
  </h3>
  {% endif %}
   </a>

   <p class="post-meta">
     Posted on {{ post.date | date: "%B %-d, %Y" }}
   </p>

   <hr align="left" class="{{ post.categories.first | replace: " ", "" }}"/>

   <div class="post-entry-container">
     {% if post.image %}
     <div class="post-image">
       <a href="{{ post.url | prepend: site.baseurl }}">
         <img src="{{ post.image }}">
       </a>
     </div>
     {% endif %}
     <div class="post-entry">
       {{ post.excerpt | strip_html | xml_escape | truncatewords: site.excerpt_length }}
       {% assign excerpt_word_count = post.excerpt | number_of_words %}
       {% if post.content != post.excerpt or excerpt_word_count > site.excerpt_length %}
         <a href="{{ post.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
       {% endif %}
     </div>
   </div>

   {% if post.tags.size > 0 %}
   <div class="blog-tags">
     Tags:
     {% if site.link-tags %}
     {% for tag in post.tags %}
     <a href="{{ site.baseurl }}/tags#{{- tag -}}">{{- tag -}}</a>
     {% endfor %}
     {% else %}
       {{ post.tags | join: ", " }}
     {% endif %}
   </div>
   {% endif %}

  </article>
  {% endfor %}
 {% endif %}
 {% endfor %}

</div>
