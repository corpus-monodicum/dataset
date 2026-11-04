# Corpus Monodicum Dataset

Corpus Monodicum is a digital edition of medieval monophonic chant. The edition covers chants such as tropes, sequences, liturgical plays and chants of the Ordinary of the Mass (Kyrie, Gloria, Credo, Sanctus, Agnus Dei), and is funded by the Akademie der Wissenschaften und der Literatur Mainz.

This dataset is a complete, self-contained copy of the published edition data. It contains:

- **6881 chants**, each transcribed syllable by syllable and neume by neume from its manuscript, with the text, comments and variant readings, plus the metadata of the chant (genre, feast, folio, editors).
- **116 sources**: the manuscripts that transmit the chants, with library, shelfmark, dating, place of origin, links to digital images (IIIF) and a written description.
- **Notation documentations** of selected manuscripts: how the neume signs of a manuscript correspond to the transcription (`notation/` folder of a source): a Markdown text, the table of the neume patterns as an SVG image (`patterns/patterns.svg`), and the HTML page of corpus-monodicum.de. Photos of the manuscripts are not part of the dataset because the image rights are unclear: the HTML page shows the manuscript lines from the IIIF servers of the libraries where it could determine the page, and a notice where it could not.
- **Transcription equivalents** of those manuscripts, as data (`<source>.annotations.json`): the table that assigns a reference number to each neume pattern, and the marked line regions on the manuscript pages with the neume signs found in them, linked to the chants. The data are not images; they refer to the images of the libraries by IIIF.
- **Contributors**: everybody who worked on the data, with roles and the sources they are credited for.

The edition is made with Monodi, the project's editing software. Everything that Monodi stores is kept here unchanged in JSON files (*lossless*). The same data also exist in two standard formats for tools that do not know Monodi:

- **TEI** (Text Encoding Initiative, the standard for describing texts and manuscripts): one file per source, describing the manuscript (`msDescription`).
- **MEI header file of a source** (`<source>.source.mei`): the description of the manuscript in the header of a MEI file (the manuscript is a `manifestation`; the `music` element the schema requires stays empty).
- **MEI** (Music Encoding Initiative, the standard for encoding music notation, here with its neumes module): one file per chant, containing the metadata header and the transcribed music.

In this text, a *source* is a manuscript, identified by its *siglum* (short name, for example `Ex 1`), and a *document* (or *chant*) is one chant as transcribed from a source.

## Where to start

- `docs/STRUCTURE.md` explains every file and folder.
- `sources/index.csv` lists all sources with their main metadata; open it in a spreadsheet program to browse.
- `sources/<source>/<source>.tei` describes one manuscript (TEI).
- `sources/<source>/documents/<document>/` holds one chant: `<document>.mei` (MEI, if present), and the complete Monodi data in `<document>.meta.json` (metadata) and `<document>.notes.json` (music text, comments, readings).
- `docs/CONTRIBUTORS.md` names everybody who contributed, with roles and the sources they are credited for.
- `docs/mapping/` holds the specification that decided which field goes where, with the lists of persons, roles and credits.
- `dataset.json` records version, time, tool versions, counts and anything that could not be generated.

`<source>` is the siglum with spaces replaced by `_` (`Ex 1` becomes `Ex_1`); accents and umlauts are kept (`Mü_5539`). File names repeat the siglum of the source and the ID of the document, so a file stays identifiable outside its folder. `.tei` and `.mei` files are XML.
