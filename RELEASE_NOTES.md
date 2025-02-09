# Release Notes


## 6.3

This version bumps macOS to 11.

### ✨ New features

* `TutorialPageView` now supports macOS.



## 6.2

This version bumps Swift to 5.9.

This version (once again) makes the `Tutorial` type non-generic, and adds a `GenericTutorial` for the rare use-cases where a generic type is needed. This will once again make it possible to add static properties to the `Tutorial` type, to define app-specific values.  

### ✨ New features

* `GenericTutorial` can be used for generic use-cases.
* `Onboarding` has new static builders for various types.

### 💡 Behavior changes

* `TutorialPageView` has one initializer for `Tutorial` and one for `GenericTutorial`.

### 💥 Breaking changes

* `Tutorial` is no longer generic.



## 6.1.1, 6.1.2

### ✨ New features

* `LocalizedTutorial` now supports custom bundles.



## 6.1

### 🗑 Deprecations

* `TutorialSlideView` has been renamed to `TutorialPageView`.
* `TutorialSlideViewStyle` has been renamed to `TutorialPageViewStyle`.



## 6.0

Tutti is renamed to OnboardingKit.



## 5.1

### ✨ New features

* `CorrectBehaviorOnboarding` `requiredIncorrectAttempts` is now public.
* `DelayedOnboarding` `requiredPresentationAttempts` is now public.
* `Onboarding` `tryPresent` is now `open`.
* `Onboarding` `tryPresent` has a new delay-based variant.



## 5.0.1

This version adjusts the `TutorialPageInfo` type slightly.

### ✨ New features

* `TutorialPageInfo` now has a current page property.
* `TutorialPageInfo` `isCurrentPage` is now a property instead of a function.



## 5.0

This version bumps the minimum iOS version to 13 to allow importing SwiftUI.

### ✨ New features

* `TutorialSlideView` is a new view for presenting tutorial-based onboarding flows.
* `TutorialSlideViewStyle` can be used to style `TutorialSlideView` views.



## 4.2

This version deprecates the `OnboardingPresenter` concept and adds a `tryPresent` function to the `Onboarding` instead.

### ✨ New features

* `TutorialPageInfo` is a new struct.
* `UrlTutorialPage` is a new tutorial page with a `URL`.

### 💡 Behavior changes

* `Tutorial` is now generic to better handle custom tutorial page types.

### 📦 Dependencies

* TuttiTests no longer depends on `MockingKit`.
* TuttiTests no longer depends on `Quick` and `Nimble`.



## 4.1

This version deprecates the `OnboardingPresenter` concept and adds a `tryPresent` function to the `Onboarding` instead.

This makes the library really lightweight.

### ✨ New features

* `Onboarding` has a new `tryPresent` function that takes a custom presentation action.
* `TutorialPage` now implements `Identifiable`.

### 🗑 Deprecations

* `OnboardingPresenter` has been deprecated.
* `HintPresenter` has been deprecated.
* `TutorialPresenter` has been deprecated.



## 4.0

This major version prepares the library for Xcode 13 and SwiftUI 5.5.

This version also removes some UIKit-specific parts of the library, which makes the entire library run on all platforms. 

If you need the removed `UIKit` parts, you can grab them from the `3.1.1` release. 

### 💡 Behavior changes

* `OnboardingPresenter` no longer requires `AnyObject` conformance.

### 💥 Breaking changes

* `Tutorial` is no longer generic.
* The `UIKit` folder has been removed in this version. 



## 3.1.1

### 💡 Behavior changes

* `CalloutView` no longer depends on `UIApplication.shared`.



## 3.1

### ✨ New features

* `Onboarding` has a new `hasBeenPresented` property.



## 3.0.2

In this version adds support for presenting titles in `CalloutView`:

* `Hint` has a default, empty `title` init value.
* `Hint` implements `Equatable`.
* `Hint` has a new `hasTitle` property.
* `CalloutViewPresenter` now supports presenting titles.
* `CalloutViewPresenter` has new `titleFont` and `titleTextSpacing` properties.

The demo has been updated with new onboarding demos.



## 3.0.1

This version adds a new `ConditionalOnboarding` type. 



## 3.0

This version adds support for macOS, tvOS and watchOS, with several breaking changes. 

`UIKit` is now only required in `UIKit`-specific files, which means that the rest of the model supports watchOS and macOS.

New functionality:

* `Onboarding` has more logic.

Breaking changes:

