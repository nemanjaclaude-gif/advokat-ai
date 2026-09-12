---
name: legal-knowledge-retriever
description: LEGAL_KNOWLEDGE_RETRIEVER — na zahtev korisnika ("izbaci mi sve o X", "šta imamo o ovome", "istraži sve", "daj mi najjače") pronalazi, povezuje, sistematizuje i prikazuje SVE materijalno relevantne informacije iz celog Legal AI sistema o pravnom pitanju/institutu/činjeničnom kontekstu — NE obična keyword pretraga, nego semantičko+konceptualno pretraživanje sa detekcijom konflikata i sintezom potkrepljenom izvorima. Koristiti kad korisnik traži širok pregled postojećeg znanja pre nego što se uđe u dubinsku analizu (`19-legal-research-orchestrator` upravlja REDOSLEDOM koraka; ovaj skill je ulazna PRETRAGA koja im daje materijal).
---

# LEGAL_KNOWLEDGE_RETRIEVER

Cilj: **USER QUESTION/CONTEXT → LEGAL ISSUE IDENTIFICATION → SEMANTIC+CONCEPTUAL RETRIEVAL → SVE VRSTE IZVORA → DEDUPLIKACIJA → DETEKCIJA KONFLIKATA → SINTEZA POTKREPLJENA IZVORIMA → POTPUN ISTRAŽIVAČKI DOSIJE.**

Kad korisnik kaže "izbaci mi sve o X" — zadatak NIJE vratiti listu fajlova. Zadatak je: **PRONAĆI + RAZUMETI + POVEZATI + KLASIFIKOVATI + PROVERITI + PRIKAZATI OBE STRANE + SINTETIZOVATI.**

## 1. Izvori za pretragu
Proveriti STVARNU strukturu radnog prostora (ne pretpostaviti da direktorijum postoji), posebno: `01_PREDMETI/` i `01_PREDMETI/*/_AI/`; `03_TAKSONOMIJA/` i `03_TAKSONOMIJA/PRAVNA-PITANJA/`; `04_OBRASCI/` i `04_OBRASCI/GENERISANI_MODELI/`; `05_IZVORI/PROPISI/`; `05_IZVORI/SUDSKA-PRAKSA/` i `.../_ANALIZE/`; `05_IZVORI/LITERATURA/` i `.../_ANALIZE/`; `05_IZVORI/CASOPISI/` i `.../_ANALIZE/`. Ako sistem ima pristup spoljnim izvorima i korisnik traži aktuelno/potpuno istraživanje — pretražiti i njih, ali JASNO razdvojiti **LOCAL KNOWLEDGE** od **EXTERNAL RESEARCH** u izlazu.

## 2. Razumevanje upita
Korisnik ne mora znati tačan naziv pravnog instituta. Upit razložiti na VIŠE istraživačkih pravaca (SEARCH PATHS) — ne pretpostaviti da su pojmovi pravno ekvivalentni, samo polazne tačke koje se zatim pravno proveravaju. Primer: "naknada za korišćenje zemljišta pre dosuđivanja naknade za faktičku eksproprijaciju" → faktička eksproprijacija; privođenje zemljišta javnoj nameni; ograničenje prava svojine; naknada za korišćenje; sticanje bez osnova; korist jedinice lokalne samouprave; pozitivne obaveze javne vlasti; ustavna/konvencijska pitanja.

## 3. Proširenje pitanja (ISSUE EXPANSION)
Za svako pitanje identifikovati: PRIMARY ISSUE, SUB-ISSUES, RELATED ISSUES, OPPOSING ISSUES, PROCEDURAL ISSUES, EVIDENTIARY ISSUES, TEMPORAL ISSUES (kad su relevantna).

## 4. Pretraga izvan ključnih reči
Ne tražiti samo dokumente sa istim rečima kao upit. Tražiti i gde: isti problem ima drugi naziv; isti ratio postoji u drugom činjeničnom kontekstu; propis nije označen istim terminom; literatura analizira isti problem pod širim institutom; presuda rešava pitanje implicitno; raniji predmet sadrži koristan argument; suprotna strana postavlja relevantan kontraargument. Koristiti: LEXICAL MATCH, SEMANTIC MATCH, ISSUE MATCH, FACTUAL CONTEXT MATCH, CITATION RELATIONSHIPS.

