# This repo may be out dated, as JIT has moved to mainline. You may still need to apply the webpack hardsource fix (and don't forget to set your `mode: 'jit'` in your new config.

# To install

```
cd phx-tailwindcssjit
asdf install # installs erlang + elixir
npm install --prefix assets
mix deps.get
NODE_ENV=development mix phx.server
visit http://0.0.0.0:4000
```

# bug with hard source webpack plugin

- uncomment HardSourceWebpackPlugin in webpack config
- Run server
- Edit lib/demo_web/templates/page/index.html.eex (change `text-<color>-800`) and save
- See page reload, text turns black (no color css generated)
- Invalidate app.css hash (add blank line)
- see new css
- Edit template, continue to see new css

Also: sometimes there is a race condition between the CSS output and the hot
reloader, sometimes you need to hard refresh the page.

https://elixirforum.com/t/using-the-tailwindcss-jit-compiler-with-phoenix/38531/8

# wip notes:

Mostly a bug with hard source webpack plugin

Fresh clone of repo, follow install instructions, performs without needing css hash invalidation.

Stop and start server, "bug" appears.

Stop, Remove cache (`rm -rf assets/node_modules/.cache`)

Start server again, all works without needing to muck with hashes.

Can just remove hard source from webpack config without much issue.

# setting up your existing phoenix project

See
https://github.com/rktjmp/phx-tailwindcssjit/compare/696a9b2a735c4a8a31c5579b3e6f55e79d442b76..HEAD
for an overview of what changes you need to apply to your project to use
tailwindcss-jit

