# The Lower Decks 2.0 — Symposium Site

Static site for **The Lower Decks 2.0: A Symposium on Janeway and Open Access Publishing**, held at Dublin City University, 21–22 May 2026.

Co-organised by the Open Library of Humanities, Michigan Publishing Services, and Dublin City University Library. Sponsored by Siliconchips Services and Iowa State Digital Press.

## Pages

- `index.html` — homepage with about, programme, attendance, sponsors
- `technical-guide.html` — technical setup for the hybrid event (venue, streaming, support rota)
- `online-attendees.html` — Zoom links, Discord, voice channels, and online activities
- `in-person-attendees.html` — venue, travel, refreshments, on-the-day support
- `options.html` — supporting page

## Static assets

- `static/style.css` — site styles
- `static/tech-guide-images/` — venue and room photography
- `static/*.svg` / `*.png` — Janeway and OLH logos, hero artwork

## Local preview

The site is plain HTML/CSS with no build step. Serve the directory with any static file server, for example:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Editing

- Programme content lives inline in `index.html` (Day 1 and Day 2 schedule tables).
- Attendance links (Online and In-person guides) live in the `.about-register` block in `index.html`.
- Sponsor links live in the `.about-sponsor` block in `index.html`.
- Zoom meeting links and Discord invite live in `technical-guide.html` (Platforms section) and `online-attendees.html`.
- Times marked **TBC** in `online-attendees.html` (livestream start, Discord welcome) need filling in nearer the event.