## 5. Iterativna pretraga
Ne završavati posle prvih dobrih rezultata: INITIAL QUERY → rezultati → novi termini/presude/autori/instituti → SECONDARY QUERY → citation chasing → related ISSUE search → contrary authority search → saturation check. Ako izvor upućuje na drugi potencijalno značajan izvor, proveriti i njega ako je dostupan.

## 6. Obe strane pitanja
"Sve na temu" NE znači "sve što potvrđuje korisnikovu tezu". Obavezno tražiti: SUPPORTING, CONTRARY, DISTINGUISHABLE, AMBIGUOUS, EVOLUTION/CHANGE OF APPROACH. Posebno OZNAČITI izvor koji može ozbiljno ugroziti korisnikovu tezu.

## 7. Hijerarhija izvora
- **PRIMARY/AUTHORITATIVE**: važeći propisi; odluke nadležnih sudova; Ustavni sud; ESLJP; EU pravo kad je relevantno.
- **SECONDARY**: monografije, disertacije, naučni radovi, komentari zakona, stručni članci.
- **INTERNAL KNOWLEDGE**: raniji predmeti, interne analize, modeli, raniji pravni memorandumi — **interni akt NIJE pravni autoritet**.

## 8. Preuzimanje sudske prakse
Za pronađene odluke prikazati (kad je dostupno): sud, broj, datum, LEGAL ISSUE, DECISIVE FACTS, RATIO, ishod, odnos prema istraživanom pitanju, RELIABILITY, putanju do originala, putanju do JUDGMENT_RECORD. Ako postoji samo analitički zapis a original nije proveren — to jasno označiti.

## 9. Preuzimanje literature
Prikazati: autora, naslov, godinu, relevantno poglavlje, relevantne strane AKO su pouzdano poznate (ne izmišljati broj stranice), tezu autora, odnos prema pitanju, presude/propise na koje autor upućuje, da li podržava/kritikuje/problematizuje pristup.

## 10. Pretraga internih predmeta
Pretražiti `01_PREDMETI/`. Ako se isto/srodno pitanje već pojavilo, prikazati: predmet, ISSUE, relevantnu činjeničnu sličnost, korišćene izvore, raniji zaključak, šta se može ponovo upotrebiti. **RANIJI PREDMET ≠ PRAVNI AUTORITET.**

## 11. Kontrola duplikata
Isti izvor može postojati kao PDF, kao analiza, u predmetu, kao citat u literaturi, kao ISSUE referenca — NE predstavljati ga kao četiri različita autoriteta. Napraviti JEDAN SOURCE NODE i prikazati njegove veze.

## 12. Detekcija konflikta
Ako izvori nisu saglasni, NE prikrivati konflikt — napraviti **CONFLICT MAP**: POSITION A → izvori / POSITION B → izvori / POSITION C → izvori, i analizirati mogući razlog razlike (različite činjenice, različit vremenski režim, različita pravna pitanja, različit nivo suda, promena prakse, različito tumačenje, stvarna protivrečnost). V. primenjen primer: ISSUE-0002 (numeracija ZZP).

## 13. Vremenska analiza
Kad je relevantno, postaviti rezultate hronološki, posebno otkriti OLD APPROACH → TRANSITION → CURRENT APPROACH. **Novija odluka nije automatski važnija** ako rešava drugo pitanje.

## 14. Pretraga po činjeničnom kontekstu
Korisnik može tražiti pretragu po ČINJENICAMA, ne po pravnom terminu (npr. "nađi sve gde je zemljište postalo ulica, a formalna eksproprijacija nije sprovedena") — tražiti FACT PATTERN prvo, tek onda identifikovati pravne institute i ISSUE.

## 15. Režimi izlaza
- "Izbaci mi sve" → FULL RESEARCH DOSSIER (v. tačka 16).
- "Daj mi samo praksu" → ograničiti na CASE LAW.
- "Daj literaturu" → ograničiti na SCHOLARSHIP.
- "Šta imamo o ovome?" → prvenstveno LOCAL KNOWLEDGE.
- "Istraži sve" → LOCAL KNOWLEDGE + dostupan EXTERNAL RESEARCH.
- "Daj mi najjače" → rangirati po AUTHORITY × ISSUE MATCH × FACTUAL SIMILARITY × RELIABILITY.

