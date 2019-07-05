---
title: This is my title
layout: default
---
### My Learning Blog

### [Scrum](scrum.md)
### [Javascript](javascript.md)
### [Angular](angular.md)

<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>
### Styling Primeng pTooltip
If you are apply CSS in your inside Component css file than it will not apply on the tooltip because tooltip is added in body root path. So you have to add css in Global Css file of your project which were located in your project src > assets > css Or you can also apply in src > assets > styles.scss. Use below css: .ui-tooltip .ui-tooltip-text {
  background-color: red !important;
}



