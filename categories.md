---
layout: page
title: 分类
---
  <!--  使用 {{ category | first }} 输出分类的名称 
        使用 {{ category | last | size }} 输出该分类下文章的数目 
        遍历category.last输出所有文章的信息，构建到该文章的索引 -->
  <div>
      {% for category in site.categories %}
    <h2>{{ category | first }}</h2>
       <span>总共{{ category | last | size }}篇</span> 
    <ul class="arc-list">
    {% for post in category.last %} 
    <li>{{ post.date | date:"%d/%m/%Y"}}<a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul> 
    {% endfor %}

  </div>

<!--<div class="posts-list">
  {% for post in site.categories[page.category] %}
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
      <!-- Posted on {{ post.date | date: "%B %-d, %Y" }} -->
      Posted on {{ post.date | date: "%Y-%m-%d" }}
    </p>
  
    <div class="post-entry">
      {{ post.content | truncatewords: 20 | strip_html | xml_escape}}
      <a href="{{ post.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
    </div>
  
   </article>
  {% endfor %}
</div>-->