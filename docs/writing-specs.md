# Writing specs

Atom uses [Jasmine](http://jasmine.github.io/2.0/introduction.html) as its spec framework. Any new functionality should have specs to guard against regressions.

## Create a new spec

[Atom specs](https://github.com/atom/atom/tree/master/spec) and [package specs](https://github.com/atom/markdown-preview/tree/master/spec) are added to their respective `spec` directory. The example below creates a spec for Atom core.

0. Create a spec file

  Spec files **must** end with `-spec` so add `sample-spec.coffee` to `atom/spec`.

0. Add one or more `describe` methods

  The `describe` method takes two arguments, a description and a function. If the description explains a behavior it typically begins with `when` if it is more like a unit test it begins with the method name.

  ```coffee
  describe "when a test is written", ->
    # contents
  ```

  or

  ```coffee
  describe "Editor::moveUp", ->
    # contents
  ```

0. Add one or more `it` method

  The `it` method also takes two arguments, a description and a function. Try and make the description flow with the `it` method. For example, a description of `this should work` doesn't read well as `it this should work`. But a description of `should work` sounds great as `it should work`.

  ```coffee
  describe "when a test is written", ->
    it "has some expectations that should pass", ->
      # Expectations
  ```

0. Add one or more expectations

  The best way to learn about expectations is to read the [jasmine documentation](http://jasmine.github.io/2.0/introduction.html#section-Expectations) about them. Below is a simple example.

  ```coffee
  describe "when a test is written", ->
    it "has some expectations that should pass", ->
      expect("apples").toEqual("apples")
      expect("oranges").not.toEqual("apples")
  ```

## Running specs

Most of the time you'll want to run specs by triggering the `window:run-package-specs` command. This command is not only to run package specs, it is also for Atom core specs. This will run all the specs in the current project's spec directory. If you want to run the Atom core specs and **all** the default package specs trigger the `window:run-all-specs` command.

To run a limited subset of specs use the `fdescribe` or `fit` methods. You can use those to focus a single spec or several specs. In the example above, focusing an individual spec looks like this:

```coffee
describe "when a test is written", ->
  fit "has some expectations that should pass", ->
    expect("apples").toEqual("apples")
    expect("oranges").not.toEqual("apples")
```
