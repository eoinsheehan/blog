# Random notes


## Notes
#### Struct vs OpenStruct 
Struct is more primative and and give you a quick means of defining a class
Struct attributes are only defined at instantiation whereas OpenStruct is able to continue to be interacted with.

#### Dependency injection
- The instance is passed to the object rather than being created within the class.
This makes it easier for testing

#### Public/Private/Protected
this is mildly interesting
Protected methods allow explicit receivers as long as the receiver is self or an instance of the same class or subclass of self.
implicit receiver is self which is the reference to the class which is in scope in that point in the application.
