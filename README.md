# Sunfish Divers: static test site

## 1. What this is

A static test rebuild of sunfish-divers.com with a "descent into the sea" design: the top of every page is the sunlit surface, the bottom is the seabed at 42 m, and scrolling is the dive. It is nine pages of plain HTML, one stylesheet and one vanilla JavaScript file. There is no framework, no build step and nothing to install. The content is the real content of the dive centre. The logo, the PADI badge and almost all the photos are real pictures taken from the live site. Two photos are free stock photographs, and the nine dive-site cards hold labelled empty slots for photos you will supply (section 6 says where every picture came from and which are still missing). The enquiry form is a front-end demo that sends nothing.

Most visitors will come on a phone, so the site is built for phones first: it is one set of pages that adapts from 320 px wide upwards, with no separate mobile site. Section 9 says what is different on a phone, including the bar with Call, WhatsApp and Book a dive at the foot of the screen and how to remove it.

This folder is ready to be put online as a temporary test site with GitHub Pages. Section 10 gives the steps, and says what to change when the site goes live for real. Until then every page asks search engines to stay away (a `noindex` tag, line 10 of every page).

Where to find what:

| Section | Contents |
|---|---|
| 2 | How to run the site on your own computer |
| 3 | File map: every file in this folder |
| 4 | How the descent works (depth, water, zones, sea life) and where things are in the stylesheet and the script |
| 5 | The illustrations and how to change one |
| 6 | Images: where each came from, which are stock, which are still missing, how to replace one |
| 7 | To do before going live, with every `TODO` comment by file and line |
| 8 | Browser support and accessibility |
| 9 | Phones |
| 10 | Publishing on GitHub Pages, and what to do at launch |

## 2. How to run

- Double-click `index.html`. The site works straight from the folder (`file://`).
- Or open the folder in VS Code and choose "Open with Live Server" on `index.html`.
- Or put the folder on any web server, in any folder of it. Every address inside the site is relative (`css/styles.css`, `about.html`, `assets/img/...`), so the site does not care where it lives. Section 10 does this with GitHub Pages.

Two things need an internet connection:

| What | Where | Offline behaviour |
|---|---|---|
| Google Fonts (Fraunces for headings, Figtree for body text) | `<head>` of every page | Falls back to the system serif and sans-serif fonts listed in `--font-display` and `--font-body` in `css/styles.css` |
| OpenStreetMap embed | `contact.html`, line 299 | The map frame stays empty; the address is still printed beside it |

Links to Instagram, Facebook, WhatsApp and Google Maps also need a connection, as any outside link does. Everything else is local.

Other fallbacks that are built in:

- JavaScript off: all content is visible, the water is a static surface gradient, and the header sits in the normal page flow with all nine links visible. On a phone the action bar (section 9) simply stays at the foot of the screen.
- `js/ocean.js` fails to load: a small inline script in each page's `<head>` shows all content after three seconds.
- A photo file is missing: a tinted box with the file name is shown in its place (see section 6).

## 3. File map

| Path | What it is |
|---|---|
| `index.html` | Home. The full descent in five zones, the wreck scene, then Instagram strip, opening hours and contact on the seabed |
| `dive-trips.html` | A map of Cyprus with a tack for each dive site, nine local shore sites as a card grid, three wrecks as feature cards |
| `try-diving.html` | Discover Scuba Diving as a four-step timeline, photo gallery, Bubblemaker |
| `courses.html` | The PADI course ladder, five rungs, plus a link card to Specialties |
| `specialties.html` | Fourteen specialties in a filterable card grid |
| `instructor-courses.html` | Assistant Instructor Course, the four-part IDC, Course Director profile |
| `dive-centre.html` | Shop, hire, air fills, cylinder inspections, servicing |
| `about.html` | History timeline, what we offer, Course Director, Dive Packages |
| `contact.html` | Enquiry form (demo), phone, WhatsApp, email, opening hours, map |
| `README.md` | This file |
| `.nojekyll` | An empty file for GitHub Pages. It tells GitHub to publish the files exactly as they are. Leave it in place (section 10) |
| `.gitignore` | A short list of clutter that Windows, macOS and editors create (`Thumbs.db`, `.DS_Store` and the like), so that Git leaves it out of the repository |
| `css/` | Stylesheet folder |
| `css/styles.css` | All styles, in numbered sections 01 to 20 (see section 4) |
| `js/` | Script folder |
| `js/ocean.js` | All behaviour, plus the embedded sea-life drawings (the `ART` table) |
| `assets/` | Images and illustrations |
| `assets/img/` | 39 image files: 22 photos and one piece of PADI course artwork from the live site, the nine dive-site photos supplied by the owner (`site-*.jpg`), three stock photographs (`stock-*.jpg`), the share image, two logo files and the PADI badge. Each is listed in section 6 |
| `assets/svg/` | Editable sources of the illustrations |
| `assets/svg/favicon.svg` | Browser tab icon, a sunfish silhouette. Linked directly from every page |
| `assets/svg/wreck-scene.svg` | Source of the ferry wreck at the bottom of `index.html` |
| `assets/svg/seabed-dive-trips.svg` | Seabed vignette for `dive-trips.html`: bow section of a wreck with anchor chain |
| `assets/svg/seabed-try-diving.svg` | Vignette for `try-diving.html`: sunken statues and a fallen column |
| `assets/svg/seabed-courses.svg` | Vignette for `courses.html`: an admiralty anchor and chain |
| `assets/svg/seabed-specialties.svg` | Vignette for `specialties.html`: amphorae, an octopus living in one |
| `assets/svg/seabed-instructor-courses.svg` | Vignette for `instructor-courses.html`: a wreck's stern with rudder and propeller |
| `assets/svg/seabed-dive-centre.svg` | Vignette for `dive-centre.html`: a stockless anchor leaning on rocks, a coil of rope |
| `assets/svg/seabed-about.svg` | Vignette for `about.html`: a statue on a plinth among column ruins |
| `assets/svg/seabed-contact.svg` | Vignette for `contact.html`: an amphora on its side, a small anchor and rope |
| `assets/svg/creatures/` | Sources of the sea life, one file per animal |
| `assets/svg/creatures/turtle.svg` | Green sea turtle (Surface) |
| `assets/svg/creatures/bream.svg` | Silver sea bream, one fish; cloned into shoals (Surface, and as dark silhouettes at the wreck) |
| `assets/svg/creatures/parrotfish.svg` | Mediterranean parrotfish (Shallow reef) |
| `assets/svg/creatures/wrasse.svg` | Ornate wrasse (Shallow reef) |
| `assets/svg/creatures/octopus.svg` | Octopus beside a rock (Shallow reef) |
| `assets/svg/creatures/seagrass.svg` | Posidonia tuft (Shallow reef) |
| `assets/svg/creatures/moray.svg` | Moray eel in a rock crevice (The caves) |
| `assets/svg/creatures/grouper.svg` | Dusky grouper (The caves, and as a dark silhouette at the wreck) |
| `assets/svg/creatures/lionfish.svg` | Lionfish (The caves) |
| `assets/svg/creatures/jellyfish.svg` | Jellyfish (The caves) |
| `assets/svg/creatures/barracuda.svg` | Barracuda, one fish; cloned into a school (Blue water) |
| `assets/svg/creatures/amberjack.svg` | Greater amberjack (Blue water) |
| `assets/svg/creatures/sunfish.svg` | Ocean sunfish, Mola mola, the shop's namesake (the large one in Blue water; smaller ones at the Surface, in The caves and Blue water, and as a dark silhouette at the wreck) |
| `assets/svg/creatures/diver.svg` | Scuba diver with a yellow cylinder and fins, trailing bubbles (every zone; a dark silhouette at the wreck) |

The header and footer markup is duplicated in every page (between the `HEADER` and `FOOTER` comments). A change to either has to be made nine times; only `aria-current="page"` differs between pages. The logo and the PADI badge are part of that markup (section 6 (e)). The phone action bar, the block between the two `MOBILE ACTION BAR` comments just above the script tag at the foot of each page, is duplicated in the same way and is identical on all nine (section 9). So is the `<head>` (lines 3 to 48): only the title, the description and the three `og:` lines that repeat them and give the page address differ from page to page.

Nothing else is in the folder, and nothing else is needed: no build files, no packages, no hidden settings. File and folder names are all lower case without spaces, apart from `README.md`. Keep new files that way: a web server treats `Photo.JPG` and `photo.jpg` as two different files, although Windows does not (section 10).

## 4. How the descent works

### Depth

Depth follows scroll progress, 0 at the top of the page and 1 at the bottom:

```
progress = scrollY / (page height - viewport height)     0 at the top, 1 at the bottom
depth    = 42 m x progress                               inner pages
--depth  = depth / 42                                    a CSS custom property, 0 to 1
```

- On the inner pages depth is exactly that. On the home page, which has a section per zone, depth is tied to the sections instead: it reads 5, 12, 20 and 30 m exactly when the reef, caves, blue water and wreck sections reach the header, and runs evenly in between (`depthAt()` and `scrollAt()`; the section positions are measured by `hudMeasure()`). So the gauge, the water colour and the zone labels agree on every screen size.
- `frame()` in `js/ocean.js` (section 3, "Depth system") computes it. It is called through `requestFrame()` from a passive scroll listener, at most once per animation frame, and reads only `scrollY`.
- `--depth` is registered in `css/styles.css` (section 18.0) as a number that does not inherit. The script writes it each frame only on the elements whose styles use it: the layers inside `#ocean`, the gauge's fill and dot, the torch glow, the animals that are on or near the screen (`lifeDepth()`), and any element with a `data-depth` attribute (`collectDepthTargets()`). A layer that is fully faded at the current depth is skipped. `<html>` receives the value shortly after scrolling pauses (`writeRootDepth()`). To use `var(--depth)` on a new element, give it `data-depth`.
- Everything that depends on layout is measured in `refresh()` (section 11, "Boot") on load, on resize and when the page height changes, never while scrolling.
- A filter on the specialties page hides cards, so the page gets shorter. The gauge must not jump when that happens, so while a filter is on the depth is tied to the card grid: everything above the grid and everything below it keeps the depth it has on the unfiltered page, and the grid in between runs through its share of the dive more quickly (`filterMap()`). The page simply closes up; there is no stretch of empty water above the seabed.
- On phones the water and the light are driven more cheaply: see "On phones" in section 9.

