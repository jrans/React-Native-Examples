# React-Native-Examples
Learn React Native by Examples

## WHAT



## WHY

#### React

The React library was created by Facebook in order ot increase engineer productivity, scalalbility, readability and all the ilities. 
* React forces the developer to break down their application into discrete composable components (which will then behave in a predictable way meaning code..)
* React is scalable and works well in big teams.

####Native 

Is difficult:

* Laying things out on a screens with varying sizes. 
* No access to react or relay
* Most importantly, recompiling the whole applicaiton for every change slowing down the developemnt velocity massively.

But necessary:

* Platform specific UI components which update regularly.
* Android or IOS (...) components can use specific native gesture recognisers.
* Web does not have a sophisticated threading model meaning we can't parallelise work onto multiple threads.


But tricky:

Because you really want to execute our JS of the main thread. Otherwise the JS might end up blocking the UI. This risks being costly as, if our JS on one thread tries to access a resource on another thread, our system has to lock (which can stall the UI). There is also an overhead with every round trip between the native environmet and the JS virtual machine. 

To get around all this we need to make sure our system passes messages across the thread boundary asynchronously and that we can batch up messages. React does this

declarative --> async --> responsive

### React Native: The best of both worlds

Since react apps are seperated into discrete components, we never need to read from the undelying rendered view. This means that the components are no blocking and can be processed on a respective thread. 

React is not tightly coupled to the DOM so can be used with javascript core (native phone engine) to render any platform specific components.

It can be adopted incrementally building on old apps as when needed.

[The article where we gout or beautiful insights](https://code.facebook.com/posts/1014532261909640/react-native-bringing-modern-web-techniques-to-mobile/)

### Learn once, write anywhere

React Native is designed to be used across devices, but each device needs its own specific components, so the idea is that as developers we can learn to use React Native, and easily create versions of our apps for different platforms using the same core logic.


## HOW

### Install

* Xcode 7.0 (This version allows for you to test your app on your own device without needing a paid devloper account)
* Home brew to instal:
 * [io.js](https://iojs.org/)
 * [watchman](https://facebook.github.io/watchman/docs/install.html)
 * [flow](http://flowtype.org/)
 Via brew instal io.js,watchman and flow respectively. Run brew update && brew upgrade to keep your programs  up-to-date.


```npm install -g react-native-cli``` 

Installs the react native command line interface. 

Use react-native-cli to initialize a working starter React Native app using the latest react-native version in npm. This package should be installed globally.

Usage:

```% npm install -g react-native-cli```

This creates your project directory in your current directory:
```% react-native init MyApplication```

## FUNdamentals

* All the native elements you will be using in your component must be required at the top of your file:
``` 
var React = require('react-native');
var {
 AppRegistry,
 StyleSheet,
 Text,
 View
} = React; 
```

* In React, there is a style object declared on each component. The style object contains entries which give the styles for each element in the component. e.g.

```
var styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  thumbnail: {
    width: 53,
    height: 81,
  },
});
```

To each element we reference it's respective enty in the style object, like so:

```
        <Image
          source={{uri: movie.posters.thumbnail}}
          style={styles.thumbnail}
        />
```

You can and should use [FlexBox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

* Declare your variables at the top of your page. 

* Component lifecycles and methods are the same as using React normally so your logic should be the same.

* [Fecthing data](https://facebook.github.io/react-native/docs/network.html) is helped by the api [Fetch](https://fetch.spec.whatwg.org/) which is avaiable in react native by default. 

* 


## WHEN

NOW!!!!!!!
