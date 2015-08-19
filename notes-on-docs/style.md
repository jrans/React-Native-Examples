#Notes on React Native docs

##Style

React Native doesn't implement CSS but instead relies on JavaScript to let you style your application.

###Problems with CSS at scale

* Global namespace - CSS throw loads of stuff into the global namespace. Bad idea!
* Dependencies - ?
* Dead Code Elimination
* Minification
* Sharing Constants - Sharing constants between css and js is a bad idea but sometimes nessisary i.e. if you change a * stype property with JS.
* Non-deterministic Resolution - if you load in files asynchronoursly, you have no control over the order of you styles and cannot be sure of presendence. 
* Isolation - If we are modifying the styles from a base and that changes, our component style may break in the future.

###React Solution

React solves most of this by applying styles inline. This works as:
1) We're not writing the styles 'inline', we give a reference to a file that's somewhere else in the file. 

2) Style is a better name than class. You want to style the element not class it. 

3) Importantly, we are not applying the style directly, we are using React virtual DOM and this is being diff-ed the same way elements are. 




* Global namespace -  All styles are local JS variables and you can export them if you need to,
* Dependencies -  You can use a module system like CommonJS/AMD
* Dead Code Elimination -  Most styles are local variables that linters/minifiers can remove
* Minification - Use Closure Compiler or Ugligyjs...
* Sharing Constants - Everything is JS
* Non-deterministic Resolution + 
* Isolation - These both get solved but defining a new style attribute on an obect via React propTypes

```
propTypes: {
  isDepressed: React.PropTypes.bool,
  style: React.PropTypes.object,
},

<div style={m{
  styles.container,
  this.props.isDepresses && styles.depressed,
  this.props.style
)} />
```

```
propTypes: {
  isDepressed: React.PropTypes.bool,
  color: React.PropTypes.string,
},

<div style={m{
  styles.container,
  this.props.color && {color: this.props.color},
  this.props.isDepressed && styles.depressed
)} />
```

We want to add the depressed style only if the button is actually depressed. To do that, we define a new attribue isDepressed on the object via React propTypes. Then, we're going to use a simple JavaScript function that merges all the objects from last to first and ignores falsy values. No more errors becasue of packaging.
```
function m(){
  var res = {};
  for (var i = 0; i < arguments.length; ++i) {
    if (arguments[i]) {
      Object.assign(res, arguments[i]);
    }
  }
  return res;
}
```

###Declare Styles

Like this:
```
var styles = StyleSheet.create({
  base: {
    width: 38,
    height: 38,
  },
  background: {
    backgroundColor: '#222222',
  },
  active: {
    borderWidth: 2,
    borderColor: '#00ff00',
  },
});
```
StyleSheet.create is optional but usefule as ensures that the values are immutable and opaque by transforming them into plain numbers that reference an internal table. By putting it at the end of the file, you also ensure that they are only created once for the application and not on every render.

For layout, React Native implements Flexbox.

###Using Styles 

All the core components accept a style attribute.
```
<Text style={styles.base} />
<View style={styles.background} />
```
They also accept an array of styles.`
```
<View style={[styles.base, styles.background]} />
```
The behavior is the same as Object.assign: in case of conflicting values, the one from the right-most element will have precedence and falsy values like false, undefined and null will be ignored. A common pattern is to conditionally add a style based on some condition.
```
<View style={[styles.base, this.state.active && styles.active]} />
```
###Pass Styles Around 

You can let a call site customize the style of your component children by passing styles though props. Use View.propTypes.style and Text.propTypes.style in order to make sure only styles are being passed.

```
var List = React.createClass({
  propTypes: {
    style: View.propTypes.style,
    elementStyle: View.propTypes.style,
  },
  render: function() {
    return (
      <View style={this.props.style}>
        {elements.map((element) =>
          <View style={[styles.element, this.props.elementStyle]} />
        )}
      </View>
    );
  }
});

// ... in another file ...
<List style={styles.list} elementStyle={styles.listElement} />
```




