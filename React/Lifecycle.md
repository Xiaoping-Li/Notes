There are three categories of lifecycle methods: _mounting_, _updating_, and _unmounting_.

## _Mounting_ lifecycle methods
A component `mounts` when it renders for the _first time_. This is when `mounting lifecycle methods` get called. There are three mounting lifecycle methods:
* **componentWillMount**

* **render**

* **componentDidMount**: gets called right after the HTML from render has finished loading. 
    * _componentDidMount_ is a good place to connect a React app to external applications, such as web APIs or JavaScript frameworks.
    * _componentDidMount_ is also the place to set timers using setTimeout or setInterval.

When a component mounts, it automatically calls these three methods, in order.

## _Updating_ Lifecycle Methods
The first time that a component instance renders, it does not update. A component updates every time that it renders, _starting with the second render_.

There are five updating lifecycle methods:

* **componentWillReceiveProps**: comparing incoming **props** to current **props** or **state**, and deciding what to render based on that comparison.

* **shouldComponentUpdate**: automatically receives two arguments: `nextProps` and `nextState`. It’s typical to compare `nextProps` and `nextState` to the current `this.props` and `this.state`, and use the results to decide what to do. Should return either `true` or `false`.
   * If `shouldComponentUpdate` returns `true`, then nothing noticeable happens. 
   * But if `shouldComponentUpdate` returns `false`, then the component will not update! None of the remaining lifecycle methods for that updating period will be called, including `render`.
   * The best way to use `shouldComponentUpdate` is to have it return `false` _only under certain conditions_. If those conditions are met, then your component will not update.
   
* **componentWillUpdate**: receives two arguments: `nextProps` and `nextState`. You cannot call `this.setState` from the body of `componentWillUpdate`! The main purpose of `componentWillUpdate` is to interact with things _outside_ of the React architecture. If you need to do `non-React` setup before a component renders, such as checking the window size or interacting with an API, then `componentWillUpdate` is a good place to do that.

* **render**: belongs to two categories: _mounting lifecycle methods_, and _updating lifecycle methods_.

* **componentDidUpdate**: automatically gets passed two arguments: `prevProps` and `prevState`.
   *  `prevProps` and `prevState` are references to the component’s props and state before the current updating period began. You can compare them to the current `props` and `state`.
   * `componentDidUpdate` is usually used for interacting with things _outside_ of the React environment, like the browser or APIs. It’s similar to `componentWillUpdate` in that way, except that it gets called _after_ render instead of _before_.

Whenever a component instance updates, it automatically calls all five of these methods, in order.


