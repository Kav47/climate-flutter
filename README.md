# Clima ☁

## Our Goal

The objective of this tutorial is to learn about asynchronous programming in Dart. We'll look at how to carry out time consuming tasks such as getting device location and networking to get data from the internet. 


## What you will create

We’re going to make a weather app inspired by the beautiful designs made by [Olia Gozha](https://dribbble.com/shots/4663154-). By the end of the module, you'll be able to find out the live weather data in the current location of the device as well as the weather for any city you can think of!

![Finished App](https://github.com/londonappbrewery/Images/blob/master/clima-demo.gif)

## What you will learn

- How to use Dart to perform asynchronous tasks.
- Understand async and await.
- Learn about Futures and how to work with them.
- How to network with the Dart http package.
- What APIs are and how to use them to get data from the internet.
- What JSONs are and how to parse them using the Dart convert package.
- How to pass data forwards and backwards between screens using the Navigator.
- How to handle exceptions in Dart using try/catch/throw.
- Learn about the lifecycle of Stateful Widgets and how to override them.
- How to use the Geolocator package to get live location data for both iOS and Android.
- How to use the TextField Widget to take user input.


>This is a companion project to The App Brewery's Complete Flutter Development Bootcamp, check out the full course at [www.appbrewery.co](https://www.appbrewery.co/)

### Notes

- [AVOID type annotating initialized local variables.](https://dart.dev/guides/language/effective-dart/design#avoid-type-annotating-initialized-local-variables)
- `var` is akin to auto in C++ (and some c), `let` in many languages like rust, kotlin, etc It says "there's gonna be a variable there, there's no type written down but figure it out when you go compilin'"
- `dynamic` is "there's gonna be a variable there, there's no type at all just take anything fam"
- [Dart docs on async and await](https://dart.dev/codelabs/async-await)
- [async exmple in dart](scratch.dart)

#### Widget Lifecycles

##### 1. Stateful
- build

##### 2. Stateless
- initState - It gets called first
- build - During execution and other
- deactivate - Once the widget gets destroyed

#### Overall

1. createState(): When the Framework is instructed to build a StatefulWidget, it immediately calls createState()
2. mounted is true: When createState creates your state class, a buildContext is assigned to that state. BuildContext is, overly simplified, the place in the widget tree in which this widget is placed. Here's a longer explanation. All widgets have a bool this.mounted property. It is turned true when the buildContext is assigned. It is an error to call setState when a widget is unmounted.
3. initState(): This is the first method called when the widget is created (after the class constructor, of course.) initState is called once and only once. It must called super.initState().
4. didChangeDependencies(): This method is called immediately after initState on the first time the widget is built.
5. build(): This method is called often. It is required, and it must return a Widget.
6. didUpdateWidget(Widget oldWidget): If the parent widget changes and has to rebuild this widget (because it needs to give it different data), but it's being rebuilt with the same runtimeType, then this method is called. This is because Flutter is re-using the state, which is long lived. In this case, you may want to initialize some data again, as you would in initState.
7. setState(): This method is called often from the framework itself and from the developer. Its used to notify the framework that data has changed
8. deactivate(): Deactivate is called when State is removed from the tree, but it might be reinserted before the current frame change is finished. This method exists basically because State objects can be moved from one point in a tree to another.
9. dispose(): Dispose is called when the State object is removed, which is permanent. This method is where you should unsubscribe and cancel all animations, streams, etc.
10. mounted is false: The state object can never remount, and an error is thrown is setState is called.

[More in this picture](lifeCycle.png)

- `value ?? alternativeValue` means if `value` is null, then take the value of `alternativeValue`
- Can only await on method that returns future