### Water colour and light

All of this lives in `<div class="ocean" id="ocean">`, which is empty in the HTML and filled by `buildOcean()`. The styles are in section 18.2 of the stylesheet, and the fades are plain CSS expressions of `--depth`.

| Depth | Colour |
|---|---|
| 0 m | `#7fdbe6` |
| 5 m | `#2bb3c9` |
| 12 m | `#1286a8` |
| 20 m | `#0b5c85` |
| 30 m | `#083a5e` |
| 42 m | `#04182b` |

- `.ocean__water` is a strip four viewports tall carrying that gradient. It slides upwards as `--depth` grows, and its stops are placed so that the middle of the screen shows exactly the colour of the depth on the gauge (the top of the screen is a little shallower, the bottom a little deeper).
- Sun rays and the rippling surface line fade out by about 15 m; the sunlight glitter by about 8 m.
- Marine snow and a soft vignette appear from about 19 m.
- From about 29 m a torch glow follows the mouse (`buildTorch()`, `torchMove()`, styles in 18.5). It is for mouse pointers only.
- Bubble streams rise from the bottom of the window every few seconds, and every `.btn` gives a burst of bubbles on hover and click (`buildBubbles()`, `stream()`, `burst()`).

### Zones

Defined once, as `ZONES` and `MAX_DEPTH` near the top of `js/ocean.js`:

| Zone | Key | Depth |
|---|---|---|
| Surface | `surface` | 0 to 5 m |
| Shallow reef | `reef` | 5 to 12 m |
| The caves | `caves` | 12 to 20 m |
| Blue water | `blue` | 20 to 30 m |
| The wreck | `wreck` | 30 to 42 m |

- On the home page each zone is a `<section class="zone" data-zone="KEY" id="zone-KEY">`. Their minimum heights are set so that each section reaches the header at about its own share of the page: see "depth calibration (home)" in section 11 of the stylesheet (`--tail-rest` and the `--k-*` values). The script then makes the depth exact at each section (see "Depth" above), so these values only decide how much open water each zone gets; if the lower part of the home page (wreck teaser, wreck scene, seabed info, footer) changes height a lot, measuring `--tail-rest` again keeps the zones evenly paced.
- Inner pages have no zone sections. The same 0 to 42 m scale is simply mapped onto their own length.

### Light and dark panels

All body text sits in a `.panel` (frosted glass). `applyTones()` sets `data-tone="light"` or `data-tone="dark"` on every `.panel` and every `[data-tone-auto]` element. A panel takes its tone from the depth at which it is centred on screen: light above 13 m (`TONE_SWITCH_M`), dark below. A heading that sits directly on the water takes the tone that reads better against the lightest and the darkest water it meets on its way up the screen. White headings also carry a soft dark halo, and a navy heading whose contrast comes close to 3:1 at the foot of the screen is marked `data-halo` by `applyTones()` and carries a soft light one (section 03 of the stylesheet). The two colour sets are the "tone variables" at the end of section 01 of the stylesheet; panels are section 07. The header bar switches from light to dark glass at the same 13 m (the script toggles `.is-deep`; section 09). Colours change at once: only `transform` and `opacity` are ever animated or transitioned. The footer is always dark.

### Depth gauge

`buildHud()` adds `<nav class="depth-hud" aria-label="Depth gauge">` to the page; `hudUpdate()` keeps the reading and the zone name current; `hudMeasure()` and `goToZone()` handle the zone buttons. On the home page a zone button scrolls to its section; on inner pages it scrolls to where that depth begins. Styles are in section 18.4, in three layouts:

- 1440 px and wider: a full panel with depth, track and zone names.
- 768 to 1439 px: a narrow panel; zone names slide out on hover or keyboard focus, stay while the pointer is on them, and can be put away with Escape.
- Under 768 px wide, or a very short window: a small pill on the right edge showing the depth. Tapping it opens the zone list. The name of a zone drops out under the pill for two seconds when the dive enters it (`.is-zone-new`). It is written downwards and is exactly as wide as the pill, so the pill stays short and neither of them lies on text. The name is not shown while a form field is being filled in.
- On touch screens the zone names of the narrow panel cannot be hovered: there the name shows while the tapped zone button has the focus.

### Sea life by depth

- The `CAST` table in `js/ocean.js` (section 7) lists the animals of each zone in priority order, with size, speed and behaviour. This is where to change which animal appears where.

  | Zone | Cast |
  |---|---|
  | Surface | turtle, a shoal of bream, a diver, a second shoal of bream, a small sunfish |
  | Shallow reef | parrotfish, seagrass, a diver, octopus with seagrass, two wrasse |
  | The caves | moray, two jellyfish, grouper, a small sunfish, lionfish, a diver |
  | Blue water | the large sunfish, two divers, two smaller sunfish, a school of barracuda, two amberjack |
  | The wreck | two groupers, a shoal of bream, a diver and a sunfish, as dim single-tone silhouettes |

  How many of each list appear depends on how much water the zone has on that page; phones take at most the first half of each list. The smaller sunfish and the divers are ordinary swimmers: only the large sunfish has a lane to itself.

- `buildLife()` places them in a `.sea-life` layer that spans the whole page and sits behind the content. Each animal is put at the page position that matches its depth. It looks for open water. Headings that sit directly on the water are off limits, counting the distance an animal's parallax carries it while it is on screen: an animal that finds no clear water is tried with less parallax and is left out if text is still in the way. The marker column of a depth timeline is off limits too (a swimming animal may pass behind it; on phones, where each marker stands in the open water above its panel, no animal swims at the height of a marker), and nothing is parked behind the "Scroll to dive" pill on the home page (a swimming animal may pass behind it). Panels and photos are avoided where possible, and an anchored animal (moray, octopus, seagrass) is left out rather than shown more than a fifth hidden. The sunfish has its lane to itself, with room for the parallax of the lanes next to it. Its water is reserved before the other zones are planned, so that an animal of the zone above cannot settle in the only open water tall enough for it; and where that gives it clearly better water, the sunfish does without its parallax.
- The plan is made again when the text moves (web fonts arriving, a resize, a specialties filter), and only then.
- How many animals a zone gets depends on how much room the page gives it, so short pages show fewer. Under 700 px wide, at most half of each zone's cast is used, at a smaller size, with smaller shoals. Rays, glitter, snow and bubbles are also reduced.
- Under 700 px wide the animals have no parallax (they scroll with the page), the sunfish gets a clearing of open water to cross in (the anchored animals keep out of it), and the moving parts inside the drawings pause while the page is being scrolled. Section 9 explains why. On a phone held sideways the sunfish gets the same clearing, and is drawn no taller than three quarters of the screen so that it is seen whole.
- The layout is seeded from the page's `data-page` value, so a page always gets the same arrangement.
- Movement is CSS only (section 18.3: `slPatrol`, `slDart`, `slRoam`, `slBob`, `slDrift`). Moving parts inside the drawings (tails, fins, tentacles) use the `sf-*` classes in section 18.1.
- Animals and scenes that are off screen are paused (`.is-off`, set by an IntersectionObserver in `buildLife()` and `watchScenes()`). Everything pauses while the browser tab is hidden.

### Reduced motion

With "reduce motion" switched on in the operating system:

- Kept: the colour descent, the depth gauge, light and dark panels, and the sea life, drawn as a still life in the margins.
- Switched off: swimming, parallax, bubbles, the torch, the movement of rays, glitter and snow, the float-up of sections, smooth scrolling and the menu animation. On phones also: the sideways glide of the home wreck (it stands still and shows its middle), and the slide of the action bar and of the zone name under the depth pill (they appear and disappear at once).

The rules are in sections 17 and 18.7 of the stylesheet; the script reads the setting into `state.reduced` and rebuilds the sea life if it changes while the page is open.

### Finding your way around the two files

`css/styles.css`:

| Section | Contents |
|---|---|
| 01 Tokens | Colours, fonts, type scale, spacing, layers, tone variables |
| 02 Base, 03 Typography, 04 Layout | Resets, focus style, skip link, headings, page grid |
| 05 Small parts, 06 Buttons | Icons, depth marks, tags, wave dividers, pill buttons |
| 07 Panels and tone | Frosted-glass panels and the solid fallback |
| 08 Photos | Photo frames and the missing-file placeholder |
| 09 Header and menu | Sticky header, full-screen mobile menu, no-JS header |
| 10 to 12 Home | Hero, zones and depth calibration, seabed info |
| 13 Inner-page components | Cards, timeline, course ladder, filter chips, steps, feature grid, profile, call-to-action cards |
| 14 Forms and map | Enquiry form and map frame |
| 15 Scenes and footer | Wreck scene, seabed vignettes, footer |
| 16 Reveal, 17 Reduced motion and print | Float-up on entry, motion and print rules |
| 18 Ocean engine | Everything `js/ocean.js` creates: 18.1 `sf-*` classes, 18.2 water and light, 18.3 sea life, 18.4 depth gauge, 18.5 bubbles and torch, 18.6 menu scroll lock, 18.7 pausing and reduced motion |
| 19 Mobile action bar | The Call, WhatsApp and Book a dive bar on phones. Self-contained: see section 9 |
| 20 Dive map | The two maps of `dive-trips.html`, their tacks and the list under them: see section 6 (f) |

