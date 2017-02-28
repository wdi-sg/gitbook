# Components

## Abstraction

To recap, components are one of the key features of React as they facilitate composition, maintenance and reusability of isolated pieces of UI:

* Components can be pieced together in various permutations
* Changes can be made to a particular component easily, without having to make consequent changes to other components
* Components can be used repeatedly in various other components of an app

Different parts of an app's view can thus be abstracted with great flexibility, nested within one another as components.

![alt tag](https://cdn.css-tricks.com/wp-content/uploads/2016/03/brad-westfall-2.svg)

[Source](https://cdn.css-tricks.com/wp-content/uploads/2016/03/brad-westfall-2.svg)

## Naming components

Because components can be reused repeatedly anywhere in an app, one convention is to name a component's props from that component's perspective, rather than that of its parent. This makes sense as the component's parent may vary,, depending on the context in which it is used within the app.

Consider the example of an Avatar component within a Post component of an app:

~~~~
function Post(props) {
  return (
    <div className="Post">
      <div className="AuthorInfo">
        {props.author.name}
      </div>
      <Avatar user={props.author} />
      <div className="PostContent">
        {props.text}
      </div>
    </div>
  );
}
~~~~
While the Avatar component will be used with the Post component's 'author' prop as an input, the Avatar component's props should be named as those of a 'user' rather than an 'author':

~~~~
function Avatar(props) {
  return (
    <img className="Avatar"
      alt={props.user.name}
      src={props.user.url}
    />
  );
}
~~~~
This follows from the fact that the Avatar component could be used elsewhere in the app, within a component with props other than an 'author' prop.

[Further reading](https://facebook.github.io/react/docs/components-and-props.html#extracting-components)

## What should be a component?

Literally every piece of UI could be defined as a component, to the greatest level of granularity:

![alt tag](https://facebook.github.io/react/img/blog/thinking-in-react-components.png)

[Source](https://facebook.github.io/react/docs/thinking-in-react.html#step-1-break-the-ui-into-a-component-hierarchy)

But this might not be necessary for the purposes of the app you are building. 2 helpful guidelines for what parts of the UI should be defined as components are:

* Any part of the UI that will be reused repeatedly, e.g. buttons, panels, avatars, etc

* Any part of the UI that is complex, e.g. the app, a feed story, comments, extracting-components

## Components as pure functions

All React components must act like pure functions with respect to their props, i.e.:

* Components must not change their inputs

* Components must always return the same result for the same inputs

But application UIs are increasingly dynamic and change over time. These requirements are instead met with state.

[Further reading](https://facebook.github.io/react/docs/components-and-props.html#props-are-read-only)
