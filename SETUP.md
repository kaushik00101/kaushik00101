# Setup: anime GitHub profile for kaushik00101

## 1. Files
Put everything in your profile repo `kaushik00101/kaushik00101`, keeping this layout:

```
README.md
SETUP.md                  (optional, you can delete it)
assets/
  banner.svg
  status-window.svg
  skill-tree.svg
  divider.svg
.github/workflows/
  pacman.yml
  snake.yml
  summary-cards.yml
  recent-activity.yml
```

## 2. Allow workflows to push
Repo **Settings → Actions → General → Workflow permissions → Read and write permissions → Save**.

## 3. Optional token for the stats cards
The summary-cards workflow works best with a personal access token.
1. GitHub **Settings → Developer settings → Personal access tokens → Tokens (classic)**, create one with `read:user` (add `repo` if you want private contributions counted).
2. In the profile repo: **Settings → Secrets and variables → Actions → New repository secret**, name it `SUMMARY_GITHUB_TOKEN`.

Without it, the workflow falls back to the default token and some cards may not generate.

## 4. Run each workflow once
**Actions** tab, pick each workflow, **Run workflow**. Run them one at a time.

| Workflow | Creates | Where |
| :-- | :-- | :-- |
| Pac-Man contribution graph | `pacman-contribution-graph.svg` and `-dark.svg` | `output` branch |
| Snake contribution graph | `github-snake.svg` and `-dark.svg` | `snake-output` branch |
| Profile summary cards | `profile-summary-card-output/<theme>/*.svg` | `main` branch |
| Recent activity | rewrites the block in `README.md` | `main` branch |

The README is already wired to these paths. Images show as broken until the matching workflow has run once.

## 5. Customize
- **Project links:** the first two quests point at your profile. Swap in the exact repo URLs.
- **Socials:** add LinkedIn, email or others as badges next to the Portfolio badge.
- **Watchlist:** uncomment the "Currently watching" block and fill it in.
- **More arcade games:** in `pacman.yml`, set `games: "pacman,breakout,galaga"`, then add a matching `<picture>` block using `<game>-contribution-graph(.svg|-dark.svg)`.
- **Colors:** the palette is pink `#FF9EC0`, violet `#B58CFF`, night `#1A1533`. Search and replace to re-theme.

## Notes
- Raw GitHub files are cached, so cards and graphs can take a few minutes to refresh.
- The banner uses an SMIL animation. It plays on github.com in the browser but not in some email or app previews.
- The typing text, badges, skill icons, streak card and footer wave come from public hosted services and can occasionally be slow or rate-limited.
