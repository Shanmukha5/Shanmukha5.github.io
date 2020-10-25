---
Date : October 24, 2020
By    : Shanmukha Arepalli
---
# TMUX -- Terminal Multiplexer

Tmux is a terminal multiplexer. The concept is, within one terminal window you can open multiple widows and split-views (called "panes").
Tmux keeps these windows and panes in a session. We can exit a session at any point. This is called "**detaching**".
Tmux will keep this session alive until you kill the tmux server (e.g. when you reboot).
This is useful because at any later point in time you can pick that session up exactly from where you left it by simply "**attaching**" to that session.

**Before you begin**
`c-` means Ctrl (hold on to ctrl option)
`c-b` means Ctrl-b, this is the initial command to interact with tmux
`c-b` is the prefix to run a command for tmux
`tmux show -g | cat > ~/.tmux.conf` -- this is the starting point for tmux configuration file
`set -g mouse on` -- add this to your ".tmux.conf" (tmux configuration file), to add mouse scrolling option
`c-b :set -g mouse on` -- to use mouse scrolling (if you didn't do the configuration file and add mouse scrolling option), use this command for this and every pane you open.


## Installing
`sudo apt-get install tmux`

`tmux` -- to enter the tmux terminal window.

## Panes

### Splitting Panes
Panes are split-views in a single window.

`c-b %` -- to split the window into Vertical panes
`c-b "` -- to split the window into horizontal panes

### Navigating Panes
We can use mouse to select which pane we want work.
But using keyboard also we can do that.

`c-b <arrow key>` -- according to the split-view, we can use arrow keys (left, right, up, and down) to navigate among the panes

### Closing Panes
It is as simple as closing a terminal, you can type `exit` or `c-d`

### Others
`c-b o` -- swap panes
`c-b q` -- show pane numbers
`c-b x` -- kill pane
`c-b +` -- break pane into window


## Creating Windows
Windows in tmux can be compared to creating new virtual desktops
`c-b c` -- to create new window. You can divide the window into several panes.
`c-b l` -- switch to last window (numerically)

`c-b p` -- switch to the previous window
`c-b n` -- switch to next window (numerically)
`c-b <number>` -- You will have window numbers at the bottom of the scree, using that number you can also switch the windows.
`c-b &` -- to close current window

## Session Handling
To detach your current session use `c-b d`
You can also use `c-b D` to have tmux give you a choice which of your sessions you want to detach.

`tmux ls` -- to list the sessions
`tmux attach -t <number>` -- tell tmux to attack to the session with <number>
`tmux new -s <session name>` -- you can also give the session a name, if you don't want to call it with a number
`tmux rename-session -t <new name> <old name> -- to rename the session

## Scroll Buffer
Tmux doesn't support mouse scrolling by default. Hence you may have to use "COPY MODE".
`c-b [` -- to start the copy mode, then use the arrow keys to traverse the terminal, or use (h for left, j for down, k for up, l for right), g (lowercase g) to go top, G (uppercase g) to go bottom.
Inside the buffer,
- `?` -- to search up
- `/` -- to search bottom

`n` -- to move on to next result of search item
`N` -- to go to previous result of the search item

We can also copy the text, inside the copy mode:
- `<space>` -- to select the text
- Move through the text to select the text
- `c-w` or <ENTER> -- to copy the text to the buffer.
- `c-b ]` -- to paste the text in the buffer.


## Other useful commands
`c-b ?` -- to see a list of all available commands 
`c-b z` -- to make a pane go full screen. Use this same command to shrink it back to its previous size
`c-b c-<arrow key>` -- resize pane in direction of <arrow key>, (c- means ctrl, two times here)
`c-b ,` -- to rename the current window

To change the prefix, add the following three commands to your ~/.tmux.conf,
* `set -g prefix C-s` 
* `unbind C-b`
* `bind C-s send-prefix`



## References
- https://gist.github.com/MohamedAlaa/2961058
- http://tmuxcheatsheet.com/
- [Change c-b to c-a](https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/#fnref:1)
