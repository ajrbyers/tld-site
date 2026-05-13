# The Lower Decks 2.0: Symposium Site

Static site for **The Lower Decks 2.0: A Symposium on Janeway and Open Access Publishing**, held at Dublin City University, 21–22 May 2026.

Co-organised by the Open Library of Humanities, Michigan Publishing Services, and Dublin City University Library. Sponsored by Siliconchips Services and Iowa State Digital Press.

## Pages

- `index.html`: homepage with about, programme, attendance, sponsors
- `in-person-attendees.html`: venue, travel, refreshments, Buswells social, on-the-day support
- `online-attendees.html`: Zoom links, Discord, voice channels, T-shirt contest, online activities
- `technical-guide.html`: technical setup for the hybrid event (venue, streaming, support rota)
- `holding-slides.html`: six-slide auto-cycling holding screen for projector display at the venue
- `options.html`: supporting page

All site pages share a sticky top nav linking the four main pages.

## Holding slides

`holding-slides.html` is a self-contained six-slide deck designed to be projected during the event:

1. Hero with theme "Users & Community"
2. Sponsors and co-organisers
3. Discord invite, QR code, lunch time, and housekeeping
4. Day 1 programme with Thursday evening Buswells social
5. Day 2 programme with Friday Keynote highlighted
6. Online T-shirt contest

Cycles automatically every 8 seconds. Controls:

- Arrow keys / Space: previous, next, pause
- F: toggle fullscreen
- Hash deep links: `#1` through `#6`
- Pause state persists across reloads via localStorage

The Discord QR is `static/discord-qr.svg`, generated with the Python `qrcode` library. To regenerate after a Discord URL change:

```sh
python3 -c "
import qrcode, qrcode.image.svg
qr = qrcode.QRCode(error_correction=qrcode.constants.ERROR_CORRECT_M, box_size=20, border=2)
qr.add_data('https://discord.gg/jkYPfj6q6N')
qr.make(fit=True)
qr.make_image(image_factory=qrcode.image.svg.SvgPathImage).save('static/discord-qr.svg')
"
```

## Static assets

- `static/style.css`: site styles, including the shared `.site-nav` and all `.slide-*` rules for the holding deck
- `static/tech-guide-images/`: venue and room photography
- `static/Janeway_RGB Logo - White.svg`, `static/OLH_RGB Symbol - White.png`: organiser logos
- `static/siliconchips-services-logo.png`, `static/iastate-digital-press-logo.svg`: sponsor logos
- `static/rainbow-road.svg`: hero background
- `static/discord-qr.svg`: QR code linking to the Discord invite

## Local preview

The site is plain HTML/CSS with no build step. Serve the directory with any static file server, for example:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Editing

- Programme content lives inline in `index.html` (Day 1 and Day 2 schedule tables) and is mirrored on `holding-slides.html` slides 4 and 5: any programme change needs both updated.
- Attendance links (Online and In-person guides) live in the `.about-register` block in `index.html`.
- Sponsor and co-organiser names live both in the homepage `.about-sponsor` block and on `holding-slides.html` slide 2.
- Zoom meeting links and Discord invite live in `technical-guide.html` (Platforms section) and `online-attendees.html`. The Discord URL is also embedded in `holding-slides.html` slide 3 and in the QR code SVG.
- Livestream and Discord welcome times in `online-attendees.html` (09:30 and 09:15 Dublin / IST) are set; update if the schedule changes.
- The Buswells social is currently scheduled for Thursday evening; if it moves, update both `in-person-attendees.html` and `holding-slides.html` slide 4.
