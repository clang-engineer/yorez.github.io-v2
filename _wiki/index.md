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
* [[vim/neovim-swap-error]]
* [[vim/shortcut]]

## [[linux/index]]

* [[linux/jobs]]
* [[linux/command]]
* [[linux/nohub]]
* [[linux/shell-script]]
* [[linux/scp]]

## [[git/index]]
* [[git/diff]]
* [[git/branch]]
* [[git/reset]]
* [[git/multi-account]]
* [[git/stash]]
* [[git/clean]]
* [[git/etc]]
* [[git/revert]]

## [[computer-science/index]]

* [[computer-science/computer-metaphor]]

## [[etc/index]]

* [[etc/stack-edit]]
* [[etc/markdown-syntax]]
* [[etc/erdcloud]]
* [[etc/regex]]
* [[etc/nikto]]
* [[etc/hhkb-hybrid]]
* [[etc/jenkins]] 
* [[etc/private-certificate]]

## [[window/index]]

* [[window/service-manager]]

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
