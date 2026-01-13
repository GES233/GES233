## Hi there 👋

This is RoastedChestnut(GES233).

```elixir
experiences = %{
  pbb: {~FuzzyD[2015-??-??], ~FuzzyD[2017-??-??], "PBB project",
        "DIY-CPU at VERY EARLY stage by using Minecraft RedStone/Logisim. Only some `.cric` file saved."},
  qy: {~FuzzyD[2017-??-??], :maybe_future, "QyProject",
       """
       Layered Generate Specification/Protocol. Inspired by a brainstorm in highschool.

       WIP(deprecated) codebase in https://github.com/GES233/LivestockMonitor .
       """},
  code_pv: {~FuzzyD[2019-03-??], :maybe_future, "PV, but in Code",
            "See < https://github.com/GES233/MortalDrinksElixir > ."},
  cau_urp: {~D[2023-11-16], ~FuzzyD[2024-11-20], "Participate in Research on La Maison Verte(Françoise Dolto)",
            "See < https://ges233.github.io/2024/10/After-URP/ > ."}
}

quote do
  defmodule Sigil do
    def sigil_FuzzyD(date_string, _opts), do: {:approx, date_string}
  end
  import Sigil

  def education,
    do: [ # ALL in agriculture university
      {"Animal Science", "QAU", {2019, 2023}},
      {"Public Management", "CAU", {2023, 2025}}
    ]

  def skills, do: %{
      :"post focused on" =>
        ~w(Logisim Python Flask/Quart Sanic Julia),
      mainly: ~w(Elixir Phoenix),
      little: ~w(TailwindCSS LaTeX Typst),
      newbie: ~w(JavaScript Svelte Rust Scala),
      anticipation: ~w(MinecraftModDev ESP32 Scheme) ++ ["become Vocaloid producer"]
    }

  for {id, {start_date, end_date, name, desc}} <- unquote(Macro.escape(@experiences)) do
    def projects(unquote(id)) do
      """
      #{inspect(start_date)} to #{inspect(end_date)}
      **#{unquote(name)}**
      #{unquote(desc)}
      """
    end
  end
  def projects(_), do: :future

  def bio, do: [
      blog: "https://ges233.github.io",
      mail: "████████████@████.com"
    ]

  def bibliography, do: [
      {:article, doi: "10.16431/j.cnki.1671-7236.2022.08.021", role: "ONLY participated in, NOT mainly author"},
      # <Maybe append in the future>
    ]
end
|> then(
  &Module.create(RoastedChestnut, &1, Macro.Env.location(__ENV__))
  # Why not GES233?
  # see `apps/ges233/lib/ges233.ex` in https://github.com/GES233/simple_blog_engine
)
|> Module.register_attribute(:maybe_called_tag?, accumulate: true)
|> Module.put_attribute(:maybe_called_tag?, ["It doesn't metter."])
```
