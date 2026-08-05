repo: juanfernandogarcia/portfolio
branch: main
path: (repo root)

## Last sync
date: 2026-08-03T00:00:00Z
commit: (none — repo was empty at first publish)

### Updated in this project
- Static export generated in `site/`: `index.html`, `project.html`, `_ds/`, `support.js`, `image-slot.js`, `.nojekyll`
- Portfolio home: EN/FR/ES switch, sticky Contact/Share bar, CV, 5 project entries, About + hobbies accordion, share sheet
- Project case study page with swipeable media gallery (4 image slides + 1 video slide)
- Publish target: GitHub Pages, branch `main`, folder `/` → https://juanfernandogarcia.github.io/portfolio

## Screen map
| Screen | Source in this project | File in repo |
| --- | --- | --- |
| Portfolio home | Portfolio.dc.html | index.html |
| Project case study | Project Page.dc.html | project.html |
| Design system tokens | _ds/modernist-.../styles.css | _ds/modernist-.../styles.css |

## Notes
- `.nojekyll` is required: GitHub Pages runs Jekyll by default, which ignores folders starting with `_` (it would drop `_ds/`).
- `cv.pdf` (CV download button) and `media/project1.mp4` (video slide) are not in the repo yet — add them at the repo root and in `media/`.
