https://tylermcginnis.com/react-router-nested-routes/

Inside of the `Topics` component, we’re assuming that the path begins with `/topics` but now it’s been changed to `/concepts`. What we need is a way for the `Topics` component to receive whatever the initial path as a prop. That way, regardless of if someone changes the parent `Route`, it’ll always just work. Good news for us is React Router does exactly this. Each time a component is rendered with React Router, that component is passed three props - `location`, `match`, and `history`. The one we care about is `match`. `match` is going to contain information about how the `Route` was matched (exactly what we need). Specifically, it has two properties we need, `path` and `url`. These are very similar, this is how the docs describe them -

`path - The path pattern used to match. Useful for building nested <Route>s`

`url - The matched portion of the URL. Useful for building nested <Link>s`

There’s one important insight in those definitions. Use `match.path` for building `nested Routes` and use `match.url` for building `nested Links`.
