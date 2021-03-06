# &lt;NavLink>

A special version of the [`<Link>`](Link.md) that will add styling attributes to the rendered element when it matches the current URL.
`<NavLink>`是  [`<Link>`](Link.md) 的一个特定版本, 会在匹配上当前 URL 的时候会给已经渲染的元素添加样式参数 

```js
import { NavLink } from 'react-router-dom'

<NavLink to="/about">About</NavLink>
```

## activeClassName: string

The class to give the element when it is active. The default given class is `active`. This will be joined with the `className` prop.
当元素匹配上当前 URL 的时候, 这个类会被赋予给这个元素. 其默认值为 `active`, 这个值会被添加到 `className` 属性的后面(追加)

```js
<NavLink
  to="/faq"
  activeClassName="selected"
>FAQs</NavLink>
```

## activeStyle: object

当元素被选中时, 为此元素添加样式

```js
<NavLink
  to="/faq"
  activeStyle={{
    fontWeight: 'bold',
    color: 'red'
   }}
>FAQs</NavLink>
```

## exact: bool

When `true`, the active class/style will only be applied if the location is matched exactly.
当值为 `true`时, 

```js
<NavLink
  exact
  to="/profile"
>Profile</NavLink>
```

## strict: bool


When `true`, the trailing slash on a location's `pathname` will be taken into consideration when determining if the location matches the current URL. See the [`<Route strict>`](../../../react-router/docs/api/Route.md#strict-bool) documentation for more information.

```js
<NavLink
  strict
  to="/events/"
>Events</NavLink>
```

## isActive: func

A function to add extra logic for determining whether the link is active. This should be used if you want to do more than verify that the link's pathname matches the current URL's `pathname`.

```js
// only consider an event active if its event id is an odd number
const oddEvent = (match, location) => {
  if (!match) {
    return false
  }
  const eventID = parseInt(match.params.eventID)
  return !isNaN(eventID) && eventID % 2 === 1
}

<NavLink
  to="/events/123"
  isActive={oddEvent}
>Event 123</NavLink>
```
