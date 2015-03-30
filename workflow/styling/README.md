Styling
-------

* For the most part, we stick to [Thoughtbot's style guide](https://github.com/thoughtbot/guides)
* *Exception*: We add blank lines at the start and end of classes & modules
* We use Hound.ci to enforce style guidelines

We prefer Sandi Metz's rules:

1. Classes can be no longer than one hundred lines of code.
2. Methods can be no longer than five lines of code.
3. Pass no more than four parameters into a method. Hash options are parameters.
4. Controllers can instantiate only one object. Therefore, views can only know
  about one instance variable and views should only send messages to that object
  (`@object.collaborator.value` is not allowed).