## 16. FULL RESEARCH DOSSIER — struktura
1. RESEARCH QUESTION (precizno formulisano)
2. EXECUTIVE SYNTHESIS (šta celina izvora trenutno pokazuje)
3. APPLICABLE LAW
4. SUPPORTING CASE LAW (od najjačeg ka slabijem)
5. CONTRARY CASE LAW (od najopasnijeg ka slabijem)
6. DISTINGUISHABLE/RELATED CASE LAW
7. CONSTITUTIONAL/ECHR/EU MATERIAL (ako relevantno)
8. SCHOLARSHIP
9. INTERNAL CASES (šta je već rađeno u postojećim predmetima)
10. EXISTING MODELS/ARGUMENTS (korisni postojeći materijali)
11. CONFLICT MAP
12. EVOLUTION OF THE LAW (ako postoji razvoj prakse)
13. STRONGEST ARGUMENT FOR
14. STRONGEST ARGUMENT AGAINST
15. UNRESOLVED QUESTIONS
16. SOURCE GAPS (šta nedostaje da istraživanje bude potpunije)
17. SOURCE INDEX (kompletna lista korišćenih izvora sa putanjama/provenance podacima)

## 17. Potpunost
Nikad ne tvrditi "ovo su SVI postojeći izvori" osim ako se stvarno može potvrditi iscrpnost pretraženog korpusa. Razlikovati: **ALL IDENTIFIED RELEVANT SOURCES IN AVAILABLE CORPUS** naspram **POTENTIALLY INCOMPLETE EXTERNAL RESEARCH**.

## 18. Provera izvora
Ako se pravni stav pojavljuje samo u starom podnesku, internoj belešci, literaturi koja prepričava presudu, ili neproverenom analitičkom zapisu — NE predstavljati ga kao direktan stav suda. Tražiti primarni izvor kad je dostupan. **ORIGINAL SOURCE WINS** (v. primenjen primer: ISSUE-0002, zvaničan tekst zakona ispravio grešku iz jedne stvarne presude).

## 19. Integracija sa Knowledge Layer-om
Koristiti Knowledge Layer kao INDEKS I MAPU znanja, ne kao zamenu za izvore. Posebno koristiti `ISSUE_RECORD` za pronalaženje već poznatih veza. Ako se tokom istraživanja otkrije nova važna veza (JUDGMENT↔ISSUE, SCHOLARSHIP↔ISSUE, CASE↔ISSUE, JUDGMENT↔JUDGMENT) — evidentirati je po pravilima `20-legal-knowledge-record-standard`.

## 20. Ne menjati znanje samo zato što je pronađeno
Ovaj skill je PRE SVEGA retrieval+synthesis. Ne menjati VERIFIED zapis samo zato što je pronađen nov izvor. Ako nov izvor potencijalno menja postojeću sintezu, označiti: **KNOWLEDGE UPDATE CANDIDATE** i proslediti odgovarajućem workflow-u za proveru (v. `19-legal-research-orchestrator`, odeljak 14b).

## 21. Odnos prema drugim skill-ovima
`22` (ovaj skill) pronalazi materijal → `24-legal-position-synthesizer` izvlači i klasifikuje stavove iz tog materijala (ko šta tvrdi — propis/sud/autor/kancelarija/model/AI) → `17-case-law-analyzer` dubinski analizira važnu presudu (rezultat postaje COURT POSITION za `24`) → `15-poredjenje-sudske-prakse` poredi praksu/stavove sa konkretnim predmetom → `18-devils-advocate` testira zaključak → `21-legal-model-builder` koristi pronađeno i sintetizovano znanje za izradu akta/modela → `19-legal-research-orchestrator` odlučuje KADA i KAKO se ovi skill-ovi aktiviraju. `22` sam NE klasifikuje stavove po tipu izvora — to je isključivo posao `24` (v. taj skill).
