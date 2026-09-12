---
name: legal-research-orchestrator
description: LEGAL_RESEARCH_ORCHESTRATOR — meta-skill koji NE zamenjuje ni ne duplira druge skill-ove, nego bira KOJE od njih treba primeniti, kojim redosledom, i kako se njihovi rezultati povezuju u jednu finalnu, proverljivu sintezu. Aktivirati na početku svakog netrivijalnog pravnoistraživačkog/analitičkog zadatka (analiza predmeta, analiza presude, poređenje sa praksom, istraživanje pitanja, provera teze, izrada podneska) da bi se odredio put kroz sistem skill-ova — pre nego što se uđe u bilo koji pojedinačan skill.
---

# LEGAL_RESEARCH_ORCHESTRATOR

## Svrha
Orkestrira: `16-case-extractor`, `17-case-law-analyzer`, `15-poredjenje-sudske-prakse`, `18-devils-advocate` — i, po potrebi, ostatak postojećeg sistema skill-ova (`01`-`14`). Ne aktivirati skill samo zato što postoji — aktivirati ga kad njegova funkcija doprinosi pouzdanosti analize.

## Podela odgovornosti (ne dozvoliti preklapanje)
| Komponenta | Funkcija |
|---|---|
| `16-case-extractor` | Rekonstrukcija i strukturiranje KONKRETNOG predmeta iz njegovih dokumenata. |
| `17-case-law-analyzer` | Dubinska analiza POJEDINAČNE sudske odluke. |
| `15-poredjenje-sudske-prakse` | Poređenje predmeta, odluka i pravnih stavova (koristi izlaze prethodna dva). |
| `18-devils-advocate` | Adversarial/red-team provera analize (napada, ne potvrđuje). |
| `19-legal-research-orchestrator` (ovaj skill) | Upravljanje CELIM workflow-om — bira redosled, ne radi sam analitički posao drugih skill-ova. |
| `20-legal-knowledge-record-standard` | KNOWLEDGE LAYER — trajno strukturirano čuvanje proverenih rezultata i njihovih međusobnih veza (CASE_RECORD/JUDGMENT_RECORD/SCHOLARSHIP_RECORD/ISSUE_RECORD u `01_PREDMETI/*/_AI/`, `05_IZVORI/SUDSKA-PRAKSA/_ANALIZE/`, `05_IZVORI/LITERATURA/_ANALIZE/`, `03_TAKSONOMIJA/PRAVNA-PITANJA/`). |
| `22-legal-knowledge-retriever` | Pretraga/sinteza CELOG Knowledge Layer-a na zahtev "izbaci mi sve o X" — prethodi dubinskoj analizi, daje materijal ostalim komponentama. |
| `21-legal-model-builder` | Sinteza generičkih, ponovo upotrebljivih pravnih modela iz više izvora (`04_OBRASCI/GENERISANI_MODELI/`). |

Svaka komponenta radi SAMO svoju funkciju — npr. `16` nikad ne poredi sa drugim predmetom (to je `15`), `17` nikad ne napada sopstveni nalaz (to je `18`), `18` nikad sam ne menja zaključak bez ponovne provere od strane orchestratora (v. tačku 13-14 ispod).

## 0. Knowledge-first, source-verified
Pre pokretanja novog istraživanja, PRVO proveriti da li u Knowledge Layer-u (`_AI/`, `05_IZVORI/*/_ANALIZE/`, `03_TAKSONOMIJA/PRAVNA-PITANJA/`) već postoji relevantan zapis. Ali postojeći analitički zapis NIJE automatski istina — hijerarhija pouzdanosti:

**ORIGINAL SOURCE > VERIFIED STRUCTURED RECORD (RELIABILITY: FULL_TEXT_VERIFIED) > CURRENT SYNTHESIS > UNVERIFIED ANALYTICAL NOTE**

Ako postoji sumnja — vratiti se originalnom izvoru (v. `20-legal-knowledge-record-standard`, odeljak X i XIV).

## 1. Osnovno pravilo
Nikad ne počinjati od željenog ishoda. Osnovni tok:

**MATERIJAL → STRUKTURIRANJE → PRAVNO PITANJE → IZVORI → ANALIZA PRAKSE → POREĐENJE → KONTRAANALIZA → REVIZIJA → ZAKLJUČAK**

Ne preskakati raniju fazu ako kasnija zavisi od nje.

