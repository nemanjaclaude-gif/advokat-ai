---
name: legal-knowledge-record-standard
description: LEGAL KNOWLEDGE RECORD STANDARD — definiše kako se rezultati analize pravnih izvora i predmeta strukturiraju i ČUVAJU radi kasnijeg pretraživanja, poređenja i ponovne upotrebe, tako da jednom pažljivo analiziran izvor ne mora svaki put iznova da se analizira od početka. Svaki analitički zapis ostaje povezan sa originalnim izvorom i NIKAD ga ne zamenjuje. Koristiti za NOVE, značajne zapise (posebno JUDGMENT_RECORD za presude koje su same po sebi vredan presedan) — postojeći, jednostavniji CASE CARD format iz `05-sudska-praksa` ostaje važeći za brzo katalogiranje; ovaj standard je puna, unakrsno-povezana verzija za predmete/izvore gde se očekuje česta ponovna upotreba i poređenje.
---

# LEGAL KNOWLEDGE RECORD STANDARD

## I. Osnovne vrste zapisa
- `CASE_RECORD` — za konkretan predmet
- `JUDGMENT_RECORD` — za sudsku odluku
- `SCHOLARSHIP_RECORD` — za disertaciju, monografiju ili naučni rad
- `LEGAL_RULE_RECORD` — za pravnu normu ili pravno pitanje
- `ISSUE_RECORD` — za pravno pitanje koje povezuje različite izvore

## II. JUDGMENT_RECORD
```
RECORD TYPE: JUDGMENT_RECORD
IDENTIFICATION: sud / broj predmeta / datum / vrsta odluke / instanca / pravna oblast / podoblast / izvor dokumenta
PROCEDURAL POSTURE: u kojoj fazi postupka je odluka doneta, o čemu je sud odlučivao
MATERIAL FACTS: samo materijalno relevantne činjenice
DECISIVE FACTS: činjenice koje su neposredno uticale na ishod
LEGAL ISSUE: precizno formulisano pravno pitanje
APPLICABLE LAW: primenjeni propisi i konkretne odredbe
HOLDING: neposredan odgovor suda na pravno pitanje
RATIO DECIDENDI: "AKO [odlučne činjenice] ONDA [pravna posledica] ZATO ŠTO [pravni razlog]"
OBITER DICTA: odvojeno, ako postoji
OUTCOME: ishod
SCOPE: dokle doseže pravni stav
LIMITATIONS: šta se iz ove odluke NE može zaključiti
DISTINGUISHING FACTORS: činjenice čija bi promena mogla dovesti do drugačijeg ishoda
AUTHORITIES CITED: druge odluke/izvori na koje se sud poziva
RELATED ISSUES: pravna pitanja sa kojima je odluka povezana
KEYWORDS: pravni koncepti (ne oslanjati pretragu isključivo na njih)
RELIABILITY: FULL_TEXT_VERIFIED / PARTIAL_TEXT / HEADNOTE_ONLY / SECONDARY_SOURCE_ONLY
```

## III. CASE_RECORD
```
RECORD TYPE: CASE_RECORD
IDENTIFICATION: sud/organ / broj predmeta / stranke / vrsta postupka / predmet spora / faza postupka
CLAIMS: zahtevi stranaka
PROCEDURAL HISTORY: hronologija postupka
UNDISPUTED FACTS / DISPUTED FACTS
EVIDENCE MAP: za svaku važnu činjenicu — FACT → SUPPORTING EVIDENCE → CONTRARY EVIDENCE → STATUS
CLAIMANT/PETITIONER ARGUMENTS — RESPONDENT/DEFENDANT ARGUMENTS
LEGAL ISSUES: spisak, svakom dodeliti ISSUE-ID
APPLICABLE LAW
RELEVANT CASE LAW: poveži sa postojećim JUDGMENT_RECORD zapisima
RELEVANT SCHOLARSHIP: poveži sa SCHOLARSHIP_RECORD
CASE PIVOTS
STRENGTHS / VULNERABILITIES / MISSING MATERIAL
CURRENT ASSESSMENT
CONFIDENCE: HIGH / MODERATE / LOW
LAST UPDATED: datum
```

## IV. SCHOLARSHIP_RECORD
```
RECORD TYPE: SCHOLARSHIP_RECORD
IDENTIFICATION: autor / naslov / vrsta rada / godina / izdavač-fakultet / izvor
SUBJECT
ISSUES DISCUSSED
AUTHOR'S MAIN THESIS
ARGUMENTS
COUNTERPOSITIONS
CASE LAW DISCUSSED: za svaku odluku — sud / broj / strana rada / kako je autor tumači / da li je originalna odluka dostupna
CRITICISM OF CASE LAW: gde i zašto autor kritikuje praksu
FOREIGN LAW / ECHR-EU LAW
KEY PROPOSITIONS: sa stranicom za svaku
RELATED ISSUES: poveži sa ISSUE_RECORD
RELIABILITY NOTE: jasno označiti da je ovo DOKTRINARNI izvor, ne sudski autoritet
```

## V. ISSUE_RECORD (centralni element sistema)
Ne organizovati znanje samo prema dokumentima — organizovati ga i prema PRAVNIM PITANJIMA.
```
ISSUE-ID: jedinstveni identifikator
ISSUE: precizno pravno pitanje (NE "Faktička eksproprijacija", nego "Od kog momenta vlasniku pripada pravo na naknadu kad je privatna nepokretnost fakticki privedena javnoj nameni bez formalnog postupka eksproprijacije?")
APPLICABLE LAW
SUPPORTING CASE LAW / CONTRARY CASE LAW / DISTINGUISHABLE CASE LAW (prividno relevantne odluke koje počivaju na drugačijim odlučnim činjenicama)
CONSTITUTIONAL COURT / ECHR-EU
SCHOLARSHIP
CURRENT SYNTHESIS
UNRESOLVED QUESTIONS
RELATED ISSUES
LAST UPDATED
```

## VI. Relationships (odnosi između zapisa)
Koristiti: `SUPPORTS`, `CONTRADICTS`, `DISTINGUISHES`, `FOLLOWS`, `OVERRULES`, `CRITICIZES`, `CITES`, `INTERPRETS`, `APPLIES`, `FACTUALLY_SIMILAR`, `FACTUALLY_DISTINCT`, `RELATED_TO`.

Primer: `JUDGMENT_A SUPPORTS ISSUE_004` / `SCHOLARSHIP_12 CRITICIZES JUDGMENT_A` / `JUDGMENT_B DISTINGUISHES JUDGMENT_A`.

## VII. Sličnost NIJE autoritet
Ne mešati: koliko je odluka AUTORITATIVNA (AUTHORITY SCORE: HIGH/MEDIUM/LOW — na osnovu suda, instance, statusa) i koliko je ČINJENIČNO SLIČNA (FACTUAL SIMILARITY: HIGH/MEDIUM/LOW — na osnovu DECISIVE FACTS). Odluka nižeg suda može biti veoma činjenično slična, ali sa manjom autoritativnom težinom. Takođe označiti ISSUE MATCH: DIRECT / PARTIAL / REMOTE.

## VIII. Update rule
Kad stigne nov dokument u postojećem predmetu — NE praviti ceo CASE_RECORD ponovo. Prvo utvrditi **WHAT CHANGED?**, zatim ažurirati: hronologiju, dokaznu mapu, sporne činjenice, pravna pitanja, CASE PIVOTS, procenu rizika, confidence. Sačuvati informaciju šta je promenjeno (v. već ustaljenu konvenciju "Dopuna (datum)" u ovom projektu, npr. `PRAVNA-ANALIZA.md` predmeta Roković-02).

## IX. Nova sudska praksa
Kad se pojavi nova odluka: (1) formirati JUDGMENT_RECORD; (2) utvrditi kom ISSUE_RECORD-u pripada; (3) uporediti sa postojećim ključnim odlukama; (4) utvrditi da li CONFIRMS / DEVELOPS / LIMITS / CONTRADICTS / CHANGES postojeću sintezu; (5) ažurirati ISSUE_RECORD ako je potrebno.

## X. Provera primarnog izvora
Ako SCHOLARSHIP_RECORD navodi presudu, a kasnije postane dostupan njen pun tekst: formirati JUDGMENT_RECORD, proveriti šta presuda STVARNO kaže, uporediti sa tumačenjem autora, i ako postoji razlika — zabeležiti je (v. već primenjen primer: `9-U-1864-10-2007.md`, status "VERIFIED posredno" preko disertacije Ane Katić, čeka proveru punog teksta). Nikad ne menjati sadržaj primarnog izvora da bi odgovarao sekundarnom.

