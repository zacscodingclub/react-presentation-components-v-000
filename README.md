# React Presentation Components

## Objectives

1. Explain the benefits of presentation components
2. Describe how we can add interactivity to "dumb" components
3. Explain how to use stateless functional components

## Overview

We want to start by revisiting something that students have already done
(without knowing they were doing it): we want to write components that only
have a `render()` function and just accept props from their parent components.

`<input>`s are actually really great for this:

```javascript
const defaultLimit = 100
const noop = () => {}

export default class TextField extends React.Component {
  render() {
    // assume that we have some of these classes defined
    return <input className="field field-light"
             onChange={this.props.onChange || noop}
             limit={this.props.limit || defaultLimit} />
  }
}
```

Now we can do whatever we want with `<TextField />`.

Why not just have a `<input className="field field-light" {...props} />`
and call it a day? I'm sure some would disagree, but I think limiting the
`TextField` props API is a win for simplicity with the application. In the
example above, we can change the `limit` and the `onChange` handler — nothing
else. If we need to change something else, maybe we need another component or
another abstraction.

It's easy to go from here to building a `<Header />`, `<Footer />` etc.

Finally, we take away all of the crusty `class` boilerplate and show students
that we can just write, e.g.,

```javascript
export default function TextField(props) {
    return <input className="field field-light"
        onChange={this.props.onChange || noop}
        limit={this.props.limit || defaultLimit} />
}
```

## Resources

- [Stateless Functions](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions)
