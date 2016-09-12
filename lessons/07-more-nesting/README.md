# More Nesting

Notice how the list of links to different repositories goes away when we
navigate to a repository? What if we want the list to persist, just like
the global navigation persists?

Try to figure that out before reading on.

...

- Nest the `Repo` route under the `Repos` route.
- Then render `this.props.children` (under the unordered list) in `Repos`.


## Active Links

- import `NavLink` so we can add the `active` class name to these links
- update your list item to render the NavLink component


Notice how both the `/repos` link up top and the individual repo links are
both active? When child routes are active, so are the parents.

---

[Next: Index Routes](../08-index-routes/)