## 2. TRIAGE — prvo utvrditi vrstu zadatka
- **TYPE A — Analiza predmeta** ("analiziraj predmet", "šta je sporno", "kakva nam je pozicija") → `16-case-extractor` (ili lakši `01-analiza-predmeta` za jednostavan predmet), zatim ostali skill-ovi po potrebi.
- **TYPE B — Analiza sudske odluke** ("analiziraj ovu presudu", "koji je ratio") → `17-case-law-analyzer`. Ne aktivirati ostale skill-ove ako nisu potrebni.
- **TYPE C — Poređenje predmeta sa praksom** ("da li nam ova presuda pomaže", "uporedi sa našim predmetom") → `16-case-extractor` → `17-case-law-analyzer` → `15-poredjenje-sudske-prakse`.
- **TYPE D — Istraživanje pravnog pitanja** ("istraži ovo pitanje", "kakva je sudska praksa") → identifikovati pravno pitanje (v. `04-pravno-istrazivanje`) → pretražiti korpus (propisi, praksa, ustavnosudska praksa, međunarodna praksa, literatura — v. `10-teorijska-analiza`, `11-strucni-clanci`) → `17-case-law-analyzer` na relevantne odluke → `15-poredjenje-sudske-prakse` ako ih ima više.
- **TYPE E — Provera postojeće teze** ("da li je ovo tačno", "proveri moju argumentaciju", "pronađi slabosti") → NE potvrđivati tezu prvo — primeniti `18-devils-advocate` odmah; po potrebi vratiti se na `17-case-law-analyzer`/`15-poredjenje-sudske-prakse`.
- **TYPE F — Izrada podneska** ("napiši tužbu/žalbu/odgovor/podnesak") → NE preći odmah na pisanje. Prvo: CASE → LAW → COMPARISON → ADVERSARIAL CHECK (`16`→`17`→`15`→`18`), zatim `07-izrada-akta` koristeći taj rezultat.

## 3. Material inventory
Pre složene analize klasifikovati dostupan materijal — kategorije NEMAJU istu pravnu snagu:
- **CASE MATERIAL** — tužbe, odgovori, podnesci, dokazi, nalazi veštaka, zapisnici, rešenja, presude, žalbe.
- **PRIMARY LAW** — zakoni, podzakonski akti, Ustav, međunarodni ugovori.
- **CASE LAW** — domaće presude, odluke Ustavnog suda, ESLJP, ESP, druga relevantna praksa.
- **SCHOLARSHIP** — doktorske disertacije, monografije, naučni radovi, komentari zakona, stručni članci (`05_IZVORI/LITERATURA/`, `05_IZVORI/CASOPISI/`).

## 4. Ne analizirati ceo korpus mehanički
Kod velikog broja dokumenata, prvo **RELEVANCE SCREENING** — za svaki potencijalni izvor proceniti: isto pravno pitanje; istu normu; slične odlučne činjenice; hijerarhijski značaj; vremensku relevantnost; potencijalni konflikt sa drugim izvorima. Tek onda dubinski analizirati najrelevantnije. Ne zaključivati da izvor nije relevantan samo zato što ne sadrži iste ključne reči.

## 5. Query decomposition
Složeno pitanje razložiti na potpitanja (materijalnopravno, procesno, legitimacija, rokovi, teret dokazivanja, primenljiva praksa) — istražiti svako zasebno, pa ponovo sintetizovati.

## 6-9. Faze
- **CASE_EXTRACTION PHASE** — `16-case-extractor` ako postoji konkretan predmet; CASE MAP je činjenična osnova daljeg rada. Ako novi dokument menja CASE MAP: **STOP → UPDATE CASE MAP → REASSESS**.
- **CASE LAW PHASE** — `17-case-law-analyzer` na svaku odluku koja može materijalno uticati na zaključak (DECISIVE FACTS, LEGAL ISSUE, RULE, RATIO DECIDENDI, OUTCOME, SCOPE, DISTINGUISHING). Ne koristiti sentencu kao zamenu za analizu cele odluke ako je cela dostupna.
- **SCHOLARSHIP PHASE** — izdvojiti tezu autora, argument, protivargument, praksu koju analizira, kritiku prakse, strane izvore, razvoj instituta, otvorena pitanja. Ako autor citira odluku dostupnu u korpusu — proveriti primarni izvor, ne oslanjati se na autorovo prepričavanje.
- **COMPARISON PHASE** — `15-poredjenje-sudske-prakse`, tek kad ima dovoljno analiziranog materijala. Poređenje mora počivati na DECISIVE FACTS ↔ DECISIVE FACTS, ne na KEYWORD↔KEYWORD ili LEGAL TOPIC↔LEGAL TOPIC.

