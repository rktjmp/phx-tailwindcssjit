# To install

```
cd phx-tailwindcssjit
asdf install # installs erlang + elixir
npm install --prefix assets
mix deps.get
NODE_ENV=development mix phx.server
visit http://0.0.0.0:4000
```

# bug

- Run server
- Edit lib/demo_web/templates/page/index.html.eex (change `text-<color>-800`) and save
- See page reload, text turns black (no color css generated)
- Invalidate app.css hash (add blank line)
- see new css
- Edit template, continue to see new css

Also: sometimes there is a race condition between the CSS output and the hot
reloader, sometimes you need to hard refresh the page.

https://elixirforum.com/t/using-the-tailwindcss-jit-compiler-with-phoenix/38531/8
