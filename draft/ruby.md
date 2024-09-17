# Ruby (some of the more interesting parts) 
Discuss some of the key features
- what are symbols
- discuss that what MRI is and YARV
- Blocks in ruby (Passing execution control and how it works)
- There is like the pretzel operator or whatever too
- What is the enumerable class
- Inheritance in Ruby (Multiple inheritence is somewhat available via modules)
- The Class hierarchy diagram or whatever it's called
- chat about the metaprogramming aspects a little and reference Paolo Perrotta's book

Some of the good reaources were the rubyapi.org documentation for exploring the fratures of the language.

I wanted to have a more solid understanding of the inner workings of ruby and so I did up the note on ruby loading. This was a means of clarifying the process for the interpreter getting access to additional ruby written in gems.

There are four main ways in which Ruby code can be loaded at runtime.

Load
Using the Kernel#load method will run the contents of the file it is pointing to every time. This could be useful if you want to pick up any changes to a file while the program is running but it isn’t the most common use case. If the file neither starts with an absolute or relative file location then $LOAD_PATH, which is an array of absolute paths, is checked.

Sidenote:
The name $LOAD_PATH is a reference to the Unix environment variable $PATH, which also stores a list of directories. Just as Unix will loop through $PATH to find the executable for a given command, Ruby will loop through $LOAD_PATH to find a ruby file with the given name.

Require on the other hand only loads the argument provided the first time that it encounters the reference. This is a more common use case than load and prevents files such as gems from being reloaded multiple times. However, there is a slight quirk to the implementation of require as in most ruby applications the RubyGems class will be present in the $LOADED_FEATURES variable which means that the Kernel#require method will be overridden with a RubyGems implementation.

The default path of loading a file will be followed but if $LOAD_PATH throws a LoadError then the Rubygems implementation will check if the error message ends with the argument that was passed to require. If so, it will try to activate the gem (This can be managed by a ruby version manager such as RVM to store installed gems) and add the directories specified in that gems gemspec file with the require_paths option which is typically the lib directory.

It then tries to require the gem again now that its lib directory has been added to the load path. 

Sidenote:
How ruby manages caching classes in the require method

So after that slightly more involved journey with require we can look at require_relative. This one is pretty self explanatory as it loads files relative to the file in which it was invoked and will throw an error if that relative path does not exist.

The final loading method which I am going to cover is autoload. The purpose of autoload is to speed up initialisation by lazily loading files. It takes two arguments: a module and a filename. It registers a filename to be loaded the first time that the module is referenced in the application. It will then load the file using the Kernel#require method under the hood.

Sidenote:
Rails implementation overrides ruby's autoload method to prevent the need to specify the file path for the constant which has been referenced.

This is essentially a combination of the following articles for my own understanding:
Understanding Load, Require, and Autoload - Mintbit
RubyGems Basics
Understanding ruby load, require, gems, bundler and rails autoloading from the bottom up | by cstack | Medium
How require loads a gem - Ryan Bigg

Ruby Object Model
Exploring the docs that are available at rubyapi.org my lack of hnderstanding of the class hierarchy in the ruby onject model became apparent. 
I dabbled somewhat with Paolo Perrottas Meta Programming book. The cyclical like relationship between class and Module was challenging and it was also interesting to note that all user defined classes inherit from the Object class. The other main learning I had was that there can be a disconnection between inheritance and the ancestor of an object??
These learnings from metaprogramming were all from the beginning of the book but I felt that the more advanced topics would not be the best use of my time right now and that would be better held off for a future date.

Out of Metaprogramming the main learning was a more solid understanding of the class hierarchy in the ruby object model. 
Constant lookup
Chapter 6 of Ruby under a microscope provided a detailed breakdown of constant lookup in ruby. Starting out using ruby on rails had meant that some of these features of the language were hidden using the autoloading feature of rails.

## Rails
- What is MVC at a high level
- Some of the key components of the rails frameworks
- Some of the key commands
- The startup process in rails
- The lifecycle of a request in rails
- Database chat
   - Discuss how this is configured and then it is all pretty straightforward after this