* `Onboarding` has been disconnected from `Hint` and `Tutorial`.
* `Onboarding`, `Hint` and `Tutorial` are now base classes instead of protocols.
* `Hint` and `Tutorial` no longer implements `Onboarding`, and are only data carriers.
* `StandardOnboarding`, `StandardHint` and `StandardTutorial` have been removed.
* `DeferredOnboarding` has been renamed to `DelayedOnboarding`.
* `HintPresenter` and `TutorialPresenter` now extend `OnboardingPresenter`, but add no extra logic.
* `Tutorial` no longer have the `resourceName(for:at:)` logic, but is now built up by generic pages.
* All hint presenters now require both a hint and an onboarding.
* All tutorial presenters now require both a tutorial and an onboarding.
* `AlertingHintPresenter` now only contains presentation logic.

The demo has been rewritten from scratch, but it still UIKit-based until Xcode 12 is released.



## 2.1.1 - 2.1.4

These versions update all external test dependenies to the latest versions.



## 2.1

This version adds Xcode 11 and iOS 13 support, including support for dark mode and high contrast color variants.



## 2.0.3

This version makes the built-in presenters `open` so that you can extend them.



## 2.0.2

This version cleans up the callout view class, but has no functional changes.



## 2.0.1

This version adds accessibility texts to the standard and deferred hint. If this is set, the callout hint will work well when accessibility is enabled.



## 2.0

This version upgrades Tutti to Swift 5. The version contains no breaking changes.



## 1.5

This version has new hint and tutorial types. The `CorrectBehaviorOnboarding` is an onboarding experience that is triggered when a user performs a certain number of incorrect actions. `CorrectBehaviorHint` and `CorrectBehaviorTutorial` can be used to build user behavior-based onboarding experiences. There are, however, no demos for these new classes yet.

This version includes a bug fix by @sebbo176, that makes sure that callout hints are presented using the correct superview. This solves a problem where hints did remain on screen even when the main view controller changed.

This version has some breaking changes:

* The `DeferredHint` protocol is removed and the `StandardDeferredHint` has been renamed to `DeferredHint`. This makes the class hierarchy a lot easier to manage.
* The `DeferredTutorial` protocol is removed, and the `StandardDeferredTutorial` has been renamed to `DeferredTutorial`, just as the hints above.
* The `LocalizedTutorial` class has been removed. Instead, this functionality is now accessible by using a new `StandardTutorial` initializer.



## 1.4

This version removes presentation logic from hints/tutorials to their presenters. Instead of calling `present` on your hints and tutorials, now use the presenters.

The presenter protocols have also been refactored. The first parameter names are now implicit.

`HintPresenter` now has a `dismissAllHints()` function. It's implemented by some of the presenters, where applicable.


## 1.3

This version extends the `Hint` and `HintPresenter` protocols to make presenting a hint from a `UIBarButtonItem` possible. If you have any custom implementations of these protocols, you must extend them.

`CalloutHintPresenter` has been improved, so that it can dismiss presented hints. This fixes [issue #3](https://github.com/danielsaidi/Tutti/issues/3).



## 1.2.2

This version migrates `Tutti` to Swift 4.2 and makes it Xcode 10 ready.



## 1.2.1

In this version, the previously `public` standard deferred classes are now `open` so that you can inherit and them and override their logic in your own projects.



## 1.2.0

This is a pretty big update with some breaking changes. The most important thing to be aware of, however, is that the decision making of whether or not a hint or tutorial should be presented has been moved from the presenters to these classes.

This means that presenters are only responsible for the actual presentation from now on. They do not have any build-in decision making whatsoever. If you now ask a presenter to present a hint or tutorial, it will do so every time.

This means that if you migrate to `1.2.0`, you must modify your code to call the `present` function of your hints and tutorials, NOT your presenters. If you keep using the presenters, your hints and tutorials will always be presented.


### New features

- I have added a new `DeferredOnboarding` protocol. It lets you specify how many times `present` must be called before a hint or tutorial is actually presented.
- The `Hint` and `Tutorial` protocols have new `present` functions, which should be used from now on, if you want automated decision making to take place.
- I have added `DeferredHint` and `DeferredTutorial` protocols, that inherit the base protocols and `DeferredOnboarding`. 
- I have also added standard deferred hint and tutorial classes that inherit the standard non-deferred base classes.
- The `Onboarding` protocol has a new `shouldBePresented` prop that indicates if an onboarding item should be presented or not. It's implemented by the standard classes and overridden by the new standard deferred classes as well.


### Breaking changes

- The decision whether or not a hint/tutorial should be presented has been moved from the presenters to the hint and tutorials. You must use the `present` of the hints and tutorials instead of the presenters from now on.
- The presenter `present` functions don't have return values anymore, since they will always present the provided hint/tutorial.


### Deprecated members

- The `LocalizedTutorial` class has been deprecated and will be deleted the next time Tutti is bumped to a new minor version. Instead, use the localization-based `StandardTutorial` initializer, which does the same thing.
