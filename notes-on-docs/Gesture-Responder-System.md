#Gesture Responder System

[Documentation](https://facebook.github.io/react-native/docs/panresponder.html#content)

#### Gesture Recognition
- Much more complicated than on web. App has to decide what a users intentions are based on a series of multiple simultaneous touches of different length. Complicated!

- The responder system acting on behalf of the app must negotiate these interactions and delegate them to the correct components. Check out [`ResponderEventPlugin.js`](https://searchcode.com/codesearch/view/66807738/) for further details.


#### We must take not of best practices in UX:

 - Feedback/highlighting- show the user what is handling their touch, and what will happen when they release the gesture
 - Cancel-ability- when making an action, the user should be able to abort it mid-touch by dragging their finger away

#### Responder Lifecycle

In each view you will need to set up methods to decide whether it will be the touch responder, passing on this responsibility etc. The deepest nodes will becomes touch responders but their are methods for a parent to capture this responsibility.

[Responder Lifecycle](https://facebook.github.io/react-native/docs/gesture-responder-system.html#responder-lifecycle)

#### TouchableHighlight and Touchable

If responder system too complicated each component can decide whether it is `Touchable` or `TouchableHighlight`
(like anywhere where you would use a button or link on web)


#### PanResponder

For higher-level gesture interpretation, check out [PanResponder](/react-native/docs/panresponder.html).

This an API which has handled many of the complicated interaction and giving methods to be called upon their occurrence.
