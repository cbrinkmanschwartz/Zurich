# Voth project: requests for troops in England, 1790s

Archive research by Caitlyn Brinkman-Schwartz for Prof. Hans-Joachim Voth (JV), UBS Center, University of Zurich. This is not a software project. The work is reading scanned Home Office papers and building a dataset from them, plus writing notes, reports and emails to JV.

## What JV wants
- **Priority:** civil **requests for troops** are about 10× more important than decisions to grant them. JV already has troop locations. Requests could become the project's core identification, i.e. the main data the paper's argument rests on.
- **Also in scope:**
  - **barracks** (requests to build them, or arguments about where to put them)
  - **corps founded, armed or expanded** (volunteer corps, militia, armed associations). Key quotes tie them to "suppress any Insurrections".
- **Geography:** England only. Wales (including Monmouthshire), Scotland and Ireland are cut entirely (CBS, 8 Nov 2026): don't log them or list them in coverage notes.
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
- **Caitlyn's Kew photos (from 6 Nov 2026):** they arrive in the same Dropbox folder as `Photo DD-MM-YYYY, HH MM SS.jpg`. Sort by time. A new volume starts with a photo whose **centre is a bright yellow TNA slip** (name + document reference); a small slip at the edge of a page photo is NOT a boundary. Photos before the first slip in a batch belong to the volume already open. Sort them into scratchpad folders named after the volume (e.g. `kew/HO 50-47/`). In the log: Call number = that volume, File = photo filename, PDF page no. = photo index, Image status = "Own photo taken". **Exception (7 Nov 2026):** HO 50/24 has no yellow slip; its boundary is a photo of the shelfmark on a cardboard background, taken shortly before 2pm on 7 Nov. **No retakes are possible:** log unreadable or unphotographed pages as ILLEGIBLE (in the row's Notes if a logged letter is affected, and in the Legend coverage note).

## Coverage so far (6 Nov 2026)
- **Read in full:**
  - HO 42/16 (1790), 17, 18 (Sep 1790–Jun 1791; routine, low yield)
  - HO 42/19 (Jul-Dec 1791), 20, 21, 22, 23 (1792 - early 1793), 24, 25, 26 (Jan–15 Sep 1793; HO 42/26 ends f.551)
  - HO 42/28, 29 (Jan–Apr 1794; 30 rows, mostly 1794 corps plans; 1 borderline request: Penzance volunteers vs smugglers)
  - HO 42/31, 32 (Jun–Jul 1794; 17 rows; Exeter wool-combers keep-troops request; Derby, Newcastle, Reading barracks; 42/32_01 is Bow St accounts)
  - HO 42/179 (Aug 1818; 56 rows, mostly Manchester E529 / Stockport E531 continued; Bolton; Byng refusing troops for wage disputes)
  - HO 42/152 (Jul–Aug 1816, complete): Preston riot E545, Leicester E538, Frome, Bolton, Workington/Whitehaven seamen, Bridgnorth/Wolverhampton/Dudley colliers and ironworkers, Derby depot, Newbury
  - HO 42/153, 154 (Sep–Oct 1816, complete; ~75 rows): silver-coin riots (Hull, Sunderland), North Shields seamen, Wigan, Bolton, Blackburn, Manchester, Stockport, Notts frame-breaking (Lambley), Birmingham riot 28 Oct, Walsall; Sidmouth yeomanry circular 20 Oct
  - HO 42/122 (complete), HO 42/123 (May 1812, complete), HO 42/124 parts 1–6 (Jun 1812): Apr 1812 peak (Manchester, Oldham, Rochdale, Penistone, Bridport, Salisbury, Carlisle, Birmingham, Huddersfield; Grey/Clay refusing for lack of troops); May (Lieutenancy schemes, Local Militia divisions, Watch & Ward; Wigan, Nottingham 14 May, Frome); Jun (Lancaster gaol guard). Grey: magistrates 'would have a guard in every town if they were indulged'.
  - HO 42/120 (complete), HO 42/121 (Mar 1812, complete), HO 42/122 parts 1–4 (Apr 1812): Notts assizes troop dispute (Coldham vs county JPs, Judge Bayley), Huddersfield (Radcliffe, Grey refusals), Leeds, Rawdon/Gildersome, Boston/Spilsby enclosure, Manchester Exchange riot, Middleton, Carlisle food riot, Cornwall tinners, Sheffield arms-depot riot, Barnsley, Bristol, Trowbridge, Birmingham, Coventry, Wigan, Leigh. HO 40/2 complete.
  - HO 42/119 (Jan 1812, complete) and HO 42/120 parts 01–07 (Feb 1812): Notts/Leics frame-breaking E169/E170 continued; office copies of Nov–Dec 1811 letters NOT re-logged; Leics 'Feb 1812' draft reply (HO 42/120_06) judged a misdated copy of the 9 Dec 1811 reply and dropped (CHECK).
  - HO 40/1 (complete) and HO 40/2 parts 01–23 except 20 (Feb 1812–Mar 1813): Luddites. Bolton/Westhoughton E562, Stockport E563, Ashton/Hyde/Mottram, West Riding (Huddersfield, Wakefield Lieutenancy, Halifax), Manchester (Maitland), Leicester, New Mills. HO 40/2 is mostly Maj-Gen Acland's military in-letters: local requests appear as officers' reports. Duplicate copies (Secret Committee '(B)' copies) dropped.
  - HO 42/178 (Jul 1818; 34 rows: Manchester spinners E529, Stockport power-loom weavers E531, Wigan, Westbury election, Holborn fire)
  - HO 42/30 (May 1794)
  - HO 42/33 (Aug–Dec 1794)
  - HO 42/34 (Jan–Mar 1795)
  - HO 42/35–40 (Jun 1795–May 1797), 41 (Jun–Dec 1797)
  - HO 42/57, 62 (May–Dec 1801)
  - HO 42/51 (Sep 1800, all parts), 52, 53 (Oct–Nov 1800), 55 (Dec 1800), 56 (Jan–Apr 1801, interdepartmental 'Domestic' volume, low yield)
  - HO 42/42–45 (1798), 46, 47, 48 (1799; security papers, low yield), 49, 50 (Jan–Aug 1800), 61 (Jan–Apr 1801)
  - HO 42/113 (Domestic, Oct–Dec 1811), 117, 118 (Aug–Dec 1811, Luddites)
  - HO 42/150, 151 (May–Jun 1816)
  - HO 40/3 (Oct 1816–Feb 1818: the 1817 Lords Secret Committee bundle; Spa Fields, Hampden clubs, Leicestershire, Lancashire; NOT 1812 Luddites)
  - **HO 50/47** (Volunteers, Jan–Jun 1800): CBS's own Kew photos, 6 Nov 2026; complete (slip photo 11:24:10)
  - HO 50/23 (Militia, Jan–May 1795): only the last photos (13:48, 27–30 May 1795) uploaded; slip 11:46, rest to follow
  - **HO 50/48** (CHECK: inferred; Volunteers 27 Jun–29 Dec 1800, not 1799 as catalogued): photos 6 Nov 14:17–15:03; ff.37–179 and 210–304 ('End') read, 21 rows. MISSING ff.1–36 (early Jul 1800) and ff.180–209 (c.8–23 Nov 1800; deleted). Photo 14 17 48 ILLEGIBLE (c.ff.44–47).
  - HO 50/30 (Militia misc.; spine photo confirms): photos 15:45–15:53, Dec 1798–Jun 1799 (Militia Reduction Bill), 2 borderline rows. 15 photos at 15:03:49 uploaded empty (lost).
  - **Batch 3 (uploaded 8 Nov; 1,322 files, 666 unique; 73 rows HO42-0797–0869):** HO 50/47 front (Leica L1170109–164, Dec 1799–Feb 1800; now complete); HO 50/10 (C-in-C 1800) ff.7–264 'END', missing ff.245–258; HO 51/61 (3 openings, 0 rows); HO 50/56 (1800–02); HO 50/55 (CHECK: letters 1793–99); HO 50/50 (18 Mar–16 Jun 1801); HO 50/389 (Dec 1800–May 1801, gap c.19 Apr–12 May); HO 50/325 slip only; HO 50/24 only ff.85–87 (Oct 1795).
  - Leica camera files (L117xxxx.JPG) have no date (clock unset); they precede the phone photos. Sort by file number.
  - WO 32/7238 (1885 Yeomanry precedence file; formation dates of yeomanry regiments): photographed 13:58–13:59; no rows logged (reference CHECK)
  - HO 42/27 (Nov–Dec 1793; ff.1–c.884; parts 06–07 are London Gazette accounts)
  - HO 42/187–194, 195–198 (May–Nov 1819; 1819 complete, incl. Peterloo, episode E253)
  - 31 Oct 2026: the 78 PDFs above were read by parallel sub-agents under a common brief (scratchpad BRIEF.md); rows merged and spot-checked by the coordinator (2 of 2 checked rows correct; one signatory name corrected). Treat CHECK: flags in those rows with extra care.
