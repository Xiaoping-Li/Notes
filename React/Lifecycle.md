There are three categories of lifecycle methods: _mounting_, _updating_, and _unmounting_.

## _Mounting_ lifecycle methods
A component `mounts` when it renders for the _first time_. This is when `mounting lifecycle methods` get called. There are three mounting lifecycle methods:
* componentWillMount
* render
* componentDidMount: gets called right after the HTML from render has finished loading. 
    * _componentDidMount_ is a good place to connect a React app to external applications, such as web APIs or JavaScript frameworks.
    * _componentDidMount_ is also the place to set timers using setTimeout or setInterval.

When a component mounts, it automatically calls these three methods, in order.

## _Updating_ Lifecycle Methods
The first time that a component instance renders, it does not update. A component updates every time that it renders, _starting with the second render_.

There are five updating lifecycle methods:

* componentWillReceiveProps
* shouldComponentUpdate
* componentWillUpdate
* render: belongs to two categories: _mounting lifecycle methods_, and _updating lifecycle methods_.
* componentDidUpdate

Whenever a component instance updates, it automatically calls all five of these methods, in order.


