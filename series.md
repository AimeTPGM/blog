---
layout: page
title: Series
permalink: /series
---

<div>

{% assign allSeries = "" %}
{% for post in site.posts %}
    {% if post.series %}
        {% assign seriesName = post.series | append:'|' %}
        {% unless allSeries contains seriesName %}
            {% assign allSeries = allSeries | append: seriesName %}
        {% endunless %}
    {% endif %}
{% endfor %}

{% assign allSeries = allSeries | split:'|' %}
{% for series in allSeries %}
    {% assign spinOff = "" %}
    {% assign mainPart = "" %}
    {% for post in site.posts %}
        {% if post.series == series %}
            {% if post.series_episode != "Spin-off" %}
                {% assign postInfo = post.topic | append: '_' %}
                {% assign postInfo = postInfo | append: post.url | append: '_' %}
                {% assign postInfo = postInfo | append: post.series_episode %}
                {% assign mainPart = mainPart | append: postInfo | append: '|' %}
            {% else %}
                {% assign postInfo = post.topic | append: '_' %}
                {% assign postInfo = postInfo | append: post.url | append: '_' %}
                {% assign postInfo = postInfo | append: post.series_episode | append: '|' %}
                {% assign spinOff = spinOff | append: postInfo %}
            {% endif %}
        {% endif %}
    {% endfor %}

    {% assign mainPart = mainPart | split:'|' | reverse %}
    <h2 id="{{series | downcase | replace: ' ', '-' }}"><span>{{series}}</span></h2>
    {% if series != "Others" and series != "Human Being" %}
    <h3>Main Content</h3>
    {% endif %}
    <div class="series-wrapper">
        {% for item in mainPart %}
            {% assign postInfo = item | split: '_' %}
                <div>
                    <a href="{{ site.baseurl }}{{postInfo[1]}}" target="_blank">
                        {% if postInfo[2] %}
                        Part {{ postInfo[2] }} 
                        {% endif %}
                        {{ postInfo [0]}}</a>
                </div>
        {% endfor %}
    </div>

    {% assign spinOff = spinOff | split:'|' | sort %}
    {% if spinOff.size > 0 %}
    <div class="series-wrapper" style="margin-top: 20px;">
        <h3>Spin-off</h3>
        {% for item in spinOff %}
            {% assign postInfo = item | split: '_' %}
                <div>
                    <a href="{{ site.baseurl }}{{postInfo[1]}}" target="_blank">{{ postInfo [0]}}</a>
                </div>
        {% endfor %}
    </div>
    {% endif %}
{% endfor %}

</div>