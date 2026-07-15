# Klein COBOL FAQ

William M. Klein's COBOL FAQ, archived and re-hosted as a static site.

**Deployed site:** https://bushidocodes.github.io/klein-cobol-faq/

## Provenance

The FAQ was originally written by William M. Klein (last revised 2005-08-17 per the document metadata) and lived alongside Michael Coughlan's University of Limerick COBOL tutorial at `http://www.csis.ul.ie/cobol/`. When that site bit-rotted, both were pulled out of the Internet Archive. The tutorial lives at [bushidocodes/limerick-cobol](https://github.com/bushidocodes/limerick-cobol); this repo splits the FAQ out so it can be linked, deployed, and updated independently.

The FAQ HTML is a near-verbatim Microsoft Word "Save as Web Page" export — formatting and structure are preserved as-is.

## Contents

- `index.html` — the FAQ itself (originally `COBOLFAQ.html`)
- `images/` — figures referenced from the FAQ
- `COBOL FAQ (word).doc` — the original Word source

## Development

The site is plain static HTML — no build step. To preview locally:

```sh
npm install
npm run serve   # http://localhost:8000
```

CI runs two checks on every PR (see [.github/workflows/checks.yml](.github/workflows/checks.yml)):

| Script             | What it does                                              |
| ------------------ | --------------------------------------------------------- |
| `npm run validate` | HTML parse / structure check via `html-validate`          |
| `npm run lint`     | Biome check on project JSON/config (FAQ HTML is excluded) |
| `npm run links`    | Internal link check via `linkinator` (externals skipped)  |
| `npm run check`    | Runs validate + links locally                             |

The `html-validate` ruleset is intentionally permissive — the FAQ is a verbatim Word "Save as Web Page" export, so the gate focuses on parse errors and structural bugs rather than flagging every legacy-HTML pattern. Tighten over time if the source gets cleaned up.