Rules for phones sit beside the component they change, in media queries: `(max-width: 47.99em)` is "under 768 px", `(max-width: 43.74em)` is "under 700 px" (the width below which the script also switches to its lighter phone behaviour), `(max-width: 22.49em)` is "narrower than 360 px", and `(max-height: 30em) and (orientation: landscape)` is a phone held sideways. Every phone layout is stylesheet only: the HTML is the same at every size.

`js/ocean.js`:

| Section | Contents | Main names |
|---|---|---|
| 1 | Art table | `ART` |
| 2 | Helpers and shared state | `ZONES`, `MAX_DEPTH`, `state` |
| 3 | Depth system | `measure()`, `requestFrame()`, `frame()`; on phones `LIGHT`, `lightSync()`, `waterSync()`, `calm()` |
| 4 | Water and light | `buildOcean()`, `oceanUpdate()` |
| 5 | Depth gauge | `buildHud()`, `hudMeasure()`, `hudUpdate()`, `goToZone()`, `filterMap()` |
| 6 | Tone | `applyTones()` |
| 7 | Sea life | `CAST`, `buildLife()`, `watchScenes()`; on phones `clearingApply()` and `swimWidth()` (the sunfish's clearing, and its size on a short screen) and `tourClass()`, `tourMeasure()`, `tourUpdate()` (the wreck tour) |
| 8 | Bubbles | `buildBubbles()`, `stream()`, `burst()`, `bubblesSync()` |
| 9 | Torch | `buildTorch()`, `torchMove()` |
| 10 | Site behaviour | `initMenu()`, `initReveal()`, `initPhotos()`, `initYear()`, `initFilters()`, `initForms()`, `initActionBar()` |
| 11 | Boot | `refresh()`, `scheduleRefresh()`, `init()` |

## 5. Illustrations

All the sea life, the wreck and the eight seabed vignettes are original SVG drawings made for this site. No stock illustrations or icon libraries are used. (The two stock photographs on the site are a separate matter: see section 6 (c).)

Each drawing exists twice:

| Drawing | Editable source | Copy the site actually uses |
|---|---|---|
| Sea life (13 animals and the diver) | `assets/svg/creatures/NAME.svg` | The `ART` table in `js/ocean.js`, between `/* ==ART:BEGIN== */` and `/* ==ART:END== */` (lines 39 to 57) |
| Wreck | `assets/svg/wreck-scene.svg` | `index.html`, between `<!-- WRECK:BEGIN -->` and `<!-- WRECK:END -->` (lines 290 to 292) |
| Seabed vignettes | `assets/svg/seabed-PAGE.svg` | Each inner page, between `<!-- SEABED:BEGIN seabed-PAGE -->` and `<!-- SEABED:END -->`, just above the footer |

The site does not load the files in `assets/svg` (apart from the favicon), so that it also works when opened straight from the folder. Editing a source file therefore changes nothing until the inline copy is replaced as well. As shipped, every inline copy is the same drawing as its source, with comments and line breaks removed.

Comments in the pages and in `js/ocean.js` say the inline copies are filled by an "embed tool" and should not be edited by hand. That helper was used while the site was being built and is not part of this folder. Without it, do the copy by hand as follows.

### Changing the wreck or a seabed vignette

1. Edit the source file, for example `assets/svg/seabed-courses.svg`. Open the file in a browser to check the drawing.
2. Open the matching page (`courses.html`) and find the two marker comments.
3. Delete everything between the markers and paste in the whole content of the source file. Keep both markers and the `<div>` around them.
4. On the pasted `<svg ...>` opening tag, add `aria-hidden="true" focusable="false"`.

The shipped inline copy is on one line with comments removed. That is not required: a multi-line paste with comments works the same.

Keep to these rules in scene files: the bottom strip is filled with exactly `#2b4a5e` so that it merges with the top of the footer; every `id` starts with the file name (`wreck-...`, `seabed-courses-...`); the scene is cropped at the sides on narrow screens (`preserveAspectRatio="xMidYMax slice"`), so keep what matters in the middle.

On phones a vignette is not simply cut from the middle. Each page tells the stylesheet where its subject stands and how much of the drawing a phone must show: the lines `[data-page="courses"] .seabed { --focus: 782; --span: 570; }` in section 15 of `css/styles.css`. Both numbers are in the units of the drawing, which is 1600 wide: `--focus` is the middle of the subject measured from the left edge, `--span` the width that has to fit on the screen. If you move or redraw a subject, change its two numbers and look at the page at 360 px wide. The home wreck needs no numbers: on phones it glides past from bow to stern (section 9).

### Changing a sea creature

1. Edit the source file, for example `assets/svg/creatures/bream.svg`, and check it in a browser.
2. Make a one-line copy of the file: remove the `<!-- comments -->` and join all the lines into one.
3. On the `<svg ...>` opening tag of that copy, add `aria-hidden="true" focusable="false"`.
4. Put a backslash in front of every double quote in the copy (`"` becomes `\"`).
5. In `js/ocean.js`, find the line in the `ART` table that begins `"bream": "`. Replace everything between that opening quote and the closing quote at the end of the line with your copy. Keep the comma at the end of the line.
6. Reload a page. If the water, the gauge and the sea life are all gone, the line has a syntax error (usually an unescaped quote or a stray line break); the browser console shows where.

Keep to these rules in creature files: the key in `ART` is the file name; keep `viewBox="0 0 W H"` on the root tag, as the script reads the size from it; no `id` attributes, `<defs>`, gradients or `<style>`, because each drawing is inserted several times on a page; swimmers are drawn facing right (the script mirrors them); moving parts carry an `sf-*` class and a `transform-origin` in viewBox units, and must not also have a `transform` attribute.

To change an animal's size, speed or zone, edit its entry in `CAST` instead; the drawing does not need to change.

### Other graphics

- `assets/svg/favicon.svg` is linked directly. Edit the file and that is all.
- The small interface icons and the wave dividers are written inline in the HTML and have no separate source file. The logo is no longer a drawing: it is the real logo, as two image files (section 6 (e)).

## 6. Images

`assets/img` holds three kinds of picture:

- **Real pictures from the live site**, sunfish-divers.com: the photos in (a), the PADI course artwork in (b), the logo and the PADI badge in (e).
- **Nine dive-site photographs supplied by the owner** (`site-*.jpg`), one on each dive-site card of `dive-trips.html`. See (d).
- **Three stock photographs** (`stock-*.jpg`), free to use with no attribution required, in places where there is no picture of the subject from the centre itself. They are listed in (c).

Every picture was cropped and resized for the web (JPEG, none larger than 181 KB, 3.2 MB for the whole folder).

Four things to know before launch:

- The live site does not say who took its photographs. Before going live, check that the dive centre holds the right to use each one. One picture is PADI course artwork and is listed separately in (b).
- Captions and `alt` texts say only what the live site says about a picture (its caption there, or the section it sits in) or what can plainly be seen in it. Where that was not enough to tie a picture to a place or an activity, the picture is described in general terms.
- The stock photographs do not show the centre's own dives, staff, customers or equipment. Their captions and `alt` texts describe only what is visible and name no place.
- Some slots still have no fitting picture. They are listed in (d): the nine dive-site cards, and the places where a stock photo or a general photo stands in for now.

### (a) Real photos

| File in `assets/img/` | Size (px) | Used on (caption on the page) | Where it came from on the live site | What it shows |
|---|---|---|---|---|
| `diver-and-turtle.jpg` | 800 x 1000 | index hero, try-diving gallery ("Amazing encounters") | Try Diving page gallery, `GalleryImage15.png`, captioned "Amazing encounters" | A diver giving two thumbs up beside a large sea turtle on sand and seagrass |
| `discover-scuba-diving-shoal.jpg` | 800 x 800 | index, Try Diving teaser ("Discover Scuba Diving, twice a day") | Home page Instagram block; the post reads "Discover Scuba Diving. Twice a day" | A diver with arms outstretched inside a shoal of silver fish |
| `dive-centre-front.jpg` | 1200 x 674 | index Dive Centre teaser ("The dive centre, Ayia Napa"), about hero ("At home in Ayia Napa since 1982") | Home page "Sunfish Divers Dive Centre" section and top of the Dive Centre page, `IMG_0251.jpg` | The front of the dive centre: the Sunfish Divers sign, "PADI 5 STAR IDC CENTER" and the entrance |
| `dive-centre-shop-front.jpg` | 720 x 900 | dive-centre hero ("The shop in Ayia Napa"), contact hero ("The dive centre, Ayia Napa") | Dive Centre page, under "Welcome to our dive center", `IMG_3385.jpg` | The shop front seen straight on: the sign above windows decorated with underwater scenes |
| `dive-centre-shop-interior.jpg` | 960 x 325 | dive-centre, "In the shop" ("Inside the shop") | Dive Centre page, under "Everything you need for your underwater adventure", `shop.jpeg` | A panorama of the inside of the shop: fins, masks, shelves, cabinets, wetsuits |
| `zenobia-entering-restaurant.jpg` | 800 x 800 | index Dive Trips teaser ("Entering the Zenobia's restaurant") | Courses page gallery, `GalleryImage12.png`, captioned "Entering Zenobias' restaurant" | Two divers at an opening in the overgrown hull, one lowering into it |
| `turtle-on-sand.jpg` | 400 x 400 | index Instagram strip | Home page Instagram block (no text) | A sea turtle on the sand beside a rocky reef |
| `turtle-at-zenobia.jpg` | 500 x 500 | index Instagram strip | Home page Instagram block; the post reads "Baby turtle on Zenobia wreck" | A young turtle with the wreck in the background |
| `divers-on-zenobia-boat.jpg` | 700 x 700 | index Instagram strip | Home page Instagram block; the post reads "Good morning from Zenobia" | Seven divers in wetsuits smiling on the deck of a dive boat |
| `konnos-bay-cavo-greko.jpg` | 675 x 844 | dive-trips hero ("Konnos Bay, Cavo Greko") | Dive Trips page, `LocalDivesImage.png`, captioned "Konnos Bay - Cavo Greko" | The bay seen from above past a bare tree: turquoise water and a small beach |
| `green-bay-statues.jpg` | 800 x 1000 | dive-trips "Local dives", try-diving gallery ("The statues of Green Bay") | Try Diving page gallery, `GalleryImage13.png`, captioned "The statues of Green Bay" | Statues and columns standing on the sandy seabed |
| `fish-feeding-rock.jpg` | 800 x 1000 | try-diving gallery ("Fish feeding rock") | Try Diving page gallery, `GalleryImage14.png`, captioned "Fish feeding rock" | A diver almost hidden by a dense shoal of small fish |
| `try-diving-getting-ready.jpg` | 675 x 844 | try-diving hero ("Getting ready for a first dive") | Try Diving page, `TryDiveImage.png`, captioned "Our experienced dive Instructor prepares one of the divers for their first dive" | An instructor fastening a diver's equipment before a first dive, under a blue sky |
| `bubbles-while-ascending.jpg` | 800 x 1000 | try-diving "Open to all ages" ("Bubbles while ascending") | Courses page gallery, `GalleryImage11.png`, captioned "Bubbles while ascending" | Air bubbles rising towards the sunlit surface |
| `wreck-liberty.jpg` | 1000 x 750 | dive-trips, Liberty card | Dive Trips page, `LibertyAndNemesisDivesImage.png`, captioned "Liberty Wreck" | The Liberty from above, upright on the seabed |
| `wreck-nemesis-iii.jpg` | 900 x 600 | dive-trips, Nemesis III card | Courses page gallery, `GalleryImage10.png`, captioned "Nemesis wreck" | The deck of the wreck from above, a diver beside the mast |
| `wreck-zenobia-propellers.jpg` | 1000 x 750 | dive-trips, Zenobia card ("One of the Zenobia's two propellers") | Dive Trips page, `ZenobiaDivesImage.png`, captioned "One of the 2 propellers of Zenobia Wreck" | Two divers above one of the wreck's propellers |
| `zenobia-propeller.jpg` | 800 x 1000 | specialties "On the wrecks" ("The Zenobia's propeller") | Dive Trips page gallery, `GalleryImage18.png`, captioned "Zenobia;s propeller" | A propeller of the wreck, close up, overgrown |
| `jellyfish.jpg` | 800 x 1000 | specialties "On the reef" ("A jellyfish drifting by") | Home page, picture behind "Welcome to Sunfish Divers", `medusa 09.jpg` | A large translucent jellyfish in blue water |
| `turtle-on-seagrass.jpg` | 700 x 875 | contact "Or simply talk to us" ("A turtle on the seagrass") | Contact page gallery, `GalleryImage20.png` (no caption) | A sea turtle resting on sand and seagrass |
| `diver-on-buoy-line.jpg` | 450 x 563 | courses "Your next step" ("On the buoy line") | Home page, background of the "Local dives and wreck dives" section, `MainImage.png` | A diver holding the chain beneath a buoy, in silhouette |
| `dena-asimenou-course-director.jpg` | 800 x 1000 | about, instructor-courses (profile block, no caption) | About page, section "Our course director Dena Asimenou", `100_0599.jpg` | Dena Asimenou smiling in a wetsuit on the deck of a dive boat at night |
| `og-sunfish-divers.jpg` | 1200 x 630 | all nine pages, as the share image (`og:image`, line 19). Not displayed on the pages | The same picture as `dive-centre-front.jpg` | The front of the dive centre |

Two of these are small originals and look a little soft on high-resolution screens, phones included (most phones draw two or three screen dots for every pixel of the layout): `dive-centre-shop-interior.jpg` (the live file, `shop.jpeg`, is only 960 x 325 px) and `diver-on-buoy-line.jpg` (cut from a wide banner). For the second there is a better source: the live site holds `MainImage.png` at 1920 x 720 px, and the copy used here was fetched at 1500 px wide, so the same cut from the full-size file would be about 576 x 720 px. The camera originals would be better still, and for the shop panorama only a camera original helps.

### (b) PADI course artwork

| File in `assets/img/` | Size (px) | Used on | Where it came from |
|---|---|---|---|
| `padi-idc-course.jpg` | 675 x 844 | instructor-courses hero ("PADI Instructor Development Course"). Marked with a comment on line 114 | The PADI picture at the top of the live Instructor Development Course page, `PADIInstructorDevelopmentCourseImage.png` |

**PADI course artwork from the live site: confirm usage rights before launch.** It is used only to illustrate that PADI course, as the live site does, and is not presented as a photo of Sunfish Divers' own staff or customers. The other PADI course pictures on the live site (Open Water, Advanced Open Water, Rescue, Divemaster, the specialties chart) are not used here.

### (c) Stock photographs (free to use, no attribution required)

Three slots show something there is no picture of from the centre itself. They are filled with stock photographs whose licence allows free use, commercial use included, without payment and without credit. **These photographs do not show the centre's own dives, people or equipment unless marked as located; none of the three is.** Each is marked in the HTML with a `STOCK PHOTO` comment directly before its figure.

| File in `assets/img/` | Size (px) | Used on (caption on the page) | What it shows | Source page | Author | Licence | Retrieved | Kind |
|---|---|---|---|---|---|---|---|---|
| `stock-diver-with-underwater-camera.jpg` | 800 x 1000 | `specialties.html`, beside the grid ("Camera at the ready"). Comment on line 260 | A scuba diver in mid-water holding a large underwater camera with two strobe lights, the sun bursting through the surface behind | https://www.pexels.com/photo/low-angle-shot-of-man-in-diving-gears-underwater-7001654/ | Leonardo Lamas (Pexels) | Pexels License | 2026-11-18 | Illustrative: replace with your own photo |
| `stock-two-divers-in-sun-rays.jpg` | 800 x 1000 | `instructor-courses.html`, PADI Assistant Instructor Course ("Under the sun rays"). Comment on line 177 | Two scuba divers upright in mid-water beneath bright sun rays, one in a red top facing the other, who holds out a hand | https://www.pexels.com/photo/two-scuba-divers-floating-in-depths-of-ocean-in-sun-rays-11060853/ | Carlos Jamaica (Pexels) | Pexels License | 2026-11-18 | Illustrative: replace with your own photo |
| `stock-divers-wading-into-shallow-bay.jpg` | 800 x 1000 | `index.html`, Courses teaser, and `courses.html`, hero ("Wading in from the shore"). Comment on the same line as each figure: index line 174, courses line 114 | Five scuba divers wading waist-deep into a calm, clear bay beside a rocky shore with old stone walls | https://www.pexels.com/photo/men-diving-in-a-bay-11442926/ | Anatolii Maks (Pexels) | Pexels License | 2026-11-18 | Illustrative: replace with your own photo |

- The Pexels License (https://www.pexels.com/license/) says: "All photos and videos on Pexels are free to use" and "Attribution is not required". You may crop and edit them. It does not allow selling unaltered copies of a photo, implying that the people in it endorse a product, showing identifiable people in a bad light, or using a photo as part of a trade mark or business name. None of the three pictures is used in any of those ways here.
- None of the source pages says where its photo was taken, so the site names no place for them, and they are not presented as Sunfish Divers' own courses or customers.
- All three are crops. The wading picture is cut to an upright 4:5 frame around the divers, with contrast and colour lifted slightly; it replaced the swimming-pool training photo from the live site at the owner's request. The camera picture is cut to the diver and the sun (the fin blades at the left, and the maker's marks on them, are outside the frame). The two-divers picture is cut to its upper two thirds, which leaves only the divers, the light and open water.
- To replace one with your own photo, follow "Replacing or adding a photo" below, and delete the `STOCK PHOTO` comment above the figure and the `stock-` file.
- No stock is used, and none should be, for the logo, the PADI badge, staff portraits, the shop, the Zenobia, Liberty and Nemesis III wrecks, the Instagram tiles, the share image or the nine dive-site cards (those carry the owner's own photos).

### (d) The dive-site photos, and photos still to supply

**The nine dive-site cards** (`dive-trips.html`, comment on line 195) now carry the photographs the owner supplied. Each was cropped to the card's 3:2 shape; none was enlarged, so three are smaller than the others because their originals were small. To change one, save the new photo in `assets/img` under exactly the same name and update `alt`, `width` and `height` on the line shown:

| Dive site | File in `assets/img/` | Size (px) | What it shows | Image tag on line |
|---|---|---|---|---|
| Green Bay | `site-green-bay.jpg` | 1080 x 720 | Statues and columns standing on the sandy seabed | 199 |
| Blue Haze | `site-blue-haze.jpg` | 1200 x 800 | Two divers at the surface in clear turquoise water beside the rocky shore | 209 |
| The Caves | `site-the-caves.jpg` | 640 x 427 | Looking out through the mouth of an underwater cave onto sunlit sand | 219 |
| The Canyon | `site-the-canyon.jpg` | 960 x 640 | Divers climbing down the rocks to the clear water | 229 |
| Chapel Bay | `site-chapel-bay.jpg` | 1024 x 683 | A shoal of small silver fish over an algae-covered rock just below the surface | 239 |
| Konnos Point | `site-konnos-point.jpg` | 935 x 623 | Fish over pale boulders and seagrass in blue water | 249 |
| Paramount | `site-paramount.jpg` | 640 x 427 | Sunlight falling through blue water from the surface | 259 |
| Nissia | `site-nissia.jpg` | 894 x 596 | A diver hovering over seagrass and sand | 269 |
| Shallow Reef | `site-shallow-reef.jpg` | 1200 x 800 | Ornate wrasse beside an algae-covered rock just below the surface | 279 |

- Best size for a replacement: landscape, about 1200 x 800 px (3:2), JPEG. A photo of another shape is cropped from the centre to 3:2. The photos of The Caves and Paramount are only 640 px wide: sharper originals would look better on large screens.
- The `alt` text of each says what the photo shows and names the site, as the owner supplied each photo for that site. Where the photos came from and who took them is not recorded here: confirm you may use them before launch.
- File names are case-sensitive on the web: keep them in lower case, exactly as listed.
- If a file is deleted, its card shows a tinted box with the file name instead. No stock photographs are used on these cards.
- On phones the nine cards stand two to a row (photo, name, tag), and the ninth runs across with its photo beside its name. When you add a description to a card (the TODO on each card), write it as a `<p>` inside the card's `<div class="card__body">`: as soon as one card has such a paragraph, phones show one card per row so that the text has room. Nothing else needs changing.

**Other places where a photo of your own would improve the site:**

| Where | What is there now | Photo wanted | Suggested file |
|---|---|---|---|
| `try-diving.html`, "Open to all ages" (comment on line 252) | `bubbles-while-ascending.jpg` as a stand-in. No stock photo is used here, because a Bubblemaker picture would have to show a child | A Bubblemaker session, 800 x 1000 | `try-diving-bubblemaker.jpg` |
| `instructor-courses.html`, Assistant Instructor Course (line 178) | The stock photo `stock-two-divers-in-sun-rays.jpg` | An Assistant Instructor Course in progress, 800 x 1000 | `instructor-courses-assistant-instructor.jpg` |
| `specialties.html`, beside the grid (line 261) | The stock photo `stock-diver-with-underwater-camera.jpg` | One of your divers with an underwater camera, 800 x 1000 | `specialties-underwater-photographer.jpg` |
| `specialties.html`, "On the reef" (line 299) | `jellyfish.jpg` | A diver hovering over the reef at one of the local sites | `specialties-buoyancy-over-reef.jpg` |
| `courses.html`, "Your next step" (line 273) | `diver-on-buoy-line.jpg` (your own photo, but small and dark) | Divers on a descent line or a training dive | `courses-training-dive.jpg` |
| `index.html`, Instagram strip (lines 309 to 325) | Three pictures from the live site's Instagram block | Newer posts, or a live feed, 600 x 600 | Any names |

### (e) Logo and PADI badge

| What | File | Where | Notes |
|---|---|---|---|
| Logo in the header | `logo-sunfish-divers-emblem.jpg` (244 x 200) | Line 56 of every page (the comment; the image is on line 58) | The sunfish and the curved "sunfish divers" lettering cut from the real logo, on a white rounded tile, beside the text wordmark "Sunfish Divers". The whole logo is too tall to read at header height, so only its upper part is used here. Styles: `.logo`, `.logo__tile`, `.logo__mark` in section 09 of the stylesheet |
| Logo in the footer | `logo-sunfish-divers.jpg` (395 x 500) | Footer of every page (comment on index 373, dive-trips 438, try-diving 309, courses 291, specialties 367, instructor-courses 315, dive-centre 304, about 297, contact 347) | The whole logo, "DIVE the Enjoy Difference" included, on a white tile. Styles: `.logo--full` in section 09 |
| PADI badge | `padi-5-star-idc-badge.jpg` (488 x 211) | Footer of every page (comment on index 378, dive-trips 443, try-diving 314, courses 296, specialties 372, instructor-courses 320, dive-centre 309, about 302, contact 352) | The badge file from the footer of the live site. Its own background is near-black, so it sits on the dark footer as a small plaque. Its `alt` text reads "PADI 5 Star Instructor Development Centre". Styles: `.padi-badge` in section 15 |

- The logo comes from a JPEG with a white background (`sunfish-logo-800x800.jpg` on the live site), which is why it sits on a white tile. If you have the logo as a vector file (SVG) or a PNG with a transparent background, it will be sharper: save it over the two logo files, or change the two `src` values on all nine pages.
- Both logo images have an empty `alt`, because the link around them is already named "Sunfish Divers, home".
- The browser tab icon is still the drawn sunfish silhouette, `assets/svg/favicon.svg`.

### (f) The dive map

`dive-trips.html` carries two drawn maps in the panel "Where we dive", between the `DIVE MAP:BEGIN` and `DIVE MAP:END` comments (lines 149 to 188): Cyprus with the Zenobia wreck and a frame round the south-east corner, and a close-up of the coast from Ayia Napa round Cavo Greko to Protaras with a numbered tack for each local dive site and a lettered one for each wreck. The list under the maps names every tack and links to its card further down the page (the cards have the ids `site-green-bay`, `wreck-liberty` and so on). The coastline is drawn from OpenStreetMap data, which is why the credit line under the list must stay. The styles are section 20 of `css/styles.css`.

**The tack positions are approximate and need the owner's check.** The live site names the sites but does not say where they are, so each tack was placed from public sources:

| Tack | Place | Latitude, longitude used | What the position rests on |
|---|---|---|---|
| 1 | Green Bay | 34.9990, 34.0672 | Green Bay beach, Protaras (OpenStreetMap) |
| 2 | Blue Haze | 34.9785, 34.0236 | Ammos tou Kambouri beach, Ayia Napa, where dive listings place the site |
| 3 | The Caves | 34.9680, 34.0546 | the sea caves west of Cape Greco (OpenStreetMap) |
| 4 | The Canyon | 34.9665, 34.0605 | dive listings: under the southern cliffs of Cape Greco, beside the Caves |
| 5 | Chapel Bay | 34.9756, 34.0772 | below the chapel of Agioi Anargyroi (OpenStreetMap) |
| 6 | Konnos Point | 34.9815, 34.0778 | the headland on the south side of Konnos Bay (estimate) |
| 7 | Paramount | 34.9943, 34.0702 | the shore below the Paramount hotel, Protaras (OpenStreetMap) |
| 8 | Nissia | 35.0012, 34.0668 | Nissia bay beside Green Bay; dive listings also call it Green Bay 2 |
| 9 | Shallow Reef | not placed | no published position found |
| L | Liberty wreck | 35.0508, 34.0362 | OpenStreetMap wreck position |
| N | Nemesis III wreck | 35.0498, 34.0365 | OpenStreetMap wreck position |
| Z | Zenobia wreck (on the map of Cyprus) | 34.8972, 33.6576 | OpenStreetMap wreck position off Larnaca |
| flag | Sunfish Divers, Ayia Napa | 34.9854, 34.0002 | the same point as the marker of the map on `contact.html`, which is itself to be confirmed |

- **Shallow Reef has no tack**: no published position was found for it. The list shows it as "not yet on the map".
- The tacks of the shore sites were moved to the nearest point of the coastline; Konnos Point moved furthest (about 450 m, to the headland on the north side of Konnos Bay), so check that one first.
- The page says "Tack positions are approximate" under the list. Take that sentence out once every position is confirmed.

To move a tack, or to add the one for Shallow Reef, the simplest way is to pass the corrected latitude and longitude of each site to whoever maintains the site. By hand: each tack is one `<a href="#site-...">` element on the long line of the close-up drawing; inside it the path `tack__pin` runs from the place on the coast to the numbered head, `tack__tip` is the dot on the coast and `tack__head` holds the circle and the number. A position on the close-up is x = (longitude - 33.985) x 5217.4 and y = (35.068 - latitude) x 6369.3, in the drawing's own units (it is 600 wide and 764 high; one kilometre is about 57.3 units). Keep the head about 70 units away from the tip, out over open water and clear of its neighbours.

### Replacing or adding a photo

- Same shape, same subject: save the new file over the old one under the same name. Nothing else changes.
- A different picture: give the file a name that says what it shows, then change `src` and `data-file` (the same path twice), `alt`, the caption (`<figcaption>`), and `width` and `height` (the real pixel size of the file) in the HTML.
- Frames crop from the centre. To keep another part of the picture in view, add `--photo-pos` to the figure, for example `style="--photo-pos: 16% 50%"` (left to right, then top to bottom). The frames have different shapes on phones and on wide screens, so look at both.
- Two frames are wider on phones than elsewhere: the photos beside the home page's four teasers (4:3 on phones, upright from 768 px) and the first photo of the gallery on `try-diving.html` (3:2 across the screen on phones, with the other two side by side below it; upright from 576 px). A tall picture loses its top and bottom there, so check the subject.
- `photo--pano` is the frame for a wide panorama (2:1 on phones, 3:1 from 768 px). `photo--cap-low` moves the caption of a home-page teaser photo to the foot of the picture on phones, for photos whose subject is at the top.
- If a file is missing, the page shows a tinted box labelled with the file name instead of a broken image (`.photo` in section 08 of the stylesheet, `initPhotos()` in the script).
- Loading: the photo in the opening panel of each page carries `loading="eager" fetchpriority="high"`, because it is the first picture a visitor sees; so does the header logo (`fetchpriority="high"`). Every other image carries `loading="lazy" decoding="async"`. Keep that pattern when you add a photo: only the first one on a page should be eager.
- Sizes that work well: 800 x 1000 for the tall frames, 1200 x 800 for the dive-site cards, 900 x 600 or 1000 x 750 for the other cards, JPEG at about 75% quality, under 180 KB each.

## 7. To do before going live

### Things a static demo cannot do

| Item | Where | What is needed |
|---|---|---|
| Enquiry form | `contact.html` line 139 (`FORM HANDLER` comment, form on line 140) and `js/ocean.js` line 1657 (`FORM HANDLER` comment in `initForms()`) | The form validates and then shows a success box, but sends nothing. Give the form a real handler (`action` and `method`, or a `fetch` call at the marked place in the script), show the success box only when sending worked, and add server-side validation and spam protection. The "Send enquiry" button (line 184) carries a `disabled` attribute that the script removes, so that the demo form cannot submit itself when the script is missing; take the attribute out once the form has a real `action`. Then reword the two demo notices: the note under the button (`contact.html` line 185) and the success message (lines 189 to 190) |
| WhatsApp number | 20 links to `https://wa.me/35799879396`, each with a TODO comment on the line above (listed per file below): the footer and the phone action bar of every page, the "Find us in Ayia Napa" panel on the home page and the "talk to us" list on the contact page | Confirm that +357 99 879 396 is correct. If it changes, change the link in all 20 places and the visible number in the 11 places that print it (the action bar shows the word "WhatsApp", not the number) |
| Map marker | `contact.html` line 295 (iframe on line 299) | Confirm the marker position, currently 34.985407 N, 34.000226 E, the OpenStreetMap entry for Sunfish Divers. The "Open in Google Maps" link on line 301 searches by name and address instead |
| Search engines | Line 10 of every page (`<meta name="robots" content="noindex, nofollow">`, with its TODO comment on line 9) | The tag keeps the temporary test site out of search results. It must come out when the site goes live, or the real site will not be found either: delete lines 9 and 10 from all nine pages (section 10, "At launch") |
| Page URLs for sharing | Line 18 of every page (`og:url`) | Currently `https://sunfish-divers.com/` for the home page and `https://sunfish-divers.com/PAGE.html` for the others. Change them if the live addresses differ. These are the only addresses in the site that name a domain; on the test site they simply point at the future address |
| Share image | Line 19 of every page (`og:image`), file `assets/img/og-sunfish-divers.jpg` | The file is a real photo (the front of the dive centre). The tag must hold a full address, and it points at `https://sunfish-divers.com/assets/img/og-sunfish-divers.jpg`, where the file does not exist yet: link previews show no picture until the site is on its final domain, or until line 19 is changed to the address where the site really is. That is true of the test site too: a link to it shared in a chat shows the title and description without a picture |
| Photo rights | Section 6 | Confirm the right to use each photo from the live site, and the PADI course artwork in 6 (b). The two stock photographs in 6 (c) need no permission and no credit |
| Dive map | Section 6 (f) | Confirm the position of every tack on the map of `dive-trips.html` and give the position of Shallow Reef, which has no tack yet |
| Photos still missing | Section 6 (d) | The nine dive-site photos are in place. Supply the others listed there, and replace the three stock photographs in 6 (c) with your own when you have them |
| Instagram strip | `index.html` lines 309 to 325 | Three fixed tiles that link to the Instagram profile. It is not a live feed; either supply newer photos or connect a feed |
| Course, site and service details | The content TODOs below | The pages hold only what was in the brief. No prices, schedules, depths or staff details were invented |

### Every TODO comment, by file

There are 65 `TODO` comments, all in the HTML pages. `css/styles.css`, `js/ocean.js` and the SVG files contain none. Line numbers are those of the files as delivered; they move as soon as a line is added or removed above them, so search a page for `TODO` to find them again.

**`index.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL; `og:url` and `og:image` must be full addresses on the final domain |
| 353 | Confirm the WhatsApp number in the "Find us in Ayia Napa" panel |
| 418 | Confirm the WhatsApp number in the footer |
| 436 | Confirm the WhatsApp number in the phone action bar |

**`dive-trips.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 150 | Dive map: confirm the position of every tack and place Shallow Reef, which has no tack yet (section 6 (f)) |
| 204 | Green Bay: add depth, level and a short description |
| 214 | Blue Haze: add depth, level and a short description |
| 224 | The Caves: add depth, level and a short description |
| 234 | The Canyon: add depth, level and a short description |
| 244 | Chapel Bay: add depth, level and a short description |
| 254 | Konnos Point: add depth, level and a short description |
| 264 | Paramount: add depth, level and a short description |
| 274 | Nissia: add depth, level and a short description |
| 284 | Shallow Reef: add depth, level and a short description |
| 483 | Confirm the WhatsApp number in the footer |
| 501 | Confirm the WhatsApp number in the phone action bar |

**`try-diving.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 247 | Add Bubblemaker details (how it runs, depth, duration) and any minimum age or medical requirements for Discover Scuba Diving |
| 252 | Supply a photo of a Bubblemaker session (`assets/img/try-diving-bubblemaker.jpg`); a photo from the live site stands in for now |
| 354 | Confirm the WhatsApp number in the footer |
| 372 | Confirm the WhatsApp number in the phone action bar |

**`courses.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 160 | PADI Scuba Diver / Open Water Diver: details from the live site |
| 173 | PADI Adventure Diver / Advanced Open Water Diver: details from the live site |
| 186 | Emergency First Response / PADI Rescue Diver: details from the live site |
| 199 | PADI Master Scuba Diver / Divemaster: details from the live site |
| 212 | PADI Assistant Instructor / Instructor Development Course: details from the live site |
| 267 | Supply course details and schedules from the live site |
| 336 | Confirm the WhatsApp number in the footer |
| 354 | Confirm the WhatsApp number in the phone action bar |

**`specialties.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 171 | Supply the details of each of the 14 specialties: what it covers, prerequisites, duration, prices and packages. The one-line descriptions and the five filter groups are neutral placeholders written for this site and need checking |
| 289 | Confirm which specialties to suggest for the local shore dives |
| 412 | Confirm the WhatsApp number in the footer |
| 430 | Confirm the WhatsApp number in the phone action bar |

**`instructor-courses.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 170 | PADI Assistant Instructor Course: course content, duration and prerequisites from the live site |
| 206 | Content, duration and prerequisites of each of the four IDC parts, from the live site |
| 234 | Add the dates of the next Instructor Development Courses |
| 360 | Confirm the WhatsApp number in the footer |
| 378 | Confirm the WhatsApp number in the phone action bar |

**`dive-centre.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 195 | Add what is available to hire and to buy, and how tax-free sales work (for example which documents to bring) |
| 230 | Add which equipment is serviced, cylinder inspection details and usual turnaround times |
| 349 | Confirm the WhatsApp number in the footer |
| 367 | Confirm the WhatsApp number in the phone action bar |

**`about.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 275 | Supply the dive package details. The section currently says that packages are put together on request and that details will follow |
| 342 | Confirm the WhatsApp number in the footer |
| 360 | Confirm the WhatsApp number in the phone action bar |

**`contact.html`**

| Line | What is needed |
|---|---|
| 9 | Take out the `noindex` tag on the next line when the site goes live (section 10) |
| 17 | Confirm the final page URL and the share image address |
| 214 | Confirm the WhatsApp number in the "talk to us" list |
| 295 | Confirm the map marker position (currently 34.985407 N, 34.000226 E) |
| 392 | Confirm the WhatsApp number in the footer |
| 410 | Confirm the WhatsApp number in the phone action bar |

Markers that do not use the word TODO but also need action: `FORM HANDLER` (`contact.html` line 139, `js/ocean.js` line 1657), the `PADI course artwork` comment (`instructor-courses.html` line 114, see section 6 (b)), and the four `STOCK PHOTO` comments (`specialties.html` line 260, `instructor-courses.html` line 177, `index.html` line 174, `courses.html` line 114, see section 6 (c)).

## 8. Browser support and accessibility

Browser support:

- Written for current versions of Chrome, Edge, Firefox and Safari, on desktop and mobile, with layouts designed for phones first and checked from 320 px wide upwards. Internet Explorer is not supported.
- Frosted glass uses `backdrop-filter` inside `@supports`. Browsers without it get a nearly opaque panel and header of the same colour, so text stays readable.
- Other newer features are guarded in the same way: the registered `--depth` property (`@property`), IntersectionObserver, ResizeObserver and the Web Animations API (bubbles). Without them the site loses the effect, not the content.
- Three more are used on phones only, each with a fallback: scroll timelines (the water strip follows the scroll position without any script work; without them the script moves it), `overflow: clip` (needed for the wreck tour; without it the wreck stands still) and the safe-area insets `env(safe-area-inset-*)` (0 where a browser does not know them).
- Without JavaScript (or if `js/ocean.js` fails to load) every page stays readable, with the plain header and all content shown. The specialties filter chips are hidden, and the enquiry form's button stays disabled, with the note beside it saying how to get in touch.
- There is a print stylesheet that drops the water, header and scenes.
- No browser test results are stored in this folder. Check the browsers and devices that matter to you before launch.

Accessibility, as built:

- A "Skip to content" link is the first focusable element on every page and jumps to `<main id="main">`.
- Semantic landmarks (header, main navigation, main, footer navigation, footer) and exactly one `h1` per page.
- The menu is a real button with `aria-expanded`. Below 1248 px it opens full screen: focus stays inside it, Escape closes it and returns focus to the button, and the rest of the page is made inert while it is open.
- Visible focus outlines on every interactive element (`:focus-visible`, 3 px), dark on light panels and sand-coloured on dark ones.
- The depth gauge is keyboard-usable: each zone is a button with a full label such as "Shallow reef 5 m to 12 m", and the current zone is marked.
- All decoration is hidden from assistive technology: the water, sea life, bubbles, wreck and vignettes are `aria-hidden`.
- Every photo has `alt` text that describes what is in the picture and has `width` and `height` set to the real size of its file, so the page does not jump as images arrive. All are lazy-loaded except the opening photo of each page. The label behind each photo (its file name, seen only if the file is missing) is drawn but not read out by screen readers.
- The logo images have an empty `alt`, because the link around them carries the name "Sunfish Divers, home". The header logo is not lazy-loaded either, as it is on screen from the start. The PADI badge is an image with the `alt` text "PADI 5 Star Instructor Development Centre".
- Text always sits on a panel whose colours switch with depth; the design target was WCAG AA contrast at every depth.
- The large headings that sit directly on the water are the exception. They are held to 3:1 (the AA figure for large text) against the plain water. One screen shows about 14 m of the colour scale from top to bottom, so on some screen sizes one or two headings near 12 m come down to between 2.7:1 and 3:1 for the moment they are at the very top or the very bottom of the screen; a soft halo around the letters makes up for it there.
- The specialties filter uses `aria-pressed` buttons and announces the result ("Showing 5 of 14 specialties").
- The enquiry form has visible labels, error messages linked to their fields, moves focus to the first field with a problem, and announces the success message.
- `prefers-reduced-motion` is respected (section 4).
- Touch: on phones every button and link that stands on its own has a tap area of at least 44 by 44 px (text links, the footer links and the depth pill get theirs from an invisible enlarged area, so they look the same). Links inside a sentence keep the size of the text. On touch screens the map on the contact page does not take over scrolling (section 9); the tap area of "Open in Google Maps" is the whole map panel. Nothing needs a hover: buttons give their bubbles on a tap, and the depth gauge shows its zone names on a tap.
- The enquiry form uses 16 px text in its fields (so iPhones do not zoom in), the email keyboard for the email field, and `autocomplete` and `enterkeyhint` on every field. The "next" key of the on-screen keyboard moves on to the next field; it does not send the form.

## 9. Phones

The site is one build. Everything below is the same HTML, switched by the width (and sometimes the height) of the screen. Checked at 360 x 740 (the main target), 390 x 844, 412 x 915, 320 x 568, and sideways at 740 x 360.

### The action bar (Call, WhatsApp, Book a dive)

On screens under 768 px wide a small bar is fixed to the foot of the screen with three actions: **Call** (dials +357 23 721 300), **WhatsApp** (opens a chat with +357 99 879 396; that number still has to be confirmed, see section 7) and **Book a dive** (goes to the enquiry form on the contact page: `contact.html#enquiry`).

- Where it is: the block between `<!-- ===== MOBILE ACTION BAR ... -->` and `<!-- ===== /MOBILE ACTION BAR ===== -->`, just above the script tag at the foot of every page (line 433 in `index.html`). The block is identical on all nine pages. Its styles are section 19 of `css/styles.css`; its behaviour is `initActionBar()` in `js/ocean.js`.
- When it shows: it slides in once the buttons of the page's opening panel have scrolled away (those are the main actions of the first screen), and stays while you read.
- When it steps aside: while the menu is open; while you type in a form field (the on-screen keyboard would push it over the field); over the wreck and the seabed drawings; and wherever the page itself offers the same actions, namely the footer, the "On the seabed" panels of the home page, the "talk to us" list of the contact page and the closing call-to-action card of each of the eight inner pages ("Plan your dive trip", "Ready to take the plunge?" and so on, which carry their own button). All but the footer are marked in the HTML with the attribute `data-bar-hide` (ten places); add that attribute to any other block that should send the bar away.
- It never covers the end of the page: it is put away as soon as the footer comes up. Without JavaScript, where it cannot step aside, the footer keeps room for it at its foot instead (`--bar-space`, plus the safe-area inset of phones with a home indicator).
- Without JavaScript it is simply always there. With "reduce motion" switched on it appears and disappears without sliding.
- It is not shown on a phone held sideways (a screen under 480 px tall), where the header shows its "Book a dive" button instead, nor from 768 px up.
- **To remove it:** delete the marked block from all nine pages, and delete section 19 from `css/styles.css`. Nothing else needs to change: the header's "Book a dive" button comes back by itself on screens from 480 px wide (as it was before the bar; narrower phones then reach it through the menu), the footer loses the extra room, and the script does nothing when the bar is not there. (Leave the `data-bar-hide` attributes or take them out; they do nothing without the bar.)
- To change an action, edit the three links in the block, on every page. Each link is an icon and a visible label.

### What else is different on a phone

| What | Under | How it differs | Where |
|---|---|---|---|
| Header | 768 px | "Book a dive" moves from the header into the action bar | stylesheet section 19 |
| Menu | 1248 px | Full screen as before. On phones the list scrolls below the header bar instead of under it; on a phone held sideways the nine links stand in two columns so that everything fits a 360 px tall screen | section 09 |
| Opening panel | 768 px | Less empty water above the heading. On short phones (under 672 px tall) the buttons come straight after the first paragraph, so the heading and the main button are on the first screen; the order in the HTML is unchanged | sections 10 and 13 |
| Depth gauge | 768 px | A short pill with the depth; the zone name drops out under it, written downwards in the same narrow column, when the zone changes | section 18.4 |
| Glass panels | 700 px | Not blurred, and a little denser instead (`--surface`). Blurring a panel that fills the screen on every scroll frame is the most expensive thing for a phone's graphics chip, and the difference only shows when an animal passes behind | section 07 |
| Sea life | 700 px | Half the cast, smaller, no parallax | `buildLife()` |
| The sunfish | 700 px wide, or 480 px tall | Panels are as wide as the screen, so the sunfish used to cross half hidden. The script now opens the widest gap in the 20 to 30 m zone to the height of the sunfish (about 350 px of open water, which makes an inner page about 160 px longer). The moray, the octopus and the seagrass keep out of that gap. On a phone held sideways the same is done, and the sunfish is drawn no taller than three quarters of the screen | `clearingApply()`, `swimWidth()` |
| Home wreck | 700 px | A tour: the wreck is drawn at four fifths of the screen height (two to three screens wide), rises into view, rests on the foot of the screen and glides from bow to stern while you scroll on, past the diver and the torch. This adds about 560 px of scrolling to the home page | section 15, `tourUpdate()` |
| Seabed vignettes | 700 px | Scaled and centred on their subject (see section 5) | section 15 |
| Home, "On the seabed" | 700 px | Tighter panels, opening hours on one line each, ripple marks and soft dunes on the sand; the footer of the home page does not repeat the opening hours and the contact lines that stand just above it | section 12 |
| Footer | 640 px | Logo and tagline share a row. Under 768 px the links are 44 px tall | section 15 |
| Text | 768 px | Card descriptions at 16 px; notes, hints and captions at 14 px, as are the tags on the dive-site and specialty cards; capital-letter labels, eyebrows, depth chips, the other tags and the small units beside large figures ("hrs", "km") keep their own sizes, from 11 px to just under 14 px (the "m" in the depth pill is smaller still, about 10 px); on phones narrower than 360 px the two largest heading sizes step down | sections 01 and 13 |
| Home, teaser photos | 768 px | Nearly the full width at 4:3 (they were three quarters of the width at 5:4, with the caption and the panel covering much of the picture) | section 11 |
| Home, trust strip | 640 px | The three years side by side on one line, then "Full-time PADI Course Director" and "Multilingual instructors" as rows with their icons | section 11 |
| Opening hours (home, dive centre, contact) | 700 px | One line per season with a hairline between; on phones narrower than 360 px the hours stand under the season, in the footer too | section 12 |
| Dive-site cards | 608 px | Two to a row; see section 6 (d) for what happens when descriptions are added | section 13 |
| Timelines (Try Diving steps, About history) | 700 px | Each marker ("On land", "1982") sits above its panel, which gets the full width; the dashed depth line runs down the left between the panels | section 13 |
| Course ladder | 700 px | The numeral and the level share the first line of each rung; title, text and button use the full width | section 13 |
| Specialty cards, IDC steps, icon cards | 700 px | Set tighter; the step number and the icon stand beside the title instead of on a line of their own | section 13 |
| Try Diving gallery | 576 px | One photo across, two side by side below it, so that all three fit one screen | section 08 |
| Map | touch screens | A finger on an embedded map moves the map and the page gets stuck, so on touch screens the map is a still picture: a drag scrolls the page, and a tap anywhere on the map opens Google Maps, as the link under it does. The + and - buttons that the embedded map draws could not be used there, so they are cropped out of view. With a mouse the map can be moved and zoomed as before | section 14 |
| Phone held sideways | 480 px tall | Tall photos are kept smaller than the screen, the dive-site cards stand three to a row, the wreck cards have the photo beside the text (as tall as the screen allows, and it stays in view while the text beside it scrolls past), the map is lower, the home page has less open water between its zones, and the sunfish is smaller and has a clearing of its own | sections 04, 10, 11, 13, 14 |
| Notches | all | The pages ask for the full screen (`viewport-fit=cover`) and keep the header, the page gutters, the menu, the depth pill and the action bar inside the safe area | `--safe-*` in section 01 |

### Why scrolling is lighter on a phone

A slow phone has about 16 ms for each frame of a scroll. Measured in Chrome set up as a phone, with the processor slowed six times, a scroll frame of the home page took about 22 ms before this work and takes about 11 ms now. Four things changed, all under 700 px wide only:

- **No parallax for the sea life.** Each animal that moved with the depth had to be restyled on every frame.
- **Moving parts pause while the page moves.** Tails, fins, seagrass blades and the fish in the wreck are parts of drawings, and a browser has to redraw those itself, frame by frame. While the page is being scrolled they hold their pose, and carry on 180 ms after it stops (`calm()`). Swimming and bobbing never stop. The growth on the wreck and on the seabed does not sway at all on phones.
- **The water and the light are written as plain values**, not through the `--depth` custom property (`LIGHT` in `js/ocean.js`; the curves are the same as in section 18.2 of the stylesheet and have to be kept in step with it). Where the browser supports scroll timelines, the water strip is tied to the scroll position by the browser itself (`waterSync()`).
- **No blur behind the panels** (see the table above).

Nothing in this list changes the site at 768 px and wider.

## 10. Publishing on GitHub Pages

GitHub Pages is a free service of GitHub that shows the files of a repository as a website. Used as below, it gives this folder a temporary test address of the form `https://USERNAME.github.io/REPOSITORY/`, which you can open on any phone.

### Three things to know first

- **The repository has to be public.** With a free GitHub account, Pages only works for a public repository. Public means that anyone can look at every file in this folder on github.com: the pages, the photos and this README. (Pages for a private repository needs a paid GitHub plan.)
- **`noindex` hides the site from search engines, not from people.** Every page carries the tag `<meta name="robots" content="noindex, nofollow">` (line 10), which asks Google and other search engines not to list the test site. It is not a lock: there is no password, and anyone who has the address can open the site. Do not put anything in this folder that is not meant to be seen.
- **It is a copy of the content of a live business.** Keep the test site only as long as you need it, and take it down afterwards (see "Taking the test site down").

### What is already prepared

| What | Why it matters on GitHub Pages |
|---|---|
| Every address inside the site is relative (`css/styles.css`, `about.html`, `assets/img/...`), with no leading slash | The test site lives in a sub-folder of the address (`/REPOSITORY/`). An address that began with `/` would look for the file at the top of `github.io` and not find it |
| All file and folder names are lower case without spaces, and every address in the pages is spelt exactly like the file it points at | The servers of GitHub tell capitals and small letters apart; Windows does not. A photo saved as `Site-Green-Bay.JPG` shows on your computer and is missing online |
| `.nojekyll` (an empty file) | Without it GitHub runs the folder through a site builder called Jekyll before publishing. With it the files go online exactly as they are. Leave it where it is |
| `noindex` on all nine pages | Keeps the test site out of search results |
| `.gitignore` | Keeps `Thumbs.db`, `.DS_Store` and similar clutter out of the repository |
| The only outside addresses are Google Fonts, the OpenStreetMap map, Instagram, Facebook, WhatsApp and Google Maps, all with `https://` | GitHub Pages serves the site over https, and browsers block plain `http://` content inside an https page |

Checked before delivery: all nine pages were loaded from a local web server set up to behave like GitHub Pages (the site at the address `/sunfish-divers-test/`, file names case-sensitive, everything outside that address "not found"), at phone size (360 x 740) and at desktop size (1440 x 900). No file was missing, there were no script errors and no broken links. The pages were then checked again opened straight from the folder. It has not been pushed to GitHub: that step is yours.

### Steps

You need a GitHub account (github.com, free) and Git on this computer. To see whether Git is installed, type `git --version` in a terminal; if it is not found, install "Git for Windows" from https://git-scm.com/ and open a new terminal. The commands below are the same in PowerShell, in the Command Prompt and in Git Bash.

1. **Open a terminal in this project folder.** In File Explorer, open the folder that holds `index.html`, click in the address bar, type `powershell` and press Enter. (Or in VS Code: File > Open Folder, then Terminal > New Terminal.) The line you type on must end in the name of this folder. This matters: the repository is made from the folder the terminal is in, and it must contain the site and nothing else.

2. **Make the folder a repository.**

   ```
   git init
   git rev-parse --show-toplevel
   ```

   The second command prints the folder Git is now working in. It must be this project folder. If it prints any other folder (your user folder, for example), stop: go back to step 1 and run `git init` again in the right place before you add anything.

3. **Add the files and record them.**

   ```
   git add .
   git status
   git commit -m "Sunfish Divers test site"
   git branch -M main
   ```

   `git status` lists what is about to be published. It should show the 77 files of section 3 and nothing else: the nine pages, `README.md`, `.nojekyll`, `.gitignore`, `css/styles.css`, `js/ocean.js`, 39 files under `assets/img/` and 24 under `assets/svg/`. If the commit stops with "Please tell me who you are", run the two `git config` lines it shows with your own name and email address, then repeat the commit. Warnings that "LF will be replaced by CRLF" are harmless.

4. **Create the repository on GitHub.** Sign in at github.com, click the **+** at the top right and choose **New repository**. Give it a name in lower case without spaces, for example `sunfish-divers-test`: the name becomes part of the address. Choose **Public**. Leave "Add a README file" unticked, and do not choose a .gitignore template or a licence: the repository has to start empty. Click **Create repository**.

5. **Push the files.** GitHub now shows a page of commands. Use the ones under "...or push an existing repository from the command line". With your own names in place of `USERNAME` and `sunfish-divers-test` they read:

   ```
   git remote add origin https://github.com/USERNAME/sunfish-divers-test.git
   git push -u origin main
   ```

   The first time, a window opens and asks you to sign in to GitHub. When the push has finished, reload the repository page on github.com: the files of this folder are listed there, with `index.html` at the top level (not inside another folder).

6. **Switch on Pages.** On the repository page, click **Settings** (the last tab in the row under the repository name), then **Pages** in the left column. Under "Build and deployment", set **Source** to **Deploy from a branch**. Under "Branch", choose **main** and the folder **/ (root)**, and click **Save**.

7. **Find the address.** Wait a minute or two and reload **Settings > Pages**. A box at the top of that page now says "Your site is live at" followed by the address, with a **Visit site** button. The address is always `https://USERNAME.github.io/REPOSITORY/`, so with the example name it is `https://USERNAME.github.io/sunfish-divers-test/`. You can watch the progress under the **Actions** tab of the repository: a run called "pages build and deployment" gets a green tick when the site is online.

8. **Try it on a phone.** Open the address, go through all nine pages from the menu, and send yourself the link. The names of menus and buttons above are those GitHub uses at the time of writing; if one has moved, look for "Pages" in the Settings of the repository.

### Updating the test site later

Change the files in this folder, look at the result on your own computer (section 2), then in a terminal in this folder:

```
git add -A
git commit -m "Say in a few words what changed"
git push
```

The test site shows the change after about a minute. If you still see the old version, the browser is showing its stored copy (GitHub lets browsers keep pages for ten minutes): reload with Ctrl+F5, or open the address in a private window.

Two things to watch when you add or rename files:

- Keep file names in lower case without spaces, and spell them in the HTML exactly as they are on disk. The nine dive-site photos, for example, must be saved under exactly the names in section 6 (d).
- If you rename a file and only its capitals change (`Photo.jpg` to `photo.jpg`), Git on Windows may not notice. Rename it with Git instead: `git mv Photo.jpg photo.jpg`.

### If something is not right

| What you see | Likely cause | What to do |
|---|---|---|
| A GitHub page saying that there is no GitHub Pages site here (404) | Pages is not switched on yet, or the first build has not finished | Check step 6, wait two minutes, look at the Actions tab |
| A 404 on the address although Pages is on | `index.html` is not at the top level of the repository (the repository was made in the wrong folder), or the branch or folder in step 6 is not `main` and `/ (root)` | Look at the file list on github.com. If the site sits inside a sub-folder there, start again from step 1 in the right folder |
| The page shows as plain text without colours or water | An address was changed to begin with `/`, or a folder or file name was changed in capitals | Compare the address in the HTML with the file name, letter by letter |
| One photo is missing online but shows on your computer | The file name and the name in the HTML differ in capitals, or the file was not added before the push | Fix the name, then `git add -A`, commit and push |
| The old version still shows | The stored copy in the browser | Ctrl+F5, or a private window |
| `git push` is refused | You are not signed in to GitHub in this terminal, or the repository on GitHub was not empty when you created it | Sign in when the window appears. If the repository was created with a README, delete it on GitHub, create it again empty and repeat step 5 |

### Taking the test site down

On github.com, open the repository, then **Settings > Pages**. Either choose **Unpublish site** from the menu (three dots) in the box that shows the address, or set the branch under "Build and deployment" to **None** and save. The address then stops working. To remove the files from GitHub as well, delete the repository: **Settings > General**, at the foot of the page, **Delete this repository**. The folder on your computer is not touched by either.

### At launch

When the site is to replace the live one, go through this list. The first four rows are the ones the test copy brought with it.

| What | Where | What to do |
|---|---|---|
| Let search engines in | Lines 9 and 10 of all nine pages | Delete the `noindex` tag and the TODO comment above it. As long as the tag is there, the real site will not appear in search results. (Deleting these two lines moves every page line number given in this README up by two.) |
| Page addresses for sharing | `og:url`, line 18 of every page (line 16 once the `noindex` lines are gone) | Must be the full, final address of each page. They are already written for `https://sunfish-divers.com/` with the present file names; if the site goes online there unchanged, they are right as they stand. Then delete the TODO comment on the line above |
| Share image | `og:image`, the line after `og:url` | Must be a full address too: `https://sunfish-divers.com/assets/img/og-sunfish-divers.jpg` works as soon as the folder is on that domain. A relative address does not work in this tag |
| Phone action bar | The `MOBILE ACTION BAR` block at the foot of every page; section 9 | Decide whether to keep the Call, WhatsApp and Book a dive bar. To keep it, confirm the WhatsApp number (section 7). To remove it, follow "To remove it" in section 9 |
| Remaining placeholders | Section 6 (d), section 6 (c) | Replace the three stock photographs and the Bubblemaker stand-in with your own pictures if you have them; confirm the rights to the dive-site photos |
| Content still open | Section 7, "Every TODO comment, by file" | Course, dive-site and service details, IDC dates, dive packages, the map marker |
| Enquiry form | Section 7, first row of the table | Connect a real form handler. Until then the form sends nothing |
| Photo rights | Section 6 | Confirm the right to use the photos taken from the live site and the PADI course artwork |
| Where the site lives | The whole folder | Copy it to the web space of the final domain. It works at the top of a domain exactly as it does in a sub-folder; nothing in the files has to change. `README.md`, `.nojekyll` and `.gitignore` are not part of the website and need not be uploaded |
| The test copy | "Taking the test site down", above | Take the GitHub test site down once the real site is online, so that two copies are not on the web. If you keep it for further tests, keep the `noindex` tag in that copy |

One more point about this README: on GitHub Pages it is published with everything else (at `.../README.md`). No page links to it, but it is not secret. If you would rather not show these notes, keep the file out of the repository: add a line `README.md` to `.gitignore` before step 3.
