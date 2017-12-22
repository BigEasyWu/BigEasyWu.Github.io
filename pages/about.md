---
layout: page
title: About
description:
keywords: Bingkui Wu, 吴炳奎
comments: true
menu: 关于
permalink: /about/
---
> God, tell us the reason youth is wasted on the young

>It's hunting season and the lambs are on the run
Searching for meaning

>But are we all lost stars, trying to light up the dark?


## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
