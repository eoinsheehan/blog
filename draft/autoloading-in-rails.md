ok so its probably time to look tk get this sorted as its pretty straightforward really.

zeitwerk in rails takea care of autoloading.
and what does that actually mean?

need to confirm two elements but it sets autoloads (check and confirm what autolaod means) for all subdirectories of the app and lib folder.

exclusions can be added in the application.rb file.

it does have small implications for the naming conventions as it expects subdirectories to use modules for namespacing.

then voila you have access to all the constants your heart desires without a raft of require statements at the top of your file.

however there is also a slight implication for constant lookups in rails as a result.
rubys lookup moves up through the ancestors of the class in question.

But something a little different is required to trigger the autoload of classes outside of the regular lookip I believe - check

quick note on the regular constant lookup as taken from Ruby under a microscope here..