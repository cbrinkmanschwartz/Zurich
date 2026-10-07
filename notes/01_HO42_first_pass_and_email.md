# Source 1: First pass at HO 42 and JV's email (Sep 2026)

## Scope agreed with JV
- **Priority:** requests for troops are about 10× more important than decisions to grant them. JV already has good data on where troops were.
- **Main data source:** HO 42 could become the project's core identification. HO 43 (replies) is background only, per JV; see the Bend notes for a revision.
- **Geography:** England only. Wales and Scotland are out.
- **In scope:** barracks.
- **Key quotes:** new militias or volunteer corps, or arms requests, "to suppress any Insurrections".
- **Workflow:**
  1. A broad funnel: glance at each letter's topic; if in doubt, scan it; record metadata and key quotes.
  2. Letter-by-letter transcription later, possibly with a vision-language model (VLM).

## Series assessed
- **HO 40 and HO 41:** not useful for the 1790s. HO 40 starts in 1812 and HO 41 in 1815–16; Bend confirms this.
- **HO 42:** digitised as free TNA PDFs. Contains requests, e.g. Bridgend 1795 (Wales, now out) and the Penzance miners' riots of March 1795.
- **HO 43:** not digitised; 16 volumes fall in the project's years.
- **Caution on folios:** the TNA HO 42 PDFs were made from microfilm *before* a later re-cataloguing put the papers back in order and renumbered the folios. Record both the PDF page and the stamped folio.

## Archive series flagged (not yet checked in person)
| Series | What it is |
|---|---|
| **HO 50** | Military correspondence, 1782–1840, 462 volumes: internal defence, militia and volunteers, returns. https://discovery.nationalarchives.gov.uk/details/r/C8914 |
| **HO 51** | Military out-letters |
| **WO 5** | Secretary at War's marching and militia orders, 1683–1852. https://discovery.nationalarchives.gov.uk/details/r/C14216 |
| **WO 1 / WO 4** | War Office in-letters; Secretary at War out-letters |
| **PC 1** | Privy Council papers (food crises of 1795–96 and 1800–01) |
| **Commissioners of Military Enquiry, 1806–07** | Reports on the Barrack Department (barrack construction) |

## Secondary works flagged
- Roger Wells, *Wretched Faces* (1988) and *Insurrection* (1983)
- John Bohstedt, *Riots and Community Politics* (1983) and *The Politics of Provisions* (2010)
- Clive Emsley, 'The Military and Popular Disorder in England 1790–1801', *JSAHR* (1983). Exact citation not verified.
- Joseph Cozens, PhD (Essex), on civil–military relations and protest, 1790–1805
- J.R. Western, 'The Volunteer Movement as an Anti-Revolutionary Force', *EHR* (1956); Austin Gee, *The British Volunteer Movement* (2003); J.E. Cookson, *The British Armed Nation* (1997)
- Andrew Charlesworth (ed.), *An Atlas of Rural Protest in Britain* (1983)
- **Nancy Horn & Charles Tilly**, 'Catalogs of Contention in Britain, 1758–1834' (Center for Studies of Social Change working paper, New School, 1986), and ICPSR 8872. **Correction:** this covers the *London region only* for 1758–1820, so it cannot give a national count of riots in the 1790s.

## Open methodological issues
1. **Selection:** only some requests reached the Home Office. Others went to local commanders, the Secretary at War or the Lord Lieutenant.
2. **Unit of analysis:** count incidents, not individual letters.
3. **Denominator:** a count of riots independent of HO 42 is needed (Wells, Bohstedt, Charlesworth).
4. **VLM trial:** test on 20–30 folios with varied hands against a careful hand transcription. Clerks' copies in HO 43 will flatter the error rate.

## Deliverable so far
`HO42_extraction_log.xlsx`: 17 rows for England, 13 incidents, 6 requests for troops, covering 1790, 1794 and 1795.
