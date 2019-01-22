---
layout: post
title: Keep it simple, stupid!
date: 2019-01-21
categories: [Jekyll]
---

Time passes and [Cmaketopia](https://unclecshark.github.io/Cmaketopia/) project goes on. Suddenly I realized that I needed to add navigation to the site. Jekyll has such but for posts but not for pages. I was googling for hours. But all solutions were too complicated. I had to do it myself. I wanted to implement a bidirectional list based on Jekyll. I thought "Keep it simple stupid!" See how I did it. First I added two **Custom Variables** previous_page and next_page that I could access in Liquid.

```markdown
---
layout: page
title: Cmake Philosophy
previous_page: PreviousPageNameUrl
next_page: NextPageNameUrl
---
# Cmake Philosophy

```

Second, on the page template I added two divisions at the bottom.

{% highlight markdown %}
{% raw  %}

<div class="left align-right">
    {% if page.previous_page %}
        <a href="{{ page.previous_page }}">&laquo;Back</a>
    {% else %}
        <span class="prev disabled">&laquo;Back</span>
    {% endif %}
</div>
<div class="right align-left">
    {% if page.next_page %}
        <a href="{{ page.next_page }}">Next &raquo;</a>
    {% else %}
        <span class="prev disabled">Next &raquo;</span>
    {% endif %}
</div>

{% endraw %}
{% endhighlight %}

You can see an effect [Cmaketopia](https://unclecshark.github.io/Cmaketopia/).
Just a [kiss](https://en.wikipedia.org/wiki/KISS_principle).  
Bye  
C