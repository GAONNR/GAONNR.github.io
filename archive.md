---
layout: another-page
title: Archive
---

<div class="preview">
  <h1 class="preview">Archive</h1>
  <ul class="preview-posts">
  {% for category in site.categories %}
    <li>
    <h3><b name="{{ category | first }}">{{ category | first }}<categoryfont>   : Category</categoryfont></b>
        {% for posts in category %}
          {% for post in posts %}
              {% if post.url %}
                  <h4><li><a href="{{ post.url }}">{{ post.title }} <small>{{ post.date | date_to_string }}</small></a></li></h4>
              {% endif %}
          {% endfor %}
        {% endfor %}
    </h3>
    </li>
  {% endfor %}
  </ul>
</div>

<!--This was original archive code
<div class="preview">
	<h1 class = "preview">Post Lists</h1>
	<ul class="preview-posts">
  {% for post in site.posts %}
	<li>
		<h3>
			<a href="{{ site.baseurl }}{{ post.url }}">
				{{ post.title }}
				<small>{{ post.date | date_to_string }}</small>
			</a>
		</h3>
	</li>
  {% endfor %}
	</ul>
</div>
-->

<!--This was Original category code
{% for category in site.categories %}
  <li><a name="{{ category | first }}">{{ category | first }}</a>
      <ul>
      {% for posts in category %}
        {% for post in posts %}
            {% if post.url %}
                <li><a href="{{ post.url }}">{{ post.title }}</a></li>
            {% endif %}
        {% endfor %}
      {% endfor %}
      </ul>
  </li>
{% endfor %}
-->
