# Ruby loading....

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

Additions:
I also just had to clarify in my head this morning how Bundler manages the gems using the Gemfile.
Gems are installed in the rbenv (that's what we are using) ruby version in operation.
So in theory if you don't bundle install you could use the incorrect version of that.

Sidenote:
with rbenv gems are loaded into the relevant version as stated in the .ruby-version file. when you run bundle install it updates the gems that are in this location as per the Gemfile (could be good to do a quick code example here with the different stages)
Bundle has it's own implementation of the require method which does additional checking on the versioning as per the Gemfiles