- **Log:** 1513 events; see Summary sheet for the breakdown; 29 leads.
- **Uploaded, not yet read (8 Nov):** HO 42/124 parts 7–11 (Jun 1812). In scratchpad pdf_new/.
- **Kew plan:** `Kew_orders.xlsx` (Friday 21 on-demand; Saturday 12 add-ins; already ordered). See notes/03.
- **Not uploaded (as of 5 Nov):** HO 40/1–2 (1812 Luddites; digitised); HO 42/28–29, 31–32 (Jan–Jul 1794); 119–131 (1812); 178–179 (1818); 152–157 (Jul–Dec 1816); 158–172 (1817). All are free TNA downloads per Discovery.
- **Theme from 1800 volumes:** volunteers unreliable or mutinous on food prices (Bolton, Potteries, Stafford, Exmouth/E. Devon); some reinforcements were unrequested (Birmingham, Nov 1800).

## Period and series (decided 26 Oct 2026)
- **Period:** 1790–1819.
- **Series:**
  - **Up to 1811:** HO 42 only.
  - **From 1812:** HO 40 (Disturbances Correspondence) as well as HO 42. Disturbance letters were moved out of HO 42 into HO 40 from 1812 (Bend, ch. 3).
  - **Caution:** the split wasn't continuous. Bend finds disturbance letters back in HO 42 for Jul 1813–Jun 1816 and Mar 1818–Jan 1820, so check both series for 1812–1819.
  - This rule is also in the spreadsheet's Legend sheet.

**Order for reading the remaining HO 42 volumes** (dates from TNA's Discovery API, `/API/records/v1/children/C8906`):
1. **Food crises:**
   - 35, 36, 37, 38 (Jun 1795–Apr 1796)
   - 49, 50, 51, 52, 53, 55 (1800)
   - 56, 61 (Jan–Apr 1801)
2. **Next:**
   - 19 (late 1791, Priestley riots)
   - 20–23 (1792–early 1793)
   - 39–40 (May 1796–May 1797, militia riots)
   - 57, 62 (May–Dec 1801)
   - 150–151 (May–Jun 1816, East Anglian bread riots)
   - 113, 117, 118 (late 1811, Luddites)
3. **Later:**
   - 42–45 (1798)
   - 178–179 (Jul–Aug 1818)
   - 187–198 (1819, Peterloo)
   - 24–29, 31–32 (rest of 1793–94)
   - 17–18 (rest of 1790–91)
4. **Skip:**
   - 63–112 (1802–10, quiet)
   - 54 (questionnaires)
   - 59–60 (Bruce report)

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
- Legend coverage cell hit Excel's 32,767-char limit on 31 Oct 2026: notes from HO 42/42_4 to 6 Nov were truncated and lost. Continuation row 'Coverage - status (cont., 8 Nov 2026)' added; flush.py now starts new rows before the limit.
- Fixed 5 Nov 2026: addrows.py had been stretching the Lookups range in the Home Secretary formula (should be $A$2:$A$20 / $B$2:$B$20). All rows reset; values were unaffected.
- The network settings for this environment have blocked `uhra.herts.ac.uk` (Bend's thesis) at least once. Retrying later worked.
- An earlier session dated the Oxford reply 1801. It is HO 43/12 pp. 106–7, **8 Sep 1800**.
- Oxford 1800 RESOLVED (HO 42/51 ff.59, 94): Hughes was "surprized" troops came; they were sent unrequested (Bend correct). Logged as HO42-0094 (Other).
- The Contentious Gatherings dataset (Horn & Tilly, ICPSR 8872) covers the London region only for 1758–1820. It is **not** a national count of riots.
- Use they/them for people unless their pronouns are known.
