# MultiFormatSave

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/itworksig/multiFormatSave?label=latest)](https://github.com/itworksig/multiFormatSave/releases/latest)
[![LibreOffice](https://img.shields.io/badge/LibreOffice-6.0%2B-brightgreen)](https://www.libreoffice.org/)

A LibreOffice extension that saves your document to **multiple formats simultaneously** — ODF, MS Office 97, MS Office XML, PDF, RTF and EPUB — with a single click.


## Features

- **One-click multi-format export** — save to several formats at once without reopening dialogs
- **Remembers your choices** — selected formats are persisted between sessions
- **Save-like shortcut** — if the document hasn't changed location, re-runs the last save silently (no dialog)
- **Works across all four apps** — Writer, Calc, Impress and Draw each get relevant format options
- **Toolbar & menu integration** — accessible from the standard toolbar and the File menu

---

## Supported Formats

| App         | Format                     | Extension |
| ----------- | -------------------------- | --------- |
| **Writer**  | ODF Text                   | `.odt`    |
|             | MS Word 97–2003            | `.doc`    |
|             | MS Word 2007–365 XML       | `.docx`   |
|             | PDF                        | `.pdf`    |
|             | Rich Text Format           | `.rtf`    |
|             | EPUB (LO 6.0+)             | `.epub`   |
| **Calc**    | ODF Spreadsheet            | `.ods`    |
|             | MS Excel 97–2003           | `.xls`    |
|             | MS Excel 2007–365 XML      | `.xlsx`   |
|             | PDF                        | `.pdf`    |
| **Impress** | ODF Presentation           | `.odp`    |
|             | MS PowerPoint 97–2003      | `.ppt`    |
|             | MS PowerPoint 2007–365 XML | `.pptx`   |
|             | PDF                        | `.pdf`    |
| **Draw**    | ODF Drawing                | `.odg`    |
|             | PNG image                  | `.png`    |
|             | SVG vector                 | `.svg`    |
|             | PDF                        | `.pdf`    |

---

## Installation

### Option A — Extension Manager (recommended)

1. Download the latest `.oxt` file from [Releases](https://github.com/itworksig/multiFormatSave/releases/latest)
2. In LibreOffice: **Tools → Extension Manager → Add**
3. Select the downloaded `.oxt` and restart LibreOffice

### Option B — LibreOffice Extensions website

[extensions.libreoffice.org/extensions/multisave-1](https://extensions.libreoffice.org/extensions/multisave-1)

---

## How to Use

After installation two new entries appear in the **File** menu and a button is added to the standard toolbar:

- **Multi Save** — Saves in all selected formats silently if the document already has a location. Opens the dialog for new or moved documents.
- **Multi Save As…** — Always opens the format-selection dialog.

In the dialog:

1. Set or confirm the save **path and filename** (without extension — the extension is added per format)
2. Tick the **formats** you want
3. Click **Save**

---

## Building from Source

Requires `make` and `zip`.

```bash
# Build the .oxt package
make

# Clean build artefacts
make clean
```

To release a new version, bump `version` in `Makefile` and push to `master`. The GitHub Action handles the rest.

---

## Changelog

### v1.6.0

- **Added** EPUB export for Writer (LibreOffice 6.0+)
- **Added** minimum LibreOffice 6.0 version requirement in extension metadata
- **Added** flat ODF extensions (`.fodt`, `.fods`, `.fodp`, `.fodg`) to extension-stripping list
- **Fixed** critical module name conflict (`saveDocuments` vs `settings`) that caused save functions to be silently overwritten
- **Fixed** syntax error in `exportArguments` — missing closing parenthesis caused parse failure
- **Fixed** missing `.` separator in file path construction (files were named e.g. `documentpdf` instead of `document.pdf`)
- **Fixed** crash on startup — `FormWizard` library was removed in LibreOffice 6.x but was still being loaded
- **Fixed** all save operations now pass an explicit `FilterName` to `storeAsURL`, preventing failures when "Always save in ODF format" is enabled
- **Fixed** `removeExtension` — `.odm` was missing its leading dot; duplicate `.odg` entry removed


## License

- Original work © 2004–2012 StarXpert, Florent Manens — LGPL v2.1+
- Subsequent work © 2012–present Rob Snelders — GPL v3+

See [LICENSE](LICENSE) for details.
