---
layout: page
title: Tags
permalink: /tags
---
<div class="tag-page-wrapper">
{% assign rawtags = "" %}
{% for post in site.posts %}
	{% assign ttags = post.tags | join:'|' | append:'|' %}
	{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}

{% assign tags = "" %}
{% for tag in rawtags %}
	{% if tag != "" %}
		{% if tags == "" %}
			{% assign tags = tag | split:'|' %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}

<div class="span-wrapper tag-page">
{% for tag in tags %}
    <span>
        <a href="#{{ tag | slugify }}"> {{ tag }} </a>
    </span>
{% endfor %}
</div>

{% for tag in tags %}
	<h2 id="{{ tag | slugify }}">{{ tag }}</h2>
	<ul>
	 {% for post in site.posts %}
		 {% if post.tags contains tag %}
		 <li>
            <div class="post-tag-list">
                <div>
                    <a href="{{ site.baseurl }}/{{ post.url }}">
                    {{ post.topic | replace: '<br>', '' }}
                        <small>{{ post.date | date_to_string }}</small>
                    </a>
                </div>
                <div class="span-wrapper tag-page">
                    {% for tag in post.tags %}
                        <span><a class="tag" href="/blog/tag#{{ tag | slugify }}">{{ tag }}</a></span>
                    {% endfor %}
                </div>
            </div>
		 </li>
		 {% endif %}
	 {% endfor %}
	</ul>
{% endfor %}
</div>
