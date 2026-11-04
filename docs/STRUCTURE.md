# Structure of this dataset

This file explains every file and folder of the dataset. It is generated from the `dataset:` block of `docs/mapping/metadata-mapping.yml`, a copy of which is part of this dataset.

`{source_id}` is the siglum of a source (the short name of a manuscript, for example `Ex 1`) with spaces replaced by `_` (`Ex_1`); letters with accents and umlauts are kept (`Mü 5539` becomes `Mü_5539`). `{document_id}` is the ID of a chant in the same form. Names with a trailing `-2`, `-3` mark IDs that were otherwise identical.

The table lists every file and folder that this dataset can contain. A file marked `no` under Required is written only if its data exist (for example a source without a notation documentation has no `notation/` folder).

| Path | Required | Lossless | Purpose |
|---|---|---|---|
| `README.md` | yes | no | Entry point: content, structure, how to cite, licence, version |
| `docs/STRUCTURE.md` | yes | no | Explanation of every file and folder of this structure |
| `docs/CONTRIBUTORS.md` | yes | no | Everybody who contributed, with roles, periods and the sources they are credited for |
| `LICENSE.txt` | yes | no | Licence text or reference; without a confirmed licence the dataset is not for publication (rules.licence_gate) |
| `CITATION.cff` | no | no | Citation hint in machine-readable form (Citation File Format) |
| `dataset.json` | yes | no | Version, creation time, tool versions, counts (sources, documents), status, anything not generated |
| `ro-crate-metadata.json` | no | no | RO-Crate (schema.org JSON-LD): describes every file of the dataset in machine-readable form |
| `checksums.sha256` | yes | no | SHA-256 checksum of every file, for integrity checks |
| `docs/mapping/metadata-mapping.yml` | yes | no | Copy of the specification used, so the dataset stays understandable without access to the repository |
| `docs/mapping/people.csv` | yes | no | Contributing persons, periods and roles (without e-mail addresses) |
| `docs/mapping/roles.csv` | yes | no | Roles and how they are used in the headers |
| `docs/mapping/credits.csv` | yes | no | Who is credited for which source and category of chants, with the status of each row |
| `sources/index.csv` | yes | no | One row per source with the most important metadata, for quick filtering |
| `sources/{source_id}/` | yes | no | Folder of one source; name = siglum as slug |
| `sources/{source_id}/{source_id}.meta.json` | yes | yes | All metadata of the source in the Monodi format; the long texts are in the description and notation files |
| `sources/{source_id}/{source_id}.tei` | no | no | Manuscript description as TEI msDescription, with the people credited for this source |
| `sources/{source_id}/{source_id}.source.mei` | no | no | Manuscript description as a MEI header file (`meiHead` with the manuscript as `manifestation`, empty `music`), written instead of or next to the TEI file when the option `--source-format mei` or `both` is chosen |
| `site/site.css` | no | no | Style sheet of the static pages (written with the option --site) |
| `index.html` | no | no | Entry page of the static pages: the sources in a table and links to the documentation files; open it in a browser |
| `site/by-library.html` | no | no | The table of sources of the start page, ordered by library (one page per order: sorting without a script) |
| `site/by-date.html` | no | no | The table of sources of the start page, ordered by date (the century and the part of it, read from the dating text) |
| `site/by-chants.html` | no | no | The table of sources of the start page, ordered by number of chants |
| `site/fonts/CrimsonText-Regular.ttf` | no | no | Crimson Text, the font of the notation text in the pictures of the static pages (SIL Open Font Licence) |
| `site/fonts/CrimsonText-Italic.ttf` | no | no | Crimson Text italic, see CrimsonText-Regular.ttf |
| `site/fonts/CrimsonText-Bold.ttf` | no | no | Crimson Text bold, see CrimsonText-Regular.ttf |
| `site/fonts/OFL-CrimsonText.txt` | no | no | Licence text of the font Crimson Text (SIL Open Font Licence 1.1) |
| `sources/{source_id}/index.html` | no | no | Page of a source: its metadata as a table, its description, its chants in a table and links to its files |
| `sources/{source_id}/notation/index.html` | no | no | The notation documentation of the source inside the static pages: with navigation and style sheet, the table of neume patterns and the manuscript lines |
| `sources/{source_id}/documents/{document_id}/index.html` | no | no | Page of a chant: its metadata as a table, then its notation as an inline SVG, links to its files and to the neighbouring chants |
| `sources/{source_id}/{source_id}.description.md` | no | yes | Source description as Markdown (the field `beschreibung`) |
| `sources/{source_id}/notation/{source_id}.notation.md` | no | yes | Notation documentation as Markdown (the field `notationsdokumentation`); its images are the files next to it. If the annotations file of the source exists, the links to the picture sheets are removed and a line names that file |
| `sources/{source_id}/notation/{source_id}.images.json` | no | no | Provenance of each image of the notation documentation: file, checksum, what it shows, the source with its library and IIIF manifests, and the rights statement of the library |
| `sources/{source_id}/notation/{source_id}.annotations.json` | no | no | Transcription equivalents of the manuscript as data, in the format of the tool (`cm-manuscript-export`): the table of neume patterns with their reference numbers, the line regions with polygons on the manuscript pages, the neume signs marked in them with their links to chants, and the IIIF manifest. No images |
| `sources/{source_id}/notation/{source_id}.notation.html` | no | no | The notation documentation as the HTML page of corpus-monodicum.de (patterns table and manuscript lines). The photos of the manuscript lines are not delivered (unclear image rights): the page shows them from the IIIF server of the library where the page could be determined, and a notice otherwise |
| `sources/{source_id}/notation/{asset}` | no | no | Images of the notation documentation that are part of the dataset: `patterns/patterns.svg` (table of the neume patterns, SVG, no photo); the Markdown links point to it. Photos of manuscripts are not part of the dataset |
| `sources/{source_id}/{source_id}.iiif.json` | no | no | List of the IIIF manifests of the source |
| `sources/{source_id}/documents/{document_id}/` | yes | no | Folder of one document; name = document ID |
| `sources/{source_id}/documents/{document_id}/{document_id}.mei` | yes | no | The chant as MEI, with a metadata header and the people credited for this chant |
| `sources/{source_id}/documents/{document_id}/{document_id}.meta.json` | yes | yes | All metadata of the document in the Monodi format |
| `sources/{source_id}/documents/{document_id}/{document_id}.notes.json` | yes | yes | Music text, comments and readings in the Monodi format |

Lossless files (`*.meta.json`, `*.notes.json`) hold the data exactly as Monodi stores it. The TEI and MEI files are views of the same data in standard formats.

Check integrity with `sha256sum -c checksums.sha256` (run it inside this folder).
