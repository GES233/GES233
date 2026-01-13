## Hi there 👋

This is RoastedChestnut(GES233).

```elixir
quote do
  def education do
    [ # ALL in agriculture university
      {"Animal Science", "QAU", {2019, 2023}},
      {"Public Management", "CAU", {2023, 2025}}
    ]
  end

  def skills do
    %{
      :"post focused on" => ~w(Python Flask/Quart Sanic Julia),
      mainly: ~w(Elixir Phoenix),
      little: ~w(TailwindCSS LaTeX Typst),
      newbie: ~w(JavaScript Svelte Rust Scala),
      anticipation: ~w(Minecraft ESP32 Scheme)
    }
  end
end
|> then(
  &Module.create(RoastedChestnut, &1, Macro.Env.location(__ENV__))
  # Why not GES233?
  # see `apps/ges233/lib/ges233.ex` in https://github.com/GES233/simple_blog_engine
)
```
