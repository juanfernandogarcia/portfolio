# Portfolio — Juan Fernando Garcia

Static site served by GitHub Pages.

- `index.html` — portfolio home (EN / FR / ES)
- `project-01.html` … `project-05.html` — one page per project (03 = cooling tower, the rest are blank templates)
- `project.html` — redirect kept for old links
- `media/` — images baked out of the design files; the portrait is preloaded for a fast, stable first paint
- `cv.pdf` — CV download target
- `_ds/` — design system stylesheet and bundle
- `.nojekyll` — required so GitHub Pages serves the `_ds/` folder

Regenerate this folder from the `.dc.html` sources whenever text or images change.
The build strips every `data-editor-only` block (the Add photo / Remove photo
controls), so the published pages never carry them. Beyond that it does three
things for every one of the six pages: rewrite the
`.dc.html` links to the `.html` names, add `src="media/<slot-id>.<ext>"` to each
filled image slot, and inject the portrait preload on `index.html`. Rebuild all
six pages together — a partial rebuild drops the photos.
