# Navigating with Link

Perhaps the most used component in your app is `Link`. It's almost
identical to the `<a/>` tag you're used to except that it's aware of
the `Router` it was rendered in.

Let's create some navigation in our `App` component.

1. Import Link from React Router in your App.js
2. Return a component with:
  3. an h1 that says 'React Router Tutorial'
  4. an unordered list with a role of 'nav'
  5. 2 list items
    6. next Link components inside the list items
    7. one for About and One for Repos


Now visit [http://localhost:8080](http://localhost:8080) and click the links, click back, click
forward. It works!

---

[Next: Nested Routes](../04-nested-routes/)
