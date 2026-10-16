# Changelog

## parley-brand 1.0.0 (2026-10-16)

First version.

### Added

- The Parley app icon: a gold tower with lightning bolts on black, as PNGs from 16 to 512 px.
  64 px and below are a plain silhouette; 128 px and up add the lattice.
- Margot the magpie, alone and perched on the tower with the wordmark.
- One Margot card per protocol (dns, pop3, imap, smtp, ssh, ftp, sftp), each asking
  "Parlez-vous ... ?".
- SVG originals of every image.
- `ParleyBrand`: loads the images as `java.awt` images (`appIcons()`, `icon(int)`, `hero()`,
  `margot()`, `margot(String)`), returns resource URLs (`resource(String)`), lists the files
  (`fileNames()`), and exposes the palette as `Color` constants.
- The app icon with a corner badge, `files` (a folder) or `terminal` (`>_`), so several applications
  built with Parley can be told apart: `appIcons(badge)`, `icon(size, badge)` and `BADGES`.
- GraalVM native-image metadata in the jar, listing the PNGs, so native builds include them.
