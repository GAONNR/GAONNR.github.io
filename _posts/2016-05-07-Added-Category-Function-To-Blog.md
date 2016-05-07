---
layout: post
title: 블로그에 Category 기능을 적용
category: Setting
---

블로그의 글 개수가 점점 많아짐에 따라, Jekyll의 category 기능을 이용하여 포스트들을 정리해 보기로 했다.

기본적으로 [이곳](http://stackoverflow.com/questions/20872861/jekyll-display-posts-by-category)의 YAML 코드를 참고하여 작성하였다.

작성된 결과물은 오른쪽 상단의 햄버거 메뉴를 누르면 나오는 Archives 페이지에 반영되었으며, 코드는 다음과 같다.

```YAML
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
```

원리는 대강 이해할 수 있었지만, CSS를 아직 감을 잡지 못해서, 야매로 이것저것 바꿔보면서 스타일을 적용하느라 애먹었다.  
아직도 썩 맘에 드는 디자인을 만들진 못했지만, 이 정도로 만족하고 좀 더 생산적인 일을 해야겠다.
