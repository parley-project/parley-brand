# parley-brand

<img src="https://raw.githubusercontent.com/tony-bringardner/parley-brand/master/src/main/resources/us/bringardner/parley/brand/parley-hero.png" alt="Margot the magpie perched on the Parley tower" width="240" align="right">

The Parley logo, app icons and mascot, kept in one place. Any Parley project that shows
them depends on this artifact instead of carrying its own copies, so a change here
reaches every project with a version bump.

- Java 11 or later
- No runtime dependencies
- Apache License 2.0

## The mascot

**Margot** is a magpie. The French say *bavarde comme une pie*, "chatty as a magpie", and
*parley* comes from the French *parler*, "to speak". She perches on the **tower**, a nod to
the Eiffel Tower's early years as a wireless telegraph station, sending radio waves and
lightning bolts down the wire. On each protocol's card she asks *Parlez-vous DNS ?*,
*Parlez-vous SMTP ?* and so on.

## Using it

```xml
<dependency>
  <groupId>us.bringardner.parley</groupId>
  <artifactId>parley-brand</artifactId>
  <version>1.0.0</version>
</dependency>
```

```java
frame.setIconImages(ParleyBrand.appIcons());   // every size; the OS picks the one it needs
Image about = ParleyBrand.hero();              // About box or splash screen
Image icon  = ParleyBrand.icon(48);            // smallest stored size >= 48 px
Image dns   = ParleyBrand.margot("dns");       // "Parlez-vous DNS ?"
frame.setIconImages(ParleyBrand.appIcons("files"));   // with a corner badge (see below)
URL   svg   = ParleyBrand.resource("parley-icon.svg");
panel.setBackground(ParleyBrand.INK);          // the palette, as java.awt.Color
```

Each call returns a new image, so you can draw on or scale it freely.

### In a README

GitHub can't read images out of a jar, so link to the file in this repository:

```markdown
![Parlez-vous DNS ?](https://raw.githubusercontent.com/tony-bringardner/parley-brand/master/src/main/resources/us/bringardner/parley/brand/margot-dns.png)
```

## What's included

All files are in `src/main/resources/us/bringardner/parley/brand/`.

| File | What it is |
|---|---|
| `parley-icon-16.png` … `parley-icon-64.png` | App icon, plain tower silhouette so it reads at small sizes |
| `parley-icon-128.png` … `parley-icon-512.png` | App icon with the tower's lattice |
| `parley-icon.svg`, `parley-icon-large.svg` | The two icon designs as SVG |
| `parley-icon-files-<size>.png`, `parley-icon-terminal-<size>.png` | The app icon with a corner badge, same sizes and SVGs |
| `parley-tower.svg` | The tower alone, transparent background |
| `parley-hero.png` / `.svg` | Margot on the tower with the wordmark, on black |
| `margot.png` / `.svg` | Margot alone, transparent background |
| `margot-<protocol>.png` / `.svg` | One card per protocol: dns, pop3, imap, smtp, ssh, ftp, sftp |

The wordmark and card text in the SVGs use the viewer's monospace font; the PNGs look
the same everywhere.

## Badges for applications

Applications built with Parley can wear the brand too. So that several of them can be told apart in
the Dock or taskbar, the icon comes with a corner badge: `ParleyBrand.appIcons("files")` adds a
folder (for file browsers such as parley-files-viewer) and `appIcons("terminal")` adds `>_` (for
shells and IDEs such as fsh-ide). `ParleyBrand.BADGES` lists them.

## Palette

| Name | Hex | Used for |
|---|---|---|
| `INK` | `#080808` | Backgrounds |
| `GOLD_BRIGHT` | `#D0AA42` | Bolts, platforms, wordmark, card backgrounds |
| `GOLD` | `#BA983D` | Margot's outline |
| `GOLD_MID` | `#AB8C3C` | The tower |
| `GOLD_DARK` | `#876D29` | Radio waves, Margot's tail |
| `BRONZE` | `#372C0F` | Lattice, cables, text on gold |

## Building

```
mvn verify
```

Runs the tests headless and fails if line or branch coverage drops below 90%.
