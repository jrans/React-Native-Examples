## Navigator

Navigator is a component used to transition between different scenes in your app, much like React Router.

Navigator can be passed a number of props to customise it:
* configureScene (function): an optional function that allows configuration about scene animations and gestures. It is invoked with the route and returns a scene configuration object.
* initialRoute (object) (**required if no initialRouteStack**): the route for the Navigator to start on. A route is an object that the navigator will use to identify each scene to render. if initialRouteStack is provided as a prop, initialRoute must be an item in it. Defaults to the last item in the route stack.
* initialRouteStack (array of objects) (**required if no initialRoute**): a set of routes to initially mount. If initialRoute is not provided as a prop, initialRouteStack is required. Otherwise, defaults to an array only containing the initialRoute.
* navigationBar (node): Optionally provide a navigation bar that persists across scene transitions.
* navigator (object): an optional navigator object, passed down from a parent navigator.
* renderScene (function) (**required**): function which renders the given route. Will be passed the route and the navigator object. Should contain the component to render in the body of the function.
```
function(route, navigator){
  return <MySceneComponent title={route.title} />
}
```
* sceneStyle: Styles to apply to the container of each scene.


Navigator has a number of methods:
* getCurrentRoutes(): returns the current list of routes
* jumpBack(): Jump backward without unmounting the current scene
* jumpForward(): Jump forward to the next scene in the route stack