## 10. Conflict detection
Aktivno tražiti: **FACT CONFLICT** (dva dokumenta različito opisuju istu činjenicu); **EVIDENCE CONFLICT**; **CASE LAW CONFLICT** (sudovi različito rešavaju suštinski isto pitanje u uporedivim činjeničnim situacijama — v. primenjen primer `20-U-26267-20.md` vs `12-U-16603-19.md`); **SCHOLARSHIP CONFLICT**; **SOURCE CONFLICT** (sekundarni izvor drugačije predstavlja primarni). Kad se otkrije konflikt — NE PRIKRIVATI GA, objasniti ga i utvrditi da li se može razrešiti.

## 11. Temporal control
Za svaki značajan zaključak proveriti: relevantan datum pravnog odnosa; propis koji je tada važio; kasnije izmene; prelazne odredbe; datum sudske odluke; kasniju praksu. **Novija odluka nije automatski relevantnija** ako primenjuje drugačiji pravni režim.

## 12. Source hierarchy
Proceniti pravnu snagu, sud/organ, instancu, neposrednost izvora, datum, činjeničnu sličnost, da li je stav kasnije prihvaćen ili napušten. Ne tretirati odluku najvišeg suda kao automatski primenljivu ako rešava DRUGO pravno pitanje ili drugačije činjenično stanje.

## 13-14. Adversarial check + revision loop
Kod svake složene analize koja vodi praktičnom zaključku — `18-devils-advocate`, sa CASE MAP-om, predloženim zaključkom, najjačom i suprotnom praksom, literaturom, dokaznom osnovom. Posle izveštaja:
- prigovor nije osnovan → objasniti zašto;
- delimično osnovan → ograničiti zaključak;
- osnovan → izmeniti zaključak;
- otkriva nedostatak izvora → vratiti se na RESEARCH;
- otkriva problem sa činjenicama → vratiti se na `16-case-extractor`;
- otkriva pogrešno tumačenje presude → vratiti se na `17-case-law-analyzer`;
- otkriva pogrešnu analogiju → vratiti se na `15-poredjenje-sudske-prakse`.

Petlja **ANALYZE → ATTACK → REVISE** dok zaključak ne postane stabilan ili dok se ne utvrdi da materijal ne dozvoljava siguran zaključak.

## 14b. Update Knowledge Layer
Kad složena analiza proizvede NOVO, provereno znanje (posle revizije/DEVILS_ADVOCATE), utvrditi da li treba ažurirati: `CASE_RECORD` (novi ili promenjeni CASE PIVOT, promenjena CONFIDENCE), `JUDGMENT_RECORD` (ako je odluka dublje analizirana ili je otkriven RELATED ISSUE), `SCHOLARSHIP_RECORD`, `ISSUE_RECORD` (nova SUPPORTING/CONTRARY praksa, promenjena CURRENT SYNTHESIS). **Ne čuvati svaku sopstvenu misao** — čuvati SAMO informacije koje imaju buduću pravnu vrednost i mogu se povezati sa proverljivim izvorom (v. `20-legal-knowledge-record-standard`, odeljak XVII). Ovaj korak ide PRE finalne sinteze (tačka 21).

## 15. Anti-confirmation-bias pravilo
Korisnikova teza NIJE činjenica. "Smatram da je X" = **HYPOTHESIS TO TEST**, ne instrukcija da se dokaže X. Obavezno tražiti i EVIDENCE FOR X i EVIDENCE AGAINST X.

## 16-19. Kontrola izvora
Nikad ne izmišljati odluku, broj predmeta, datum, stranicu, citat, pravni stav, činjenicu, sadržaj dokumenta. Kad nešto nije moguće proveriti: **UNVERIFIED**. Kad materijal ne dozvoljava zaključak: **INSUFFICIENT EVIDENCE**. Svaka značajna tvrdnja mora imati izvor (CASE DOCUMENT→stranica/odeljak; CASE LAW→sud/broj/datum/pasus; SCHOLARSHIP→autor/naslov/strana; PROPIS→akt/član/verzija). Kad su dostupna i primarni i sekundarni izvor: **PRIMARY > SECONDARY** (npr. disertacija opisuje presudu → pronaći samu presudu → analizirati presudu, zatim odvojeno kako je autor tumači). Ne mešati nivoe tvrdnji: FACT / PARTY CLAIM / EVIDENCE / COURT FINDING / LEGAL RULE / CASE LAW POSITION / SCHOLARLY POSITION / ANALYTICAL INFERENCE — nikad jedan nivo ne predstavljati kao drugi.

