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
* [[vim/neovim]]

## [[linux/index]]

* [[linux/command]]
* [[linux/shell-script]]

## [[computer-science/index]]

* [[computer-science/computer-metaphor]]

## [[etc/index]]

* [[etc/stack-edit]]
* [[etc/markdown-syntax]]
* [[etc/erdcloud]]
* [[etc/regex]]

## [[memo/index]]

* [[memo/2021]]

## [[window/index]]

* [[window/service]]

## [[tableau/index]]
* [[tableau/tableau-trusted-ticket]]
* [[tableau/tableau-issue]]


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
