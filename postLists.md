---
layout: another-page
title: Post Lists
---

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
