# Gems

Devise
- used  set up authentication within an application

Pundit

- controls the similar but distinct aspect of authorization
    - the areas of the application which an authenticated user is authorised to access

Administrate

- sets up administrative aspect of application using the models that have been defined by the user

So yeah just today learned that ~> in the gemfile is called the pessimistic operator or something along those lines

Depending on how granular you go in your declaration it will upgrade only within the scope of the last decimal.

e.g ~> 1.0.1 will not move over the 1.0 range

whereas ~> 1.2 will not move to 2.x range.

]

using bundler

- when you use bundle exec it uses the version of the gem from the gemfile
- come up with an alias for bundle exec
    - just use be GEM
    - although maybe there are quicker aliases as these are both on my left hand
    - do rubocop ?? use rubocop

cmd to use to check the current state of gems is: bundle update
