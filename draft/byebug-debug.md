# Debugging with Byebug
This is like a nicer debugger for developing in ruby with a few more features I believe.


Questions:
- Need to look through the pry-byebug docs
- Don't now what the current stack frame is
- or what the callstack navigation is in general

frame is normally like the executing method can move to the next line in the same frame using next.

step moves into any invoked methods outside of the current frame if you want to dive in a bit deeper.

finish - execute until current stack frame returns
continue - completes the entire execution

This is pretty nice but really I should probably just use the debug gem from ruby instead.
