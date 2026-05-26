---
title: "分类与标签"
permalink: /categories/
layout: single
author_profile: true
breadcrumbs: true
---

在同一页面查看全部分类与标签。

## 分类

{% assign category_taxonomies = site.categories | sort %}

<ul class="taxonomy__index">
	{% for taxonomy in category_taxonomies %}
	<li>
		<a href="#category-{{ forloop.index }}">
			<strong>{{ taxonomy[0] }}</strong> <span class="taxonomy__count">{{ taxonomy[1].size }}</span>
		</a>
	</li>
	{% endfor %}
</ul>

{% for taxonomy in category_taxonomies %}

<section id="category-{{ forloop.index }}" class="taxonomy__section">
	<h2 class="archive__subtitle">{{ taxonomy[0] }}</h2>
	<div class="entries-list">
		{% for post in taxonomy[1] %}
			{% include archive-single.html type="list" %}
		{% endfor %}
	</div>
	<a href="#page-title" class="back-to-top">返回顶部 &uarr;</a>
</section>
{% endfor %}

## 标签

{% assign tag_taxonomies = site.tags | sort %}

<ul class="taxonomy__index">
	{% for taxonomy in tag_taxonomies %}
	<li>
		<a href="#tag-{{ forloop.index }}">
			<strong>{{ taxonomy[0] }}</strong> <span class="taxonomy__count">{{ taxonomy[1].size }}</span>
		</a>
	</li>
	{% endfor %}
</ul>

{% for taxonomy in tag_taxonomies %}

<section id="tag-{{ forloop.index }}" class="taxonomy__section">
	<h2 class="archive__subtitle">{{ taxonomy[0] }}</h2>
	<div class="entries-list">
		{% for post in taxonomy[1] %}
			{% include archive-single.html type="list" %}
		{% endfor %}
	</div>
	<a href="#page-title" class="back-to-top">返回顶部 &uarr;</a>
</section>
{% endfor %}