## XI. Kontrola duplikata
Pre kreiranja novog zapisa proveriti da li već postoji: za presudu — SUD + BROJ PREDMETA + DATUM; za literaturu — AUTOR + NASLOV + GODINA; za predmet — SUD + BROJ PREDMETA. Ne praviti više zapisa za isti izvor samo zato što je dostavljen u drugom fajlu.

## XII. Provenance (poreklo)
Svaki zapis mora zadržati vezu sa originalnim dokumentom: SOURCE → PAGE/SECTION → ANALYTICAL PROPOSITION. Ako se analitički zapis i originalni izvor razlikuju: **ORIGINALNI IZVOR IMA PREDNOST.**

## XIII. Ponašanje pri pretrazi
Pri istraživanju novog predmeta, ne pretraživati samo nazive/keywords — pretraživati prema: LEGAL ISSUE, DECISIVE FACTS, APPLICABLE RULE, RATIO, CASE PIVOTS, DISTINGUISHING FACTORS. Cilj je konceptualno i činjenično pronalaženje srodnih slučajeva.

## XIV. Pravilo ponovne upotrebe
Ako postoji JUDGMENT_RECORD označen FULL_TEXT_VERIFIED — ne analizirati celu presudu ponovo bez razloga, koristiti postojeći zapis. Vratiti se originalnoj presudi ako: novi predmet postavlja drugačije pravno pitanje; potreban je tačan citat; postoji sumnja u prethodnu analizu; nova praksa menja značaj odluke; `18-devils-advocate` identifikuje problem.

## XV. Princip knowledge graph-a
Tretirati bazu kao MREŽU, ne kao folder PDF dokumenata: **CASE ↔ LEGAL ISSUE ↔ JUDGMENT ↔ LEGAL RULE ↔ SCHOLARSHIP ↔ ECHR/EU/USTAVNI SUD**. Cilj: novi predmet automatski aktivira relevantna pravna pitanja, a pravna pitanja aktiviraju relevantne izvore.

## XVI. Kontrola kvaliteta
Pre čuvanja zapisa proveriti: da li je činjenica ZAISTA u izvoru; da li je ratio pravilno identifikovan; da li je stav autora odvojen od stava suda; da li su stranice provere; da li su suprotni stavovi zabeleženi; da li su distinguishing factors identifikovani; da li je reliability pravilno označen. Ako nisi siguran: **`REQUIRES_VERIFICATION`** — ne pretpostavljati.

## XVII. Osnovni princip
Ne graditi bazu "Claude-ovih zaključaka". Graditi bazu: **IZVOR → STRUKTURIRANA ANALIZA → VEZA SA DRUGIM IZVORIMA → PROVERLJIV ZAKLJUČAK**. Svaki analitički zaključak mora moći da se vrati do originalnog izvora.

## Odnos prema postojećem sistemu ovog projekta
- Postojeći CASE CARD format (`05-sudska-praksa`) je LAKŠA, brža verzija JUDGMENT_RECORD-a — dovoljan za rutinsko katalogiranje. Prelazak na pun JUDGMENT_RECORD format je vredan kad se očekuje česta ponovna upotreba/poređenje (npr. presedan koji se koristi u više predmeta, kao `12-U-16603-19.md` / `20-U-26267-20.md`).
- `16-case-extractor` je CASE MAP metodologija (kako doći do sadržaja) — CASE_RECORD iznad je format u kome se taj sadržaj TRAJNO čuva radi ponovne upotrebe.
- `17-case-law-analyzer` je metodologija ČITANJA jedne odluke — JUDGMENT_RECORD je format u kome se taj rezultat čuva.
- Postojeći doktorski/naučni radovi u `05_IZVORI/LITERATURA/` katalogovani su prema README konvenciji (Autor/Naslov/Godina/Napomena) — SCHOLARSHIP_RECORD je dublja opcija kad se rad stvarno detaljno koristi u analizi (ne za sve 239+ katalogovanih dela odjednom).
- Migracija POSTOJEĆIH, već napravljenih CASE CARD-ova u pun RECORD format NIJE automatski nalog za retroaktivan rad — raditi postepeno, po potrebi, ne kao jednokratan veliki poduhvat, osim ako korisnik izričito to zatraži.
