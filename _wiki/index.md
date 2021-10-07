---
layout  : wikiindex
title   : root
toc     : true
public  : true
comment : false
regenerate: true
---

## [[vim/index]]

* [[vim/plugin]]

## [[etc/index]]

* [[etc/stack-edit]]
* [[etc/erdcloud]]
* [[etc/tableau-trusted-ticket]]
* [[etc/tableau-issue]]

## [[memo/index]]

* [[memo/2021]]


## [[computer-science/index]]

* [[computer-science/computer-metaphor]]


## [[linux/index]]

* [[linux/command]]


## [[spring/index]]
## [[chrome/index]]

## blog posts
<div>
    <ul>
{% for post in site.posts %}
    {% if post.public != false %}
        <li>
            <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                {{ post.title }}
            </a>
        </li>
    {% endif %}
{% endfor %}
    </ul>
</div>

