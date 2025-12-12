---
layout: single
title: "相簿"
permalink: /album/
classes: wide
---

記錄與分享我的所見與所聞

{% assign album_images = site.static_files | where_exp: "file", "file.path contains '/assets/images/album/'" %}
{% assign album_images = album_images | sort: "path" %}

{% if album_images and album_images.size > 0 %}
<div class="album-gallery">
  {% for file in album_images %}
  <figure>
    <a href="{{ file.path | relative_url }}">
      <img class="album-thumb" src="{{ file.path | relative_url }}" alt="{{ file.basename | escape }}" loading="lazy">
    </a>
  </figure>
  {% endfor %}
</div>
{% else %}
<div class="notice--warning">
  <p>目前尚未偵測到照片。請將相片放到 <code>assets/images/album</code> 後重新產生網站。</p>
</div>
{% endif %}
