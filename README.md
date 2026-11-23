# world-news-2026-11-22

[![make.fun · news-image-20261122](https://make.fun/badge/news-image-20261122.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![rank](https://make.fun/badge/news-image-20261122/ricaiueo/world-news-2026-11-22/rank.svg)](https://make.fun/bounty/news-image-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![reward](https://make.fun/badge/news-image-20261122/ricaiueo/world-news-2026-11-22/reward.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)

A printed-newspaper front page summarising the world news of Sunday
22 November 2026.

`main.py` writes `entry.png` to the output directory. The image is rendered
ahead of time and committed here, so the run uses only the standard library,
touches no network, and writes the same bytes every time. Before writing, the
program checks the committed file is a whole PNG within the bounty's caps.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out python3 -P -s main.py
```

## The stories

Every headline, figure and location comes from reporting datelined
22 November 2026. Nothing is invented. Several tolls were contested that day,
and where outlets disagreed the page says so rather than picking a number.

| # | Desk | Story | Figure | Source |
| --- | --- | --- | --- | --- |
| 1 | War | Drones kill four in Khartoum, damage a UN compound | 4 killed | Sudan Tribune, AFP |
| 2 | Energy | Tankers hit in Hormuz as Iran strikes Bahrain | 2 injured at Sitra | RTE, Arab News |
| 3 | Climate | COP31 ends with no mention of fossil fuels | 44 hours over | Al Jazeera |
| 4 | War | Drone hits a five-storey block at Dymer | counts differ | wires |
| 5 | Sea | Russian corvette hit by sea drones at Benghazi | Merkury sank | Al Jazeera |
| 6 | Formula 1 | Verstappen wins a wild Las Vegas Grand Prix | top five in 3s | Formula1.com |
| 7 | Politics | Democrats take their largest House majority since 1992 | since 1992 | Al Jazeera |

Story 4 carries no toll. Reported drone counts ran 148 to 186 and casualty
figures ranged widely through the day, so the chart shows both counts and
labels them as differing rather than asserting one.

## Design

Portrait broadsheet, designed at 1200x1700 and rendered to 723x1024 — the
bounty caps entries at 1024x1024 px, so the page keeps its proportions at a
legal size. Drawn at 2x device scale and downsampled so the type stays crisp.

Newsprint paper `#F1ECE1`, ink `#161412`, a single vermilion accent `#D2381E`.
Playfair Display for headlines, Source Serif 4 for body, IBM Plex Mono for
labels. Columns are divided by hairline rules, not cards. The world map is
real country geometry (Natural Earth via `world-atlas`, drawn with `d3-geo`),
the illustrations are flat shapes over an SVG halftone pattern, and an
`feTurbulence` grain sits over the whole page.

## Rebuilding the image

`tools/poster.html` is the poster; `tools/render.py` shoots it with headless
Chrome and writes `entry.png`. Development tools only — they need Chrome and
Pillow, and the graded entry never runs them. `tools/vendor/` holds pinned
copies of d3, topojson-client and the Natural Earth atlas.
