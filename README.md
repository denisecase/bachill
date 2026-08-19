# Baby Animal Stress Sanctuary

A tiny, calming corner of the web: a fullscreen slideshow of baby animals that
fades and blurs from one to the next, with optional ambient background music.
Lower your stress - and breathe.

**Live:** [https://denisecase.github.io/bachill/](https://denisecase.github.io/bachill/)

---

## About

A small project exploring HTML5, CSS, and vanilla JavaScript.
Thirty public-domain / Creative Commons animal photos cross-fade on an 8-second timer,
each transition passing through a soft blur.
A single ♪ play/pause button offers a looping ambient track.

Inspired by an early online "Sanctuary" by U. Nowling,
by Jane McGonigal's TED talk on games and well-being,
and by the simple happiness of the original randomkittengenerator.com.

## Running it locally

It's a static site.
No build step, no dependencies.
Any static server works:

- **VS Code:** open the folder and use the _Live Server_ extension.
- **Python:** `python -m http.server` then open `http://localhost:8000`.

Opening `index.html` directly from disk mostly works too,
though a local server avoids browser quirks around `file://` paths.

## How it works

- **`index.html`**: page markup, the slideshow images, and two small inline
  scripts (the crossfade slideshow and the music toggle).
- **`css/`**: `reset.css`, `style.css` (layout + slideshow + button), and
  `fonts.css`.
- **`images/large/`**: the 30 full-size photos shown in the slideshow.
- **`images/thumbs/`**: thumbnail copies.
- **`music/`**: the optional background track and its license file.

The slideshow preloads every image behind a black "Loading…" screen,
then cross-fades them with a CSS blur transition using nothing but the browser's
built-in Web Animations API.
There is **no external JavaScript**: no jQuery, Modernizr, or StackBlur:
so nothing can break from a broken CDN link or a mixed-content block.

Autoplay-with-sound is blocked by modern browsers until the visitor interacts
with the page, so the music starts from the ♪ button rather than on load.

## Credits & sources

- **Images**: believed to be public domain, Creative Commons, or otherwise
  free to use. Source links are in each `<img>` tag's `title` attribute (view
  source). If attribution is missing or incorrect, please open an issue.
- **Music**: _"The Mountain"_ via [Pixabay](https://pixabay.com/) (track
  146145), under the Pixabay Content License. See the license file in
  `music/`.
- **Blur crossfade**: inspired by the Codrops "Fullscreen Image Blur Effect
  with HTML5" tutorial (2011); the original implementation has since been
  rewritten as dependency-free vanilla JavaScript.

## 2026 modernization

The site was updated to run cleanly on HTTPS / GitHub Pages:

- Replaced the HTTP-loaded jQuery and the missing Modernizr/StackBlur files
  with a self-contained vanilla-JS slideshow.
- Switched images to `object-fit: cover` with an opacity + blur crossfade.
- Moved web fonts to HTTPS.
- Replaced the old copyrighted audio with a royalty-free looping track and a
  play/pause toggle.
- Removed the retired Google Analytics (`ga.js`) snippet.

## Make Your Own

1. **Fork** it (top-right _Fork_ button on GitHub).
2. **Swap the images** in `images/large/` and `images/thumbs/`, then update the
   `<img>` list in `index.html` to match your filenames.
3. **Swap the music** (optional): drop a royalty-free `.mp3` into `music/` and
   update the `src` on the `<audio>` element in `index.html`. Find tracks at
   [Pixabay Music](https://pixabay.com/music/). Check each track's license.
4. **Enable GitHub Pages:** _Settings_ / _Pages_ / _Build and deployment_ /
   Source: **Deploy from a branch** / Branch: **`main`** / **`(root)`** /
   _Save_.
5. Wait a minute, then visit `https://<your-username>.github.io/<repo-name>/`.

## Report Issues

Found a broken link, a missing image credit, or something not loading?
[Open an issue](https://github.com/denisecase/bachill/issues).

## License / disclaimer

Unless required by applicable law or agreed to in writing, this software is
distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
either express or implied. Bundled images and music remain under their
respective original licenses.