## 20. Confidence calibration
Ne koristiti kategoričan jezik ako izvori ne opravdavaju kategoričan zaključak: **HIGH** (snažni primarni izvori, stabilna praksa, visoka činjenična sličnost) / **MODERATE** (dobar osnov, ali i materijalna neizvesnost) / **LOW** (praksa podeljena, činjenice nepotpune, nema neposrednog izvora) — uvek objasniti uzrok neizvesnosti.

## 21. Final synthesis — struktura
KRATAK ODGOVOR → ODLUČNE ČINJENICE → PRAVNO PITANJE → PRAVNI OKVIR → NAJRELEVANTNIJA SUDSKA PRAKSA (rangirana po primenljivosti, NE po tome da li podržava željeni ishod) → POREĐENJE → LITERATURA → ARGUMENTI U PRILOG → ARGUMENTI PROTIV → DISTINGUISHING → RED TEAM RESULT (iz `18-devils-advocate`) → ZAKLJUČAK (posle adversarial kontrole) → CONFIDENCE (HIGH/MODERATE/LOW) → ŠTA MOŽE PROMENITI ZAKLJUČAK.

Ne prikazivati korisniku samo mehaničke output-e pojedinačnih skill-ova — sintetizovati ih.

## 22. Mapiranje komandi korisnika
- "ANALIZIRAJ PREDMET" → `16` → identifikacija pravnih pitanja → relevantna praksa → `17` → `15` (ako treba) → `18` → FINAL SYNTHESIS.
- "ANALIZIRAJ PRESUDU" → `17`.
- "UPOREDI" → `16` (ako postoji predmet) → `17` → `15`.
- "ISTRAŽI" → query decomposition → relevance screening → primarni izvori → sudska praksa → literatura → `17` → `15` → `18` → synthesis.
- "PROVERI MOJU TEZU" → hypothesis to test → izvori ZA → izvori PROTIV → `18` → revised conclusion.
- "NAPIŠI PODNESAK" → prvo sprovesti potrebnu analizu, zatim `07-izrada-akta` sa proverenim rezultatima. Ne žrtvovati pravnu tačnost radi retorike.

Pun tok za TYPE A/C/D: `16` → identifikacija ISSUE (provera `03_TAKSONOMIJA/PRAVNA-PITANJA/` pre novog zapisa, v. `16` t. 11) → provera postojećeg Knowledge Layer-a (t. 0) → relevance screening (t. 4) → `17` → literatura → `15` → preliminaran zaključak → `18` → provera prigovora (t. 13-14) → RESEARCH/ANALYSIS LOOP ako treba → revidiran zaključak → **UPDATE KNOWLEDGE LAYER (t. 14b)** → FINAL SYNTHESIS (t. 21). Ne mora svaki jednostavan zadatak aktivirati sve korake.

## Self-check (integration test)
Pre nego što se ovaj workflow proglasi ispravnim za konkretan slučaj, proveriti: da li je isti fajl/zapis ažuriran DVA PUTA od strane različitih koraka (duplirani rad); da li jedan skill tiho prepisuje rezultat drugog umesto da ga nadograđuje; da li postoji kružna zavisnost (npr. `15` čeka na `17` koji čeka na `15`); da li je ANALYZE→ATTACK→REVISE petlja (t. 13-14) stvarno terminisala, ne beskonačna. Ako se otkrije problem — vratiti se na `13. Osnovno pravilo` (MINIMUM NECESSARY CHANGE se ne primenjuje na ispravku stvarne greške u workflow-u).

## 23. Autonomy rule
Ne tražiti od korisnika da kaže koji skill treba upotrebiti — sam izabrati odgovarajući workflow prema zadatku. Ako se tokom rada otkrije novo pitanje koje zahteva drugi skill — aktivirati ga bez traženja odobrenja.

## 24. Stop rule
Ne nastavljati istraživanje kad novi izvori više ne menjaju analizu, glavni pravni stavovi su identifikovani, suprotni stavovi provereni, najrelevantnije odluke analizirane, materijalne razlike utvrđene. Cilj NIJE maksimalan broj izvora — cilj je pravno relevantna pokrivenost.

## 25. Krajnji cilj
Ne uverljiv tekst — nego analiza koja je **PROVERLJIVA → ČINJENIČNO UTEMELJENA → IZVORNO POTKREPLJENA → KONTRAARGUMENTIMA TESTIRANA → PRAVNO ODBRANJIVA**. Uvek prednost tačnosti nad samouverenošću, i relevantnosti nad količinom.
