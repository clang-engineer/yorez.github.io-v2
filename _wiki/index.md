---
layout  : wikiindex
title   : root
toc     : true
public  : true
comment : false
regenerate: true
---

## [[/vim/index]]

* [[/vim/plugin]]

## [[/etc/index]]

* [[/etc/tableau-embedded]]
* [[/etc/stack-edit]]

## [[/memo/index]]

* [[/memo/2021]]

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

