# Voth project: requests for troops in England, 1790s

Archive research by Caitlyn Brinkman-Schwartz for Prof. Hans-Joachim Voth (JV), UBS Center, University of Zurich. This is not a software project. The work is reading scanned Home Office papers and building a dataset from them, plus writing notes, reports and emails to JV.

## What JV wants
- **Priority:** civil **requests for troops** are about 10× more important than decisions to grant them. JV already has troop locations. Requests could become the project's core identification, i.e. the main data the paper's argument rests on.
- **Also in scope:**
  - **barracks** (requests to build them, or arguments about where to put them)
  - **corps founded, armed or expanded** (volunteer corps, militia, armed associations). Key quotes tie them to "suppress any Insurrections".
- **Geography:** England only. Wales and Scotland are out; note them in passing but don't log them.
- **Responses** (HO 43, and notes on the letters themselves) are background, per JV. Bend's thesis shows HO 43 can also be used to *find* requests (see `notes/02_…`).
- **Workflow** ("broad funnel"):
  1. Look at each letter's topic. If in doubt, include it. Record the metadata and the key quote.
  2. Full transcription comes later. JV expects to use a vision-language model (VLM) for it.

## Files
| Path | What it is |
|---|---|
| `HO42_extraction_log.xlsx` | The main dataset (sheets listed below) |
| `notes/01_HO42_first_pass_and_email.md` | JV's brief, the series assessed, the early reading list |
| `notes/02_Bend_2018_HomeOffice_PhD.md` | Bend's thesis: how the Home Office handled letters, selection bias, data tables, new sources |

The spreadsheet's sheets:
- **Events:** only things someone has read in the original document.
- **Leads:** things cited in secondary sources (Gee, Bend, Wells) but not yet checked in the original.
- **Summary:** formulas only.
- **Legend:** definitions and coverage status.
- **Lookups:** dropdown lists and the dates each Home Secretary held office.

## Spreadsheet rules
- **Row IDs** (`HO42-0001`, …) are never reused. **Episode IDs** (`E01`, …) group letters about the same incident; count requests by episode, not by letter.
- **Dates:** `Date (ISO)` is TEXT in the form `YYYY-MM-DD`, because Excel can't hold dates before 1900. `Year`, `Home Secretary in office` and `In scope` are formulas; don't overwrite them.
- **Folios:** TNA's HO 42 PDFs were made from microfilm *before* the volumes were renumbered. Record the folio number stamped on the page in `Folio`, the PDF page number in `PDF page no.`, and set `Folio basis` accordingly.
- **"Civil power inadequate?":** Y means the *writer says* the constables or magistrates couldn't cope. It records the claim, not whether it was true.
- **Addressee:** check how the letter opens. "Your Grace" means Portland (Home Secretary from 11 Jul 1794). "Your Lordship" means someone else, so the letter was probably forwarded.
- **Routes:** requests reach HO 42 in three ways: direct to the Home Secretary; forwarded by a peer, MP or Lord Lieutenant; or made locally (to a garrison or volunteer corps) and only reported afterwards. Record which route.
- **After any edit:** run the xlsx skill's `recalc.py` and confirm 0 errors. Keep Arial and the existing look. Copy the formatting of the last row when adding rows.
- **Flag guesses.** If a role, addressee or event type is inferred rather than read, write "CHECK:" in Notes.

## Reading the HO 42 PDFs
- Caitlyn shares the PDFs through a Dropbox folder. Ask her for the current link. Adding `dl=1` to the link downloads the whole folder as a zip with `curl`.
- Dropbox may rename files on upload, e.g. `HO-42-33_04 (1).pdf`. List the zip's contents before extracting.
- The PDFs are scanned images with no text layer. Work in the scratchpad, not the repository:
  1. Extract the pages with `pdfimages -j`.
  2. Build thumbnail grids to find the pages with writing and skip blank backs of letters.
  3. Read every page with writing on it, one at a time.
- Each image is about one folio and carries its folio number, so use the stamped numbers to locate a range.
- Photographs of the backs of letters matter: clerks recorded the reply date and decision there.
- Never commit the PDFs. They're 50–70 MB each.

## Coverage so far (7 Oct 2026)
- **Read in full:**
  - HO 42/16 (1790)
  - HO 42/30 (May 1794)
  - HO 42/33 (Aug–Dec 1794)
  - HO 42/34 (Jan–Mar 1795)
- **Log:** 20 events and 16 incidents. There are 8 requests for troops: 6 clear, plus 2 borderline (Keynsham 1790; London Nov 1794).
- **Not yet done:** HO 42 for later 1795 to 1801, which should be the richest years (the food crises of 1795–96 and 1800–01).

## Next steps (proposed to JV; awaiting answers)
1. HO 42, 1795–1801.
2. Wells, *Wretched Faces*, pp. 419–40: a table of about 200 food riots and which force was used. That page range is *reported* by another session and not yet checked. It would give a count of riots independent of HO 42.
3. A single trip to The National Archives at Kew for HO 50 (military correspondence) and selected HO 43 volumes. Neither is digitised. Caitlyn is in Rugby, so it's a day trip; the alternative is a paid researcher or TNA's copying service.

**Questions put to JV:**
- What counts as a request: only those made to the Home Secretary, or any request for military help?
- Do requests to *keep* troops count?
- Should the period extend past 1801?
- Is there budget for a Kew trip?

## Known problems
- The network settings for this environment have blocked `uhra.herts.ac.uk` (Bend's thesis) at least once. Retrying later worked.
- An earlier session dated the Oxford reply 1801. It is HO 43/12 pp. 106–7, **8 Sep 1800**.
- Whether troops were *requested* at Oxford in 1800 is disputed: Gee says they were, Bend says Portland sent them without being asked. Check HO 42/51 before logging it.
- The Contentious Gatherings dataset (Horn & Tilly, ICPSR 8872) covers the London region only for 1758–1820. It is **not** a national count of riots.
- Use they/them for people unless their pronouns are known.
