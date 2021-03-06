---
layout: post
title: Keep it simple, stupid!
date: 2019-01-21
categories: [Jekyll]
---

Time passes and [Cmaketopia](https://unclecshark.github.io/Cmaketopia/) project goes on. Suddenly I realized that I needed to add navigation to the site. Jekyll has such but for posts but not for pages. I was googling for hours. But all solutions were too complicated. I had to do it myself. I wanted to implement a bidirectional list based on Jekyll markdown pages. I thought "Keep it simple stupid!" See how I did it. First I added two **Custom Variables** previous_page and next_page that I could access in Liquid.

<!-- markdownlint-disable MD033 -->
<!-- markdownlint-disable MD002 -->
<!-- markdownlint-disable MD003 -->
<!-- markdownlint-disable MD022 -->
{% highlight markdown %}
{% raw  %}

---
layout: page
title: Cmake Philosophy
previous_page: PreviousPageNameURL
next_page: NextPageNameURL
---
# Cmake Philosophy

{% endraw %}
{% endhighlight %}
<!-- markdownlint-enable MD033 -->
<!-- markdownlint-enable MD002 -->
<!-- markdownlint-enable MD003 -->
<!-- markdownlint-enable MD022 -->

Second, on the page template I added two divisions at the bottom.
<!-- markdownlint-disable MD033 -->
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
<!-- markdownlint-enable MD033 -->
You can see an effect on [Cmaketopia](https://unclecshark.github.io/Cmaketopia/) page.
Just a [kiss](https://en.wikipedia.org/wiki/KISS_principle).:kiss:  
Bye  
C