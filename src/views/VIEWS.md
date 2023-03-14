# Views

This directory contains all your UI files. It is divides into sub-directories based on the atomic design pattern. Its sub-directories are:

```
views/
    atoms
    molecules
    components
    wrappers
    pages
```

## atoms
`atoms` contain the smallest UI elements. Any element that doesn't take props is an atom

## molecules
`molecules` contains elements that take props but do not have their own state internally. A molecule typically renders its UI based on the props that are passed into it

## components
`components` contains elements that have their own state and manage their own internal state. If an element has `useState<T>()` or `useSelector()` inside it, it is a component

## wrappers
`wrappers` are JSX elements that are used to wrap other components. A wrapper usually has a prop named **children** in its definition.

If you have a wrapper named `NavigationLayout` defined with the code below

```
export default function NavigationLayout({ children }: PropsWithChildren<NavLayoutProps>): JSX.Element {
  return (
    <div className="nav-layout">
      {children}
    </div>
  )
}
```

it will be used to wrap other JSX elements and you can use it to wrap another JSX element named `ElementWeWillWrap` like this:

```
<NavigationLayout>
  <ElementWeWillWrap />
</NavigationLayout>
```

**Any element that is used like this 👆 should live in the `wrappers` directory**

## pages
A page is an entire screen. It's literally a web page. Only one page can be displayed in the browser window at a particular time