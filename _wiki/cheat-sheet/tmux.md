---
layout  : wiki
title   : tmux cheat sheet
summary : 
date    : 2021-11-30 15:56:19 +0900
updated : 2022-02-20 13:22:12 +0900
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
- <ctrl+b> + d : detach session
- <ctrl+b> + ) : next session
- <ctrl+b> + ( : previous session

# tmux windows
- 브라우저의 탭과 유사함 
 
## key bindings
- <ctrl+b> + c : create window
- <ctrl+b> + n : move to next window
- <ctrl+b> + p : move to previous window
- <ctrl+b> + l : move to window last used
- <ctrl+b> + 0..9 : select window by nubmer
- <ctrl+b> + ' : select window by name
- <ctrl+b> + . : change window number
- <ctrl+b> + , : rename window
- <ctrl+b> + f : search windows
- <ctrl+b> + & : kill window
- <ctrl+b> + w : list windows
- <ctrl+b> + z : toggle pane zoom

# tmux panes
- 화면을 여러개로 나눠쓸 때 사용하는 개념

## key bindings
- <ctrl+b> + % : vertical split
- <ctrl+b> + " : horizontal split
- <ctrl+b> + <left> : move to pane to the right
- <ctrl+b> + <right> : move to pane to the left
- <ctrl+b> + <up> : move up to pane
- <ctrl+b> + <right> : move down to pane 
- <ctrl+b> + o : go to next pane
- <ctrl+b> + ; : go to last active pane
- <ctrl+b> + } : move pane right 
- <ctrl+b> + { : move pane left 
- <ctrl+b> + ! : convert pane to window 
- <ctrl+b> + x : kill pane

# tmux copy mode
## key bindings
- <ctrl+b> + [ : enter copy mode
- <ctrl+b> + ] : paster from buffer

## copy mode commands
- <space> : start selection
- <enter> : copy selection
- <esc> : clear selection
- g : go to top
- G : go to bottom
- h : move cursor left
- j : move cursor down
- k : move cursor up
- l : move cursor right
- / : search
- # : list paste buffers
- q : quit
