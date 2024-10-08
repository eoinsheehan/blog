# Developer workflow

There were just a couple of things that greatly improved my workflow.

These were:
- Moving to nvim as code editor
    - just used kickstart to not have to mess around with the config all that much.
    - nvim comes with lua built in somehow - not really sure how this works could do with looking into it
- Using tmux to have multiple shell windows up and running
    - just some minor tweaks required on the default controls
- Change some of the mappings on the keyboard
    - basically just remapping the caps lock key to be esc
    - also for tmux just changing the activation

Then with nvim
There were a couple of binary files that I had been missing which were essential
- fzf was definitely one of them anyways and maybe another one.

Being able to touch type at a reasonable level which I have now thankfully arrived at.
I got a bit addicted to this element which had long been removed as a limiting factor when I was looking into areas for improvement.


But in reality I needed to focus on developing APIs to best practice, learning about database internals etc.

i was having issues with my workflow if resolving merge conflicts in git after a revase using neovim so I looked onto that and got mergetool came to light which seems to be useful. after that it got me thinking about configiring my jnteractions with git via the command line so that js probably something that I should look into as well.


ok so today I learned that in vim I had been using visual line incorrectly.
For columnar based operations I should have been using visual block mode as opposed to visual line mode which is specific to line based operations.
e. indentation changed are actually block based operations
but copying or deleting entrire lines are line based operations
but actually I have just discovered that I should have been using the > sign for indentation on a line based operation.
so not really sure what the use case is for visual block then
although seems like in visual block mode you can also use this indentation sign

Ok so I was doing a little bit of work to be able to use neovim with claude.
this led me down the path of actually being comfortable interacting with neovim and its plugin manager lazy.
I forked the modular version of kickstart and it was very easy to get set up with.

I'm not sure how it works but anything in the lua/ directory is automatically availabe to be required within lua.
Need to look into how lua itself actually comes with neovim.

