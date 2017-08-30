# State

## Implications of top-down data flow

State is private, local, encapsulated within and controlled only by that component. A component's state can be passed down as props to its child components, but the children cannot update that component's state directly.

If a component is set up such that its state can be modified depending on its children's input, this can be done by way of a function passed down as a prop. If its state can be modified depending on its grandchildren's input, that function needs to be passed down another level as a prop.

This pattern can get pretty complicated depending on the complexity of the app and the extent of interdependence between components. For this reason, React could instead be used in conjunction with tools to manage state, such as [Redux](http://redux.js.org/).

## Where should state reside?

You may find that several components of your app need to reflect the same changing data. The shared state thus needs to be lifted up to a common ancestor. This should probably be their closest common ancestor, bearing in mind in particular that every additional level by which the state is lifted means another level it must be passed down as a prop.

In other words:

* Identify every component that renders something based on the state.

* Find the lowest common ancestor component.

* The state should ideally reside at that component, but can also reside in a component higher up in the hierarchy

## Of a component's data, which should be state?

DRY means that the set of mutable state required by your app should be kept to the minimum. Some guidelines to figure out which data is state are:

* If the data is passed from a parent as props, it probably is not state. State can only be modified within a component and not by its children.

* If the data remains unchanged over time, it probably is not state. Remember that state can be modified and determine how child components are rendered.

* If the data can be computed based on any other state or props within the component, it probably is not state. If you are building a todo list with an array of todo items, and want to render the todo count, it is probably unnecessary to keep a separate state variable for the count. This variable would be redundant as the array's length can be easily computed.
