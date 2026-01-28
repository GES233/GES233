## Hi there 👋

This is RoastedChestnut(GES233).

```elixir
defmodule Sigil do
  # ~FUZZYD[...] means "approximate/fuzzy date"
  def sigil_FUZZYD(date_string, _opts), do: {:approx, date_string}
end
import Sigil

defmodule RoastedChestnut do
  @moduledoc """
  > *Que le temps ne vaut que du jour où il nous est compté*
  >
  >   --Indila, Parle à ta tête
  """
  @maybe_called_tag? ["It doesn't metter."]

  def education,
    do: [ # ALL in agriculture university
      {"Animal Science", "QAU", {2019, 2023}, "Bachelor of Science in Agriculture"}, # Animal Science
      {"Public Management", "CAU", {2023, 2025}, "Bachelor of Management"} # Public Management
    ]

  def skills, do: %{
      :"post focused on" =>
        ~w(Logisim Python Flask/Quart Sanic Julia),
      mainly: ~w(Elixir Phoenix),
      little: ~w(TailwindCSS LaTeX Typst),
      newbie: ~w(JavaScript Svelte Rust Scala),
      anticipation: ~w(MinecraftModDev ESP32 Scheme) ++ ["become Vocaloid producer"]
    }

  # Timeline of things I tried to build or experiences
  @experiences %{
    pbb: {~FUZZYD[2015-??-??], ~FUZZYD[2017-??-??], "PBB project",
          "DIY-CPU at VERY EARLY stage by using Minecraft RedStone/Logisim. Only some `.cric` file saved."},
    qy: {~FUZZYD[2017-??-??], :maybe_future,  # Until today, and maybe re-activated in future
         "QyProject",
         """
         Layered Generate Specification/Protocol. Inspired by a brainstorm in highschool.
  
         WIP(deprecated) codebase: GES233/LivestockMonitor
         """},
    meowcave: {~W[2022-02-21], ~D[2024-03-01], "MeowCave",
               """
               I was removed from a small group, so I wanted to build my own site to become a site owner.

               New repos in private.
               """},
    code_pv: {~FUZZYD[2019-03-??], :maybe_future, "PV, but in Code",
              "See GES233/MortalDrinksElixir (WIP for a long time)"},
    cau_urp: {~D[2023-11-16], ~FUZZYD[2024-11-20], "Participate in Research on La Maison Verte(Françoise Dolto)",
              "See <https://ges233.github.io/2024/10/After-URP/> ."}
  }

  def projects(id) do
    case @experiences[id] do
      {start_date, end_date, name, desc} ->
        """
        #{inspect(start_date)} to #{inspect(end_date)}

        **#{name}**:
        #{desc}
        """

      nil ->
        :future
    end
  end

  def bio, do: [
      blog: "https://ges233.github.io",
      mail: "███████.█████@outlook.com" |> String.replace("█████", "roasted") |> String.replace("roasted██", "chestnut")
    ]

  def bibliography, do: [
      {:article, doi: "10.16431/j.cnki.1671-7236.2022.08.021", role: "ONLY participated in, NOT mainly author"},
      # <Maybe append in the future>
    ]

  def git_metrics, do: GitHubUserMetrics.query(30802664, :all, theme: :terminal)
end
```

![](github-metrics.svg)
