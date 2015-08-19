## Navigator

Navigator is a component used to transition between different scenes in your app, much like React Router.

Navigator can be passed a number of props to customise it:
* configureScene: an optional function that allows configuration about scene animations and gestures. It is invoked with the route and returns a scene configuration object.
* initialRoute: the route for the Navigator to start on. A route is an object that the navigator will use to identify each scene to render. if initialRouteStack is provided as a prop, initialRoute must be an item in it. Defaults to the last item in the route stack.
* initialRouteStack: a set of routes to initially mount. If initialRoute is not provided as a prop, initialRouteStack is required. Otherwise, defaults to an array only containing the initialRoute.
