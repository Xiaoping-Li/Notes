There are three categories of lifecycle methods: _mounting_, _updating_, and _unmounting_.

## _Mounting_ lifecycle methods
A component `mounts` when it renders for the _first time_. This is when `mounting lifecycle methods` get called. There are three mounting lifecycle methods:
* componentWillMount
* render
* componentDidMount: gets called right after the HTML from render has finished loading. 
    * _componentDidMount_ is a good place to connect a React app to external applications, such as web APIs or JavaScript frameworks.
    * _componentDidMount_ is also the place to set timers using setTimeout or setInterval.
When a component mounts, it automatically calls these three methods, in order.


