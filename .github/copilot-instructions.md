<!--
Guidance for AI coding agents working on the security-forum-2025 repository.
Keep this file concise and focused on repository-specific patterns, workflows,
and examples so agents become productive quickly.
-->

# Copilot instructions — security-forum-2025

This is a tiny static landing site for the "Telecom Cybersecurity Forum 2025". Key facts to be aware of:

- Single-page / single-file site(s): primary files are `index.html` and `研討會活動網頁_單檔html.html`.
- No build system, package manager, or server-side code present in repository.
- UI uses Tailwind via CDN (`<script src="https://cdn.tailwindcss.com"></script>`) and Google Fonts.
- The second file contains event structured data (`application/ld+json`) — keep dates/locations in sync if editing.

What you can safely change
- Fix layout, copy, accessibility (alt attributes) and small CSS/HTML improvements in-place.
- Add assets (images, icons) under a new `assets/` directory and reference them with relative paths.
- Add lightweight progressive enhancements (small inline scripts) but avoid bundlers or introducing build steps unless the maintainer asks.

What to avoid without approval
- Do not introduce Node/npm, Tailwind compilation, or other build tooling without explicit instruction — this repository is intentionally zero-build.
- Do not change event dates/times unless the change is deliberate and documented.

Patterns & examples to follow
- Navigation: pages use anchor links to named section IDs (for example: the "about" and "agenda" sections).
	If you add or remove sections, update the header navigation in both `index.html` and `研討會活動網頁_單檔html.html` so they stay in sync.
- Repeating content: `speakers`, `agenda`, `faq` sections are duplicated between files. If you update one, update the other.
- Styling: small utilities use Tailwind classes inline. Keep modifications minimal and consistent with existing spacing and color choices (cyan-400, slate-* palette).
- Structured data: `研討會活動網頁_單檔html.html` includes Schema.org `EducationEvent`; preserve or update it if event metadata changes.

Developer workflows
- Preview locally by opening the HTML file in a browser (no server required). Example (Linux/macOS): `xdg-open index.html` or open via the editor's Live Preview.
- If you add many assets or adopt a build step, update this file with exact commands and why they were added.

Edge cases and checks
- When changing navigation anchors, ensure `id` attributes exist on target sections.
- When adding images, include `alt` text and prefer WebP/optimized sizes to keep the repo small.
- Keep character encoding as UTF-8 and preserve the `lang="zh-Hant"` attribute.

Quick examples
- Update speaker name in both files: edit the card in `index.html` and mirror the change in `研討會活動網頁_單檔html.html`.
- Add an `assets/` folder and place `logo.png`; reference it using `<img src="/assets/logo.png" alt="forum logo">`.

If unsure
- Leave a clear PR description explaining the change and why (files edited, content sync between the two HTML files, accessibility considerations).
- Ask for maintainer confirmation before adding build tooling or modifying event metadata.

Files to reference
- `index.html` — primary landing page.
- `研討會活動網頁_單檔html.html` — alternate/SEO copy with structured data.

End of file.
