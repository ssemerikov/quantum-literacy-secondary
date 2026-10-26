# Supplementary S1 — Structured search and screening

## Part A. Search log (queries, run times, counts)


One row per completed query run. `meta.count` = total hits reported by the API; `retrieved` = records actually saved. SHA-256 = hash of the saved raw page files' bytes concatenated in page order. `no abstract` = records whose `abstract_inverted_index` is null (OpenAlex) or whose `description` is empty (ERIC). Requests are anonymous (no email). Page 1 URL shown; later pages repeat it with `page=N` (OpenAlex; page 1 of run A used `cursor=*`, see agents/search.md) or the next `start` offset (ERIC); every page URL is in the run manifest and in `search/raw/calls.jsonl`.

| qid | database | exact query string | full request URL (page 1) | UTC timestamp (page 1) | meta.count | retrieved | SHA-256 (concatenated raw pages) | no abstract | raw files |
|---|---|---|---|---|---|---|---|---|---|
| A | OpenAlex | ("quantum physics" OR "quantum mechanics" OR "quantum technology" OR "quantum technologies" OR "quantum information" OR "quantum computing") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (curriculum OR framework OR competence OR competences OR "key concepts" OR Delphi) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22quantum%20physics%22%20OR%20%22quantum%20mechanics%22%20OR%20%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20information%22%20OR%20%22quantum%20computing%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28curriculum%20OR%20framework%20OR%20competence%20OR%20competences%20OR%20%22key%20concepts%22%20OR%20Delphi%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&cursor=%2A | 2026-10-24T15:46:39Z | 222 | 222 | b5dc654cb7557f43d964dd148dc6df150b11076d17859e1e89368f055e26967e | 14 | openalex_A_2026-10-24_p1.json ... p2 |
| C2 | OpenAlex | ("quantum divide" OR "quantum divides") | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22quantum%20divide%22%20OR%20%22quantum%20divides%22%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:48:26Z | 116 | 116 | 7283d22ba05fe9fb08ab11d92d1606ac1c11e743a433f55856d8ea4b49fa979d | 25 | openalex_C2_2026-10-24_p1.json |
| C1 | OpenAlex | ("quantum technology" OR "quantum technologies" OR "quantum computing") AND (equity OR inclusion OR "Global South" OR divide OR divides OR democratization OR democratisation) AND (education OR workforce OR literacy) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20computing%22%29%20AND%20%28equity%20OR%20inclusion%20OR%20%22Global%20South%22%20OR%20divide%20OR%20divides%20OR%20democratization%20OR%20democratisation%29%20AND%20%28education%20OR%20workforce%20OR%20literacy%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:48:29Z | 142 | 142 | 4300f3c5f3e76a86ea4f36873108ca1ce85a0612392e2c473cf6372a812b4655 | 13 | openalex_C1_2026-10-24_p1.json |
| B | OpenAlex | ("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation" OR "entanglement" OR "teleportation" OR "BB84" OR "quantum key distribution" OR "quantum cryptography" OR "qubit" OR "quantum computing" OR "Dirac notation" OR "two-state" OR "quantum sensing" OR "quantum sensor" OR "atomic clock" OR "interferometer") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%20OR%20%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%20OR%20%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22two-state%22%20OR%20%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22interferometer%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:48:38Z | 2397 | 2397 | 2e378c692eb5159f1ad0d1d485cc34e92206f31ed5fa680de28b35829cccedfb | 129 | openalex_B_2026-10-24_p1.json ... p12 |

## Notes (appended; rows above are not rewritten)

- **B (OpenAlex):** the row shows `retrieved` = 2397 rows saved, but these contain **2396 unique** works: W7155694503 appears on two pages (relevance-score tie at a page boundary under `page=N` paging, which is used because anonymous cursor paging is refused with HTTP 401). One of the 2397 matching works was therefore not retrieved by run B; see later notes for whether the sub-queries B1-B5 recovered it. All downstream counts use unique works.
- **A (OpenAlex):** page 1 was requested with `cursor=*` and page 2 with `page=2` (cursor paging refused, HTTP 401); completeness verified: 222 unique works = meta.count 222.
- **Planning counts:** the project plan gives planning-time estimates (A about 222, B about 341, C about 142) but records no planning-time strings; A and C1 reproduce, B does not (2397). The B strings used here are the binding strings from task T1; the discrepancy is unexplained.
| B3 | OpenAlex | ("BB84" OR "quantum key distribution" OR "quantum cryptography") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:53:38Z | 27 | 27 | 9b8d425f426cd88ee6c9d3272a4b900f5d3c3a8422fb1d7d5d347de7bc055ab9 | 3 | openalex_B3_2026-10-24_p1.json |
| B5 | OpenAlex | ("quantum sensing" OR "quantum sensor" OR "atomic clock" OR "metrology" OR "interferometer") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22metrology%22%20OR%20%22interferometer%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:53:40Z | 67 | 67 | 94b7fc96913a25687faca87bf919e8c3327de83a5d68b7360b2ac87c81c9db96 | 7 | openalex_B5_2026-10-24_p1.json |
| B4 | OpenAlex | ("qubit" OR "quantum computing" OR "Dirac notation" OR "complex numbers" OR "two-state") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22complex%20numbers%22%20OR%20%22two-state%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:53:42Z | 437 | 437 | de5df64a5b8aaa14ed46a245f0936f2db6d26edf41e4441169aa669d593fbef6 | 24 | openalex_B4_2026-10-24_p1.json ... p3 |
| B2 | OpenAlex | ("entanglement" OR "teleportation" OR "Bell") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22Bell%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:53:57Z | 1250 | 1250 | b1d031209fc315025ed4c576f935788841c628d1d7bbd542de85ec63c119a7fc | 55 | openalex_B2_2026-10-24_p1.json ... p7 |
| B1 | OpenAlex | ("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation") AND ("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") AND (students OR teaching OR learning OR course) | https://api.openalex.org/works?filter=title_and_abstract.search:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%29%20AND%20%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20AND%20%28students%20OR%20teaching%20OR%20learning%20OR%20course%29,from_publication_date:2010-01-01,to_publication_date:2026-10-24&per-page=200&page=1 | 2026-10-24T15:54:32Z | 1842 | 1842 | d5b023bd9a500c17bdb8293619aa3ca6b3ad3ab23c211c9f5318b854a795a145 | 89 | openalex_B1_2026-10-24_p1.json ... p10 |
- **B1 vs B (consistency):** B1 is a logical subset of B. B1 minus B = 1 work, W2166624804 (2014, Indonesian biology-teaching paper), which is the work lost from run B at the page boundary; it enters the record set through B1. B3 minus B = 0. Every B work occurs in at least one of B1-B5. The union of B and B1-B5 is 3497 unique works.
- **B2:** `retrieved` = 1250 rows but **1248 unique works** (two page-boundary duplicates); two works matching B2 were not retrieved by B2 and cannot be identified with certainty (they may have been retrieved by B or another Bk).
| ERIC-A | ERIC | (title:("quantum physics" OR "quantum mechanics" OR "quantum technology" OR "quantum technologies" OR "quantum information" OR "quantum computing") OR description:("quantum physics" OR "quantum mechanics" OR "quantum technology" OR "quantum technologies" OR "quantum information" OR "quantum computing")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(curriculum OR framework OR competence OR competences OR "key concepts" OR Delphi) OR description:(curriculum OR framework OR competence OR competences OR "key concepts" OR Delphi)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22quantum%20physics%22%20OR%20%22quantum%20mechanics%22%20OR%20%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20information%22%20OR%20%22quantum%20computing%22%29%20OR%20description:%28%22quantum%20physics%22%20OR%20%22quantum%20mechanics%22%20OR%20%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20information%22%20OR%20%22quantum%20computing%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28curriculum%20OR%20framework%20OR%20competence%20OR%20competences%20OR%20%22key%20concepts%22%20OR%20Delphi%29%20OR%20description:%28curriculum%20OR%20framework%20OR%20competence%20OR%20competences%20OR%20%22key%20concepts%22%20OR%20Delphi%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:44Z | 18 | 18 | 9aefbbef07c0de6de551ffa438a21c947d81989489e41e8f172753ad495f7436 | 0 | eric_A_2026-10-24_p1.json |
| ERIC-C1 | ERIC | (title:("quantum technology" OR "quantum technologies" OR "quantum computing") OR description:("quantum technology" OR "quantum technologies" OR "quantum computing")) AND (title:(equity OR inclusion OR "Global South" OR divide OR divides OR democratization OR democratisation) OR description:(equity OR inclusion OR "Global South" OR divide OR divides OR democratization OR democratisation)) AND (title:(education OR workforce OR literacy) OR description:(education OR workforce OR literacy)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20computing%22%29%20OR%20description:%28%22quantum%20technology%22%20OR%20%22quantum%20technologies%22%20OR%20%22quantum%20computing%22%29%29%20AND%20%28title:%28equity%20OR%20inclusion%20OR%20%22Global%20South%22%20OR%20divide%20OR%20divides%20OR%20democratization%20OR%20democratisation%29%20OR%20description:%28equity%20OR%20inclusion%20OR%20%22Global%20South%22%20OR%20divide%20OR%20divides%20OR%20democratization%20OR%20democratisation%29%29%20AND%20%28title:%28education%20OR%20workforce%20OR%20literacy%29%20OR%20description:%28education%20OR%20workforce%20OR%20literacy%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:45Z | 4 | 4 | 5b4aee3ce29f67813d0d3a67ed53c64cec7b42b8b73226a69e6dac5c09679e3d | 0 | eric_C1_2026-10-24_p1.json |
| ERIC-C2 | ERIC | (title:("quantum divide" OR "quantum divides") OR description:("quantum divide" OR "quantum divides")) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22quantum%20divide%22%20OR%20%22quantum%20divides%22%29%20OR%20description:%28%22quantum%20divide%22%20OR%20%22quantum%20divides%22%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:46Z | 0 | 0 | d03a6fc8797e5f99d54d02f9e301f2c7adb87e8aef2cef4e35ff19806cee42a8 | 0 | eric_C2_2026-10-24_p1.json |
| ERIC-B | ERIC | (title:("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation" OR "entanglement" OR "teleportation" OR "BB84" OR "quantum key distribution" OR "quantum cryptography" OR "qubit" OR "quantum computing" OR "Dirac notation" OR "two-state" OR "quantum sensing" OR "quantum sensor" OR "atomic clock" OR "interferometer") OR description:("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation" OR "entanglement" OR "teleportation" OR "BB84" OR "quantum key distribution" OR "quantum cryptography" OR "qubit" OR "quantum computing" OR "Dirac notation" OR "two-state" OR "quantum sensing" OR "quantum sensor" OR "atomic clock" OR "interferometer")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%20OR%20%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%20OR%20%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22two-state%22%20OR%20%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22interferometer%22%29%20OR%20description:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%20OR%20%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%20OR%20%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22two-state%22%20OR%20%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22interferometer%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:46Z | 312 | 312 | a9e31c00887250c7e2570512b9497e12517b168886bd12b0534955c53fcb5ab5 | 0 | eric_B_2026-10-24_p1.json ... p2 |
| ERIC-B1 | ERIC | (title:("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation") OR description:("superposition" OR "interference" OR "Mach-Zehnder" OR "single photon" OR "polarization" OR "polarisation")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%29%20OR%20description:%28%22superposition%22%20OR%20%22interference%22%20OR%20%22Mach-Zehnder%22%20OR%20%22single%20photon%22%20OR%20%22polarization%22%20OR%20%22polarisation%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:51Z | 143 | 143 | bac34306e1121d54911f67ac385a0d264d6a9490dd38ebe409005f6c686cfa71 | 0 | eric_B1_2026-10-24_p1.json |
| ERIC-B2 | ERIC | (title:("entanglement" OR "teleportation" OR "Bell") OR description:("entanglement" OR "teleportation" OR "Bell")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22Bell%22%29%20OR%20description:%28%22entanglement%22%20OR%20%22teleportation%22%20OR%20%22Bell%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:53Z | 154 | 154 | cdd9b192804c26e421d2d13c06bdae3071294863565f3e85319c5523a90d8987 | 0 | eric_B2_2026-10-24_p1.json |
| ERIC-B3 | ERIC | (title:("BB84" OR "quantum key distribution" OR "quantum cryptography") OR description:("BB84" OR "quantum key distribution" OR "quantum cryptography")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%29%20OR%20description:%28%22BB84%22%20OR%20%22quantum%20key%20distribution%22%20OR%20%22quantum%20cryptography%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:55Z | 4 | 4 | 9e178bc422185b782aae3edb2208633c231f8c47c8660ed8b2e7376bc8d881d6 | 0 | eric_B3_2026-10-24_p1.json |
| ERIC-B4 | ERIC | (title:("qubit" OR "quantum computing" OR "Dirac notation" OR "complex numbers" OR "two-state") OR description:("qubit" OR "quantum computing" OR "Dirac notation" OR "complex numbers" OR "two-state")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22complex%20numbers%22%20OR%20%22two-state%22%29%20OR%20description:%28%22qubit%22%20OR%20%22quantum%20computing%22%20OR%20%22Dirac%20notation%22%20OR%20%22complex%20numbers%22%20OR%20%22two-state%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:56Z | 136 | 136 | 89b8bb9d52db61f87835276faffeb5d6ac893d23782887180ff438c7b8fdd2b9 | 0 | eric_B4_2026-10-24_p1.json |
| ERIC-B5 | ERIC | (title:("quantum sensing" OR "quantum sensor" OR "atomic clock" OR "metrology" OR "interferometer") OR description:("quantum sensing" OR "quantum sensor" OR "atomic clock" OR "metrology" OR "interferometer")) AND (title:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university") OR description:("secondary school" OR "high school" OR "upper secondary" OR "lower secondary" OR "middle school" OR "K-12" OR "pre-university")) AND (title:(students OR teaching OR learning OR course) OR description:(students OR teaching OR learning OR course)) AND publicationdateyear:[2010 TO 2026] | https://api.ies.ed.gov/eric/?search=%28title:%28%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22metrology%22%20OR%20%22interferometer%22%29%20OR%20description:%28%22quantum%20sensing%22%20OR%20%22quantum%20sensor%22%20OR%20%22atomic%20clock%22%20OR%20%22metrology%22%20OR%20%22interferometer%22%29%29%20AND%20%28title:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%20OR%20description:%28%22secondary%20school%22%20OR%20%22high%20school%22%20OR%20%22upper%20secondary%22%20OR%20%22lower%20secondary%22%20OR%20%22middle%20school%22%20OR%20%22K-12%22%20OR%20%22pre-university%22%29%29%20AND%20%28title:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%20OR%20description:%28students%20OR%20teaching%20OR%20learning%20OR%20course%29%29%20AND%20publicationdateyear:%5B2010%20TO%202026%5D&format=json&rows=200&start=0&fields=id,title,author,description,publicationdateyear,source,publicationtype,language,peerreviewed,educationlevel,url,issn,isbn,publisher,subject,e_fulltextauth | 2026-10-24T15:57:57Z | 3 | 3 | 35c282677ba06ac1f7f5f116256ac93d0277bfbe0c0c9180e7853529668963f1 | 0 | eric_B5_2026-10-24_p1.json |
- **ERIC:** all runs complete (numFound = unique IDs retrieved). ERIC has no DOI field; a DOI is taken from the `url` field only when it is a doi.org link. ERIC exposes only the publication year, so its window is `publicationdateyear:[2010 TO 2026]` against OpenAlex 2010-01-01 to 2026-10-24. ERIC-C2 was run in addition to the task list (A, B/B1-B5, C1) for parity. ERIC consistency: B1 minus B = 0; B3 minus B = 0; every B record occurs in some Bk; union of B and Bk = 426.
- **Snowballing (OpenAlex, one round, run 2026-10-24 15:52-15:53Z):** seeds resolved in one call `filter=doi:<5 DOIs>`; backward = `filter=openalex:<referenced_works IDs>` (<=100 IDs per call); forward = `filter=cites:<seed W id>` with `page=N`. 12 list calls (1 credit each). Every URL, SHA-256 and per-seed count is in `search/raw/openalex_SB_manifest.json` and `search/raw/calls.jsonl`; per-record pre-filter decisions in `search/snowball_prefilter.csv`. Pre-filter (local, logged): normalised title+abstract must contain >=1 of A first-block phrases AND >=1 SCHOOL-block term, and publication date 2010-01-01..2026-10-24. Retrieved 287 backward + 273 forward rows (per seed); 178 pass keywords; 169 also in window; 125 unique works enter dedup as stream SB (44 not retrieved by any database query).
- **Call audit:** 80 logged network calls in total: OpenAlex search 39 (38 saved pages, including A p1 by `cursor=*`, plus 1 refused with HTTP 401 for cursor paging), OpenAlex list 15 (3 probes + 12 snowball), ERIC 26 (16 syntax probes + 10 result pages). The HTTP 401 is the only non-200 response. Two curl header checks to OpenAlex and one to ERIC were made before caching existed; their bodies were not saved and they feed no count.


## Part B. Screening protocol


Status: frozen before the first screening decision. Its SHA-256 is recorded in the screening log. Changes after freezing appear only as dated amendments in Section 13, and nothing above Section 13 is edited after freezing.

## 1. Purpose and scope

This protocol governs the first-pass (S1) title/abstract screening of the records retrieved by the structured search (task T1; `search/search_log.md`, `search/counts.json`). The search informs a conceptual position paper. It is not a systematic review. The S1 decisions are provisional. The authors verify a defined sample (Section 11), and full-text eligibility (E5, and E3 for empirical studies) is assessed in a later stage that is not covered here.

## 2. Model identity and access

- Screener: Claude (Anthropic), model ID `claude-opus-5-5`.
- Access: Claude Code (Anthropic's command-line agent, Claude Agent SDK), running as a general-purpose sub-agent (task T2, agent name `screen`), started by the main Claude Code session of this revision.
- Screening dates: from 2026-10-24 (times given in UTC). Each decision row carries an ISO-8601 timestamp (`ts`).
- The model received the instruction text reproduced in Sections 4–10 (the task brief's criteria verbatim, plus the interpretations fixed before screening). It saw only the record display defined in Section 7. No web access, full texts or external databases were used for S1 decisions.
- Temperature and sampling settings are not exposed by the access route and were not set. Re-running the model on the same input may therefore not reproduce every decision exactly. The frozen rules, the saved per-batch decision files (`screening/batches/batch_NNN.tsv`) and the rationale stored per record make each decision auditable.

## 3. Inputs (SHA-256 at freezing)

| File | SHA-256 |
|---|---|
| `screening/records_dedup.csv` (4142 records) | 37f950fb748a966d8e75d14a9a45e79b22fbeee10c9bd232cbc467d3d6416563 |
| `screening/abstracts.jsonl` (4142 lines) | b15ef90c6605f486f6e30734e7de0f90ed471d5319fe32153affbd76cec60f33 |
| `screening/dedup_flags.csv` (111 flagged pairs) | 6bc07101e879e217714eabe304bfb7cc030227c214f373779f254aaf5cce03ab |
| `tools/screen/screen.py` (pre-filter, display, apply, sampling) | 2223e067fe3a3d278819324ee6a3891c11339b515318aa21683a1fc4844517f1 |

## 4. Eligibility criteria (verbatim from the task brief / the project plan)

> Include: I1 the work is about education in quantum physics / quantum information science / quantum technologies; I2 learners at ISCED 2–3 (approx. ages 11–19) or a framework/curriculum explicitly for that level; I3 (records whose streams include B only) empirical work (intervention, teaching experiment, interview, classroom study) reporting learners' grade or age; I4 peer-reviewed article, proceedings paper, book chapter, or official framework/curriculum document; I5 full text in English.
>
> Exclude: E1 university-only samples or tertiary-only frameworks; E2 public outreach without a school-age sample (stream B); E3 no age/grade reported (stream B) → decision "context" (not discarded: kept as context-only); E4 not about quantum education (e.g. classical optics, non-education physics, unrelated fields); E5 full text not retrievable (only at full-text stage). Stream C records (divides/equity) are included if they address unequal access/participation in quantum technologies or quantum education at any level (I2 not required for C). Stream A records: framework/curriculum/competence/consensus works for school level. Preprints: decision "uncertain-I4" unless a published version is in the set (dedup_flags.csv lists same-title pairs).

Streams: A = curricula/frameworks; B = classroom studies (B1 superposition/interference/MZI/polarisation, B2 entanglement, B3 BB84/QKD, B4 qubit/Dirac/complex, B5 sensing/clocks/interferometer); C = divides/equity (C1, C2); SB = snowballing; SEED = seed records.

## 5. Interpretations fixed before screening

These interpretations were fixed after reading the data description and before any decision was made. They close gaps that the verbatim criteria leave open.

1. **The content role decides which stream-specific criterion applies, not the retrieval route.** A work can be retrieved by any stream, including SB and SEED, so each record gets one content role, and the criteria for that role apply:
   - **F**: framework, curriculum, competence or consensus work for school level. This covers official curricula and standards, curriculum or textbook analyses and comparisons, competence frameworks, Delphi/expert-consensus studies, and proposed curricula or courses that specify what is taught. Criteria: I1, I2, I4, I5. I3 does not apply.
   - **E**: empirical study with learners (intervention, teaching experiment, interview, classroom study, test or questionnaire administered to learners, outreach programme with participant data). Criteria: I1–I5 (I3 applies).
   - **P**: school-level quantum-education work with no learner data (lesson or activity design, teaching proposal, simulation or tool description, literature review, position or opinion piece).
   - **T**: study whose participants are in-service secondary-school teachers.
   - **D**: work on divides, equity, inclusion, access or participation in quantum technologies or quantum education (the stream-C rule).
   - **O**: anything else.

   The literal brief applies I3 to "records whose streams include B". Applying it by content role instead treats identical works the same whatever query retrieved them. This is an interpretation, and it is reported as one.
2. **E3 at S1.** An abstract cannot show that a full text omits grade or age. So at S1 an E-role record whose abstract states a school-level sample but no grade or age is *included provisionally* with criterion `I1,I2,I4,I5;I3-ft`, and I3/E3 are decided at full text. An E-role record whose abstract states a grade or age gets `I1-I5`.
3. **Works with no learner sample (role P)** report no learners' age or grade, so E3 applies literally: decision `context`, criterion `E3`.
4. **Teacher samples.** Pre-service teachers are a university sample (E1, exclude). In-service secondary-school teachers (role T) are not ISCED 2–3 learners: decision `context`, criterion `notI2-teacher`.
5. **Failing an inclusion criterion that has no E-code** is coded `notI2`, `notI4` or `notI5` (exclude).
6. **Duplicates (`DUP`).** A record that would otherwise be retained is coded `DUP` (exclude) in two cases:
   - it is a copy of another retained record (a pair in `dedup_flags.csv`, or the same work visibly present under another ID);
   - it is a preprint whose published version is in the set.

   Version-of-record priority: journal article, proceedings paper or book chapter over a preprint, repository, dataset or figshare/Zenodo/OSF copy. Between two versions of record, the lower `record_id` is kept. Both members get the flag `possible_duplicate`, and the DUP rationale names the kept ID.
7. **Stream-C rule (role D).** A D-role work passes I1 if it substantively addresses unequal access to or participation in quantum technologies or quantum education. A passing mention is not enough. I2 is not required, but I4, I5 and DUP still apply.
8. **Mixed-level samples** that include ISCED 2–3 learners (for example, "high-school and undergraduate students", K-12) satisfy I2. Community college, first-year university and foundation-year university courses are tertiary (E1). Primary-only (ISCED 0–1) fails I2 (`notI2`).

## 6. Automated pre-filter (applied by `tools/screen/screen.py prefilter`)

All regular expressions are Python `re`, case-insensitive (`re.I`). They are applied to the string `title + " " + abstract`, where the abstract comes from `screening/abstracts.jsonl`. `quantum_term_hit` and `abstract_present` are the T1 columns of `records_dedup.csv`.

- **Rule (a): automatic E4 exclusion.** `quantum_term_hit == "true"` → manual screening. Otherwise, if the abstract is present and neither the secondary regex nor the rule-(c) regex matches → decision `exclude`, criterion `E4-auto`, screener `prefilter-rule-a` (not the model). If the secondary regex matches → manual screening (route `a_rescue`). The secondary regex, verbatim from the brief:
  ```
  photon|wave[- ]particle|duality|Mach[- ]Zehnder|electron diffraction|atomic model|energy levels?|spin|uncertainty principle|tunnel(l)?ing|Planck|photoelectric
  ```
- **Rule (b).** `quantum_term_hit == "false"` and no abstract → manual screening on title/venue/type, flag `no_abstract` (route `b_noabs`).
- **Rule (c): diagnostic rescue, added before screening.** A dry run showed that the secondary regex misses R1084 ("Teaching Diffraction of Light and Electrons", one of six records the search agent named as possibly relevant). Rather than overriding one record by ID, a general diagnostic regex routes every would-be E4-auto record that matches it to manual screening (route `c_rescue`):
  ```
  modern physics|f[ií]sica moderna|\belectrons?\b|\batoms?\b|atomic|wave nature|matter waves?|de broglie|bohr|schr[oö]dinger|heisenberg|nanotechnolog|semiconductor|laser|interferometer|double[- ]slit
  ```
- **Dry-run counts (computed before freezing; the final counts are in `screening/prefilter_counts.json`):**
  - quantum_term_hit true: 860;
  - rule (b): 153;
  - rule (a) rescue: 71;
  - rule (c) rescue: 70;
  - to manual screening: 1154;
  - E4-auto: 2988.
- **Named records:**

  | Record | Route |
  |---|---|
  | R0633 | a_rescue |
  | R0679 | a_rescue |
  | R1651 | a_rescue |
  | R0762 | a_rescue |
  | R1084 | c_rescue |
  | R0055 | b_noabs |

  Reaching manual screening does not imply inclusion. R0633, R0679 and R1651 carry Portuguese language metadata.
- The departure from the literal brief: the `screener` column of E4-auto rows reads `prefilter-rule-a`, not `claude-opus-5-5`, because the model never saw those records.

## 7. What the model saw (display format, `screen.py show K`)

- Records go to manual screening in ascending `record_id` order, in batches of 40 (batch K = queue positions 40(K−1)+1 … 40K of `screening/manual_queue.csv`).
- For each record the display shows:
  - one header line: record_id, streams, databases, type, language metadata, year, venue (first 80 characters), DOI, pre-filter route, abstract length in characters;
  - the full title;
  - the **first 1200 characters** of the abstract verbatim;
  - if the abstract is longer, up to **6 merged keyword-in-context snippets** (±90 characters around each match) from the remainder, for the regex:
    ```
    grade|graders?|year[- ]olds?|years? old|\baged?\b|\bages\b|pupil|school|secondary|K-?12|undergrad|universit|college|teacher|curricul|classroom|outreach|participant|\bn\s*=|sample|equity|inclusi|divide|gender|access|quantum
    ```
  - one line per `dedup_flags.csv` pair involving the record (partner ID, reason, partner DOI).
- The model saw no other text from the abstract.
- **Extraction pass.** For includes of role E or F, a second display (`screen.py full`) shows the first 6000 characters of the abstract plus KWIC from the remainder, for the extraction fields of Section 10. If this fuller reading shows that a grade or age is stated, the include code changes from `I1,I2,I4,I5;I3-ft` to `I1-I5`, and the change is logged.

## 8. Decision and criterion codes

`s1_decision` ∈ {include, exclude, uncertain, context}. The `criterion` field holds exactly one of these codes:

| Decision | Criterion | Meaning |
|---|---|---|
| include | `I1-I5` | Role E; grade or age stated in title/abstract |
| include | `I1,I2,I4,I5;I3-ft` | Role E; school-level sample, grade/age not in the abstract, so I3/E3 is decided at full text |
| include | `I1,I2,I4,I5` | Role F (I3 not applicable) |
| include | `C,I4,I5` | Role D (stream-C rule) |
| context | `E3` | Role P: school-level quantum-education work with no learner sample |
| context | `notI2-teacher` | Role T: in-service secondary teachers |
| uncertain | `I1`, `I2`, `I3`, `I4`, `I5` | The named criterion cannot be decided from the display (`I4` = the brief's "uncertain-I4") |
| exclude | `E4-auto` | Rule (a) |
| exclude | `E4` | Not about quantum education (and not a D-role work) |
| exclude | `E1` | University/tertiary/workforce-only sample or framework; pre-service teachers |
| exclude | `E2` | Public outreach without a school-age sample |
| exclude | `notI2` | No ISCED 2–3 learners (for example, primary only), or no level stated and nothing indicates school level |
| exclude | `notI4` | Publication type outside I4 (Section 9, step 6) |
| exclude | `notI5` | Full text not in English |
| exclude | `DUP` | Copy of a retained record (Section 5.6) |

Other fields:
- `role` ∈ {F, E, P, T, D, O}, as defined in Section 5.1.
- `flags` (semicolon-separated):
  - `no_abstract` (set automatically);
  - `preprint` (set automatically from the type);
  - `non_english`;
  - `possible_duplicate`;
  - `thesis` (added before screening, to keep relevant theses findable).
- `rationale`: at most 25 words, enforced by the apply script.
- `route` ∈ {qhit, a_rescue, b_noabs, c_rescue, a_auto}.

The columns `role` and `route` are appended after the brief's column list.

## 9. Instruction followed for each record

For each displayed record, apply the steps in this order and stop at the first step that yields a decision. Record that step's code.

1. **Role.** Assign the content role (Section 5.1) from the title and abstract.
2. **I1 / E4.**
   - Ask whether the work is about education in quantum physics, quantum information science or quantum technologies. "Education" here means teaching, learning, curriculum, assessment, literacy, outreach or workforce education.
   - Quantum content includes:
     - wave–particle duality, the photoelectric effect and photons;
     - quantum or atomic models, including the Bohr model and orbitals taught in physics or chemistry;
     - quantised energy levels and spectra treated as quantum phenomena;
     - uncertainty, tunnelling, spin, superposition, entanglement and measurement;
     - qubits, quantum computing, QKD and quantum sensing.
   - Not quantum content:
     - classical wave optics (interference, diffraction or polarisation of light treated classically);
     - relativity alone;
     - nuclear or particle physics, or astronomy, without explicit quantum concepts;
     - "quantum learning" or "quantum teaching" as pedagogy brand names;
     - metaphorical "quantum";
     - social or other non-physics uses of "entanglement", "superposition" or "interference";
     - quantum cognition or decision models;
     - quantum physics or computing research with no education component.
   - If the work is not about quantum education → `exclude E4`.
   - A D-role work passes this step under the stream-C rule (Section 5.7).
   - If the abstract cannot show whether quantum content is involved → `uncertain I1`.
3. **E1 / E2** (role D exempt).
   - Learners, sample or framework exclusively post-secondary (university, college, graduate, workforce/professional), or pre-service teachers → `exclude E1`.
   - Public outreach with no school-age sample → `exclude E2`.
4. **I2** (role D exempt).
   - Learners at ISCED 2–3, or a framework/curriculum explicitly for that level, means: lower or upper secondary, middle or high school, grades about 6–13, ages about 11–19, pre-university, A-level or equivalent, or K-12 coverage that includes these grades.
   - Role T passes this step and receives `context notI2-teacher` at step 8.
   - No ISCED 2–3 learners, or no level stated and nothing indicates school level → `exclude notI2`.
   - School level compatible but ambiguous → `uncertain I2`.
5. **I5.**
   - Full text evidently not in English → `exclude notI5` (flag `non_english`). This is judged from the language metadata, the language of the title and abstract, and the venue.
   - If these disagree, for example non-English metadata with an English title and abstract → `uncertain I5`.
6. **I4.** Judged from the type and venue.
   - **Met:**
     - journal article or review (including ERIC "Journal Articles");
     - proceedings or conference paper;
     - book chapter;
     - an official framework or curriculum document (from a ministry, national agency, standards body, intergovernmental body or recognised framework project), whatever its database type.
   - **`exclude notI4`:**
     - dissertation or thesis (flag `thesis`);
     - editorial, paratext, erratum, letter, book review, peer-review report, reference entry;
     - conference abstract only;
     - dataset or software that is not a DUP copy.
   - **`uncertain I4`:**
     - preprint with no published version in the set (flag `preprint`);
     - whole book (monograph or edited volume);
     - report, "other" or standard that is not an official framework/curriculum document;
     - ERIC non-journal documents (Reports, Speeches/Meeting Papers, Collected Works, Guides).
7. **DUP.** Apply Section 5.6.
8. **Final decision by role.**
   - E → `include I1-I5` (grade or age stated) or `include I1,I2,I4,I5;I3-ft`.
   - F → `include I1,I2,I4,I5`.
   - D → `include C,I4,I5`.
   - P → `context E3`.
   - T → `context notI2-teacher`.
9. **Rationale.** Write at most 25 words naming the deciding fact. Add flags.

**Batch procedure.**
1. Print the batch with `screen.py show K`.
2. Decide every record.
3. Write `screening/batches/batch_NNN.tsv` (record_id, decision, criterion, role, flags, rationale).
4. Run `screen.py apply K FILE`. It validates the codes, the 25-word limit and batch completeness, writes `screening/screening.csv` atomically (`.tmp` then rename), and appends a log line to the screening log with the timestamp, batch range, counts by decision and the next batch.

On restart, `screening.csv` is read, and IDs already decided are never overwritten.

**Consistency safeguards.**
- Borderline patterns that recur are written as dated *precedents* in the screening log. A precedent that changes a rule becomes an amendment in Section 13.
- Before sampling, a consistency sweep by category (teacher samples, preprints, no-abstract records, theses, non-English, DUP) checks uniform coding. Any corrections are logged with their IDs.

## 10. Extraction (includes of role E or F; values only if stated in the displayed text)

Fields:
- `country`, `setting`, `grade`, `n`, `design` (short free text);
- `age`, with `age_basis` ∈ {reported, inferred, blank}. Ages are never inferred from grade without marking `inferred`. In this pass ages are recorded only when stated, so `age_basis` is `reported` or blank;
- `topics`: one or more of superposition, interference, MZI, polarisation, entanglement, QKD/BB84, qubit/QC, Dirac/complex, sensing/metrology, nature-of-science, other (as `other:<term>`);
- `representation` ∈ {verbal, visual, real-vector, complex, matrix, unknown}.

Blank means not stated. The brief requires extraction for stream-B includes. It is done for all E- and F-role includes, a superset.

## 11. Verification sample (author check; task T3)

- **Sample:**
  - all `include`, `uncertain` and `context` rows;
  - a 20% random sample of manual excludes (the model's `exclude` decisions, i.e. every exclude except E4-auto);
  - a 5% random sample of E4-auto excludes.
- **Method** (`screen.py sample`):
  1. Create `rng = random.Random(20261024)` (Python 3 `random` module).
  2. Draw `k1 = ceil(0.20 × N_manual_exclude)` IDs from the ascending-sorted manual-exclude ID list, with `rng.sample`.
  3. With the same `rng` instance, draw `k2 = ceil(0.05 × N_E4_auto)` IDs from the sorted E4-auto list.
- Sampled rows get `verify_sample = 1`; all others get 0.
- The sample is written to `screening/verify_packet.csv` (full abstract, S1 decision, empty verifier columns) and `screening/verify_sample.json` (seed, method, the IDs).
- Agreement can be estimated separately for each sampling stratum.

## 12. Outputs

- `screening/screening.csv`: one row per record.
- `screening/manual_queue.csv`.
- `screening/prefilter_counts.json`.
- `screening/batches/`.
- `screening/verify_packet.csv` and `screening/VERIFY_INSTRUCTIONS.md`.
- `screening/screening_counts.json`.
- the screening log: the log, precedents and the SHA-256 of this file.

## 13. Amendments (append-only, dated)

(none at freezing)

### A1 — 2026-10-25T05:29:57Z (display length only; no criterion, code or decision rule changed)
⟦To reduce the usage of the model,⟧ the screening display from batch 13 record 31 (R1475's batch position 31) onward shows the **first 900 characters** of the abstract instead of 1200. The KWIC snippets from the remainder (same regex, ±90 characters, at most 6 snippets), the header fields (record_id, streams, databases, type, language, year, venue, DOI, route, abstract length) and the dedup-pair lines are unchanged; type and language stay in the header because I4 and I5 depend on them. Batches 1–12 (R0001–R1338, 480 records) and batch 13 positions 1–30 were screened with the 1200-character head. Change to tools/screen/screen.py: `show K [HEAD]` takes an optional head length; decision, apply and sampling code unchanged. New tools/screen/screen.py SHA-256: b3425ef377c134bfddf695408e9284030d25f91a8260ed3d4150396ccc58b956 (previous 2223e067fe3a3d278819324ee6a3891c11339b515318aa21683a1fc4844517f1).
A1 erratum (2026-10-25T05:30:08Z): the parenthetical '(R1475's batch position 31)' is wrong; the 900-character head applies from batch 13 position 31 (the first record after R1492) onward.
Display deviation note (2026-10-25T05:33:18Z): for batch 18 positions 21-40 (R2400..R2443) the KWIC lines were filtered out of the display by mistake; titles and 900-character heads were shown. All 20 records are reviews, obituaries, editorials or non-physics topics and were coded E4; they remain in the random-exclude sampling population.
Display deviation note (2026-10-25T05:35:28Z): for batch 21 positions 28-40 (R3558..R3606) display lines were truncated at 1300 characters (KWIC partly cut). All 13 are essays, obituaries, reviews or medical items coded E4.

### A2 — 2026-10-25T05:44:05Z (correction procedure; no criterion changed)
After the last batch, the consistency sweep of Section 9 was run. Its corrections are made only through `screening/corrections.tsv` and `tools/screen/apply_corrections.py` (SHA-256 6036743c8efc6b00b18ced8789f98dd2bf5c6e91542dfa03015b6d92f78890a0). The script logs every change as old -> new in the screening log. Three corrections were made:
- R0136 became DUP once its journal version R0223 appeared later in the queue.
- R0340 was flagged possible_duplicate (same text as R0771).
- R3867 went from include to uncertain I5 (a Turkish-titled version, R3902, exists).

### Display deviation note 2 — 2026-10-25T05:52:08Z
After screening ended, the displays were re-rendered to measure every line that a terminal filter may have shortened.

- **`cut -c1-1500`, batch 12 positions 1–40 (R1133–R1338):** no display line exceeded 1500 characters, so nothing was lost.
- **`cut -c1-1400`, batch 13 positions 1–20 (R1339–R1474):** one KWIC line was cut, for R1427 (1689 characters; a public-private school-improvement paper coded E4).
- **`cut -c1-1500`, batch 19 positions 14–27 (R2464–R2484):** no line exceeded 1500 characters.
- **Truncation at 1300 characters, batch 21 positions 28–40 (see the first note):** KWIC lines were cut for R3564 (1424), R3570 (1433) and R3603 (1670). All three are coded E4 (an essay collection, an obituary, surgical abstracts).
- **Extraction display for R4118–R4136 (KWIC lines filtered):** no abstract in that group exceeds the 6000-character extraction head, so the full abstract was shown for every record.

No decision depended on the truncated text.

### A3 — 2026-10-25T05:52:08Z (precedents that refine the decision procedure; recorded here as required by Section 9)
The following precedents went beyond pure interpretation. They are recorded as amendments with the date of first use (2026-10-24 for batches 1–12, 2026-10-25 for batches 13–29) and examples.

1. **P26 (batch 9): a certain later exclusion overrides an uncertain earlier step.** When an earlier criterion is uncertain but a later one is certain to exclude, the certain exclusion is coded. This departs from Section 9's "stop at the first step that yields a decision", which would code "uncertain". Uncertain is reserved for records whose outcome depends on the open criterion. Example: R0679 (Portuguese metadata with an English title, but a thesis, so notI4).
2. **P13/P22 (batches 4 and 7): some conference abstracts count as proceedings papers.** An OpenAlex "conference-abstract" is treated as a proceedings paper (I4 met) in two cases:
   - its text says "this paper";
   - its DOI is an SPIE proceedings DOI (10.1117/12.*), unless the text says talk, poster or tutorial.

   Affected includes: R0121, R0249, R1615. All other conference abstracts stayed notI4, for example R0059, R0086, R0107, R0233, R0724, R1073, R1114, R1633.
3. **P31 (batch 23): no-abstract stream-C records.**
   - A no-abstract record retrieved by C2 (whose query requires the phrase "quantum divide") is taken as role D: uncertain I4 if it is a preprint, otherwise uncertain I1. Records: R3877, R3903, R4063, R4084.
   - A C1-only no-abstract record is uncertain I1 when its title is societal or QT-related (R3901, R3905, R3908, R3997, R4011), and E4 otherwise (R3863).
4. **P33 (recorded at the end of screening; applied throughout): target grades count, curriculum levels do not.**
   - I3 is met by a stated grade or age of the target learners of the teaching, course or module, even when the measured sample's grades are not reported: R0119 (grades 10–12), R0223 (Years 6–10), R0228 (ages 15–18), R1338 (grade 9 onwards). These entries are marked "(target)" in the extraction fields.
   - A curriculum prerequisite level or the curriculum context of the topic does not meet I3: R0090 ("9th-grade curriculum level"), R0005 ("final year pre-university"). Both stay I3-ft.

## Appendix S1-A — Precedent list (verbatim from the screening log, P1–P32; P33 above)

- **P1.** Teacher or expert surveys whose aim is to determine curriculum content (which topics should be taught) count as consensus works, so role F (R0037, R0006). Teacher surveys on knowledge, readiness, practice or professional development are role T, so context notI2-teacher (R0039, R0008, R0022).
- **P2.** Design-based or teaching-learning-sequence papers that imply classroom trials but report no explicit learner data are role E with I3-ft (R0020, R0005). A study only scheduled or planned, with no data, is role P, so context E3 (R0010).
- **P3.** No-abstract records whose title shows school-level QE but whose role cannot be determined are uncertain I3 (R0019, R0023). Teacher-training titles without an abstract (pre- or in-service unknown) are uncertain I2 (R0032).
- **P4.** Figshare/Zenodo copies are DUP of the journal version, with both members flagged possible_duplicate.
- **P5.** Literature reviews of school-level QE are role P, so context E3 (R0028, R0034).
- **P6.** I3 counts as met only if a specific grade, year or form (grade 9, Year 11, first year of secondary, Form Five) or an age or age range is stated. Level bands ('high school', 'middle school', 'senior secondary') do not meet it, so I3-ft (R0061, R0064).
- **P7.** General chemistry or physics curricula where quantum concepts are background, not focus, are E4 (R0070).
- **P8.** Speculative or fringe physics expositions, including teenagers' theories, are E4, not education research (R0063, R0065, R0067).
- **P9.** Venues that mainly publish non-English articles but show an English title and abstract are uncertain I5 (R0051, New Physics: Sae Mulli).
- **P10.** Supplementary 'additional file' records are notI4 (R0043).
- **P11.** No-abstract records retrieved by A or B whose title shows QE but no level are uncertain I2 (R0044, R0076).
- **P12.** The same study published twice (proceedings plus journal) keeps both records, both flagged possible_duplicate (R0042 with R0014). DUP is used only for copies of the same publication.
- **P13.** See A3.2.
- **P14.** A preprint of a study whose journal version is in the set is DUP even when the title differs (R0138 -> R0097). A preprint of a different paper from the same study stays uncertain I4, flagged possible_duplicate (R0141 vs R0110).
- **P15.** A non-English title plus non-English language metadata gives notI5, even with an English abstract (R0132, R0140, R0160).
- **P16.** A proposal whose implementation is 'under way' with no results is role P, so context E3 (R0122).
- **P17.** QIS or quantum cryptography as one of several topics is E4 (R0154, R0155).
- **P18.** English language metadata with a non-English title is a disagreement, so uncertain I5 (R0199).
- **P19.** Zenodo/OSF speculative 'unified theory' preprints are E4.
- **P20.** A preprint and a later article with near-identical abstracts count as the same publication, so the preprint is DUP (R0185 -> R0186; R0161 -> R0162).
- **P21.** A repository item whose text says 'this talk' is notI4 (R0231).
- **P22.** See A3.2.
- **P23.** Bulletin of the APS items are meeting abstracts, so notI4 (R0262).
- **P24.** Zenodo/OSF/ResearchGate/Knowledge Commons 'article' deposits with no journal venue are uncertain I4 (R0274, R0275, R4090).
- **P25.** Post-quantum (lattice) cryptography activities are uncertain I1, since the content is classical cryptography (R0288).
- **P26.** See A3.1.
- **P27.** Course, TLS or programme designs without learner data are role P (context E3), even when they set out a content progression (R0565). Role F is reserved for works whose main object is curriculum/content selection or analysis.
- **P28.** Magazine news items are notI4 (R0632).
- **P29.** Role D includes works whose main topic is access, inclusion, EDI or the quantum divide in QT/QE (R3859, R3861, R3867). A governance framework counts when equity or the quantum divide is one explicit dimension (R3865, R3876, R4051).
- **P30.** Textbooks and books for advanced high-school-plus-college readers are role P: whole books are uncertain I4, chapters are context E3 (R3807, R3800, R1328).
- **P31.** See A3.3.
- **P32.** [Redacted for anonymous review: this precedent concerns a record that is withheld from the anonymous supplement.]

## 14. Verification result (task T3, 2026-10-26)

- **Who:** one author reviewed the 632 sampled decisions (Section 11).
- **How it was recorded:** the author reported, in a single statement, agreement with every sampled decision and changed none. No row-level record was kept: the packet's verifier cells were empty, and the statement was copied into the `verifier` and `verifier_decision` columns of every sampled row of `screening.csv` (`agree`) by a script, on the author's instruction. These columns therefore record the author's statement, not a separate judgement per row.
- **Sampled rows, by stratum:**

| Stratum | Rows | Changed by the author |
|---|---|---|
| all includes | 145 | 0 |
| all uncertain | 79 | 0 (left undecided) |
| all context-only | 90 | 0 |
| random 20% of manual excludes | 168 | 0 |
| random 5% of E4-auto excludes | 150 | 0 |

- **No agreement statistic is reported.** Because agreement was not recorded row by row, a percentage agreement or a confidence bound on the error rate of the unsampled exclusions would overstate what the record shows.
- **Uncertain records:** the 79 uncertain records were not decided. They were not taken to full text and contribute no evidence.
- **Final decisions:** `final_decision` in `screening.csv` holds the first-pass decision for every row; for sampled rows the author's statement did not change it.
- **Limits:** one author reviewed the sample, so no agreement between authors is available.
