# Fantasy Football Leverage Chart

Playoff odds for every team in a Sleeper or ESPN league: now, with a win this week, and with a loss this week.
Styled after the NFL playoff leverage charts by mrcaseb.

Everything runs in the browser. There's no server and no build step.

## Use it

1. Open the page and enter a Sleeper username, or paste an ESPN league link (or its `leagueId` number).
2. Pick a league. ESPN leagues stay in the list until you remove them with ×.
3. Optional: open **Playoff rules** to match your league's format, then **Apply rules**.
4. Use **Copy chart as PNG** to paste the chart into a group chat, or **Copy share link** to send the page.

The share link includes the username, league and playoff rules, so everyone who opens it sees the same chart.
The last username, league and rules are also remembered in your browser (`localStorage`).

## ESPN leagues

- **Public leagues** load for anyone.
- **Private leagues** load through your own ESPN sign-in, with no token or server:
  the page links to the league's data on ESPN, you copy that page (while signed in to ESPN)
  and paste it back into the chart page. The data stays in that browser tab only, so share the
  chart as a PNG. Repeat the steps to refresh the numbers.
  (A pasted token can't work from a static site: ESPN accepts sign-in only as cookies, and a web page
  can't attach another site's cookies.)
- Projections: Sleeper's weekly projections for every remaining week, matched to ESPN players by
  name, position and NFL team and scored with the ESPN league's scoring settings. Defenses use Sleeper's
  standard defense points. Any player who can't be matched falls back to ESPN's projection.

## How the odds work

- Each team's expected score each remaining week is the best lineup its current roster can field,
  using the platform's player projections scored with the league's own settings.
  Players on bye or ruled out are left out.
- Week-to-week spread comes from how much each team's scores have varied this season.
- 50,000 simulated seasons. Leagues with a median game count it every week.
- Playoff spots are filled in order: top teams in each division, then best remaining records
  (ties broken by points for), then most remaining points for.
- **x** / **y** / **e** replace a percentage once a team has mathematically clinched a playoff spot,
  clinched its division, or been eliminated, based on records alone.
  These letters never show early, but they can show up a week later than the earliest possible moment.

If projections can't be loaded, it falls back to each team's scoring average so far.

## Publish with GitHub Pages

Settings → Pages → Build and deployment → Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)**.
The site will be at `https://lsands65.github.io/fantasy-football-leverage-chart/`.

To try it locally, serve the folder (opening `index.html` as a file blocks the font loading for image export):

```
python3 -m http.server
```

Fonts: Rubik and Roboto Condensed (SIL Open Font License), subset to Latin.
