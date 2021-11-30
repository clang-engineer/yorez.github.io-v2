---
layout  : wiki
title   : Tmux cheat sheet
summary : 
date    : 2021-11-30 15:56:19 +0900
updated : 2021-11-30 16:02:54 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}


# tmux sessions
 
## new session
```shell
tmux
tmux new
tmux new-session
tmux new -s sessionname
```

## attach session 
```shell
tmux a
tmux att
tmux attach
tmux attach-session
tmux a -t sessionname
```

## remove session
```shell
tmux kill-ses
tmux kill-session -t sessionname
```

 ## key bindings
 - <ctrl+b> + $ : rename session
 
