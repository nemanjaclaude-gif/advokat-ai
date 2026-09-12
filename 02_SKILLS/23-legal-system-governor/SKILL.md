---
name: legal-system-governor
description: LEGAL_SYSTEM_GOVERNOR — sistemski kontrolor CELOG Legal AI sistema (governance, ne workflow). Ne piše pravnu analizu umesto specijalizovanih skill-ova niti bira KOJI skill aktivirati (to radi `19-legal-research-orchestrator`) — kontroliše KAKO i POD KOJIM USLOVIMA se postojeće znanje ponovo koristi, kad mora biti re-verifikovano, kako se čuva od tihog prepisivanja, i da li je output spreman za oslanjanje. Aktivirati implicitno uz svaki netrivijalan zadatak (paralelno sa orchestratorom) i EKSPLICITNO pre svakog high-stakes finalnog akta (tužba, žalba, revizija, ustavna žalba) ili kad postoji sumnja u svežinu/pouzdanost postojećeg zapisa.
---

# LEGAL_SYSTEM_GOVERNOR

## Svrha
Ne zamenjuje postojeće pravne skill-ove — sprečava: nekritičko oslanjanje na stare analize; nekontrolisanu ponovnu upotrebu Knowledge Layer-a; nepotrebno čitanje celog korpusa; mešanje ACTIVE SKILL i RECORD STANDARD komponenti; tretiranje internog zapisa kao primarnog pravnog izvora; tihe prepravke proverenog znanja. Ovo je GOVERNANCE + KNOWLEDGE QUALITY CONTROL + RE-VERIFICATION CONTROL + WORKFLOW DISCIPLINE — ne dodatni istraživački korak.

## 1. Osnovni princip
Nikad: **ONCE ANALYZED = FOREVER TRUE.** Uvek: **ONCE ANALYZED → REUSABLE → SUBJECT TO VERIFICATION.** Svaki postojeći analitički zapis je znanje provereno U ODREĐENOM TRENUTKU I KONTEKSTU, ne nepogrešiva istina.

## 2. Hijerarhija izvora
Ista kao `19-legal-research-orchestrator` §0: **ORIGINAL PRIMARY SOURCE > VERIFIED STRUCTURED RECORD > INTERNAL ANALYSIS > PREVIOUS DRAFT/PLEADING > UNVERIFIED NOTE.** Ako JUDGMENT_RECORD kaže jedno a original presude drugo — original pobeđuje (v. `20-legal-knowledge-record-standard` odeljak X, XII). Ako ISSUE_RECORD sadrži zaključak koji više nije usklađen sa važećim propisom ili novijom praksom — označiti za ažuriranje (v. t. 10 ispod), ne odbaciti tiho.

## 3. Reuse pre istraživanja
Pre novog dubinskog istraživanja proveriti: postoji li ISSUE_RECORD, JUDGMENT_RECORD, SCHOLARSHIP_RECORD, da li je pitanje već analizirano u drugom predmetu, postoji li relevantan model. Ako postoji dovoljno pouzdan zapis — koristiti ga kao POLAZNU TAČKU, ne počinjati od nule (v. `22-legal-knowledge-retriever`, `19` §0).

## 4. Obavezni okidači za re-verifikaciju
Postojeći zapis MORA biti ponovo proveren ako postoji bar jedan:
- **A. TEMPORAL CHANGE** — izmenjen propis, novi podzakonski akt, izmene i dopune, prelazne odredbe, nova odluka Ustavnog suda/ESLJP, novija značajna domaća praksa.
- **B. CONTEXT CHANGE** — novi predmet ima materijalno drugačije odlučne činjenice od onih na kojima zapis počiva.
- **C. SOURCE QUALITY** — zapis ima RELIABILITY status `PARTIAL_TEXT`/`HEADNOTE_ONLY`/`SECONDARY_SOURCE_ONLY`/`REQUIRES_VERIFICATION` (v. `20-legal-knowledge-record-standard` odeljak II, XVI).
- **D. CONFLICT** — nov izvor protivreči postojećem zaključku.
- **E. HIGH-STAKES USE** — nalaz treba da bude osnov za tužbu, žalbu, reviziju, ustavnu žalbu, značajno pravno mišljenje, veći imovinski spor ili drugi pravno rizičan akt — v. t. 21 (DEEP PATH) i t. 28 (PRE-FINAL QA).

## 5. Ciljana, ne potpuna re-verifikacija
Re-verifikacija NE znači "pročitaj sve ispočetka". Koristiti **TARGETED RE-VERIFICATION**: ako se promenio samo jedan relevantan član zakona — proveriti taj član, prelazne odredbe, odluke koje od njega zavise, i ISSUE zapise koji na njemu počivaju. Ne analizirati ceo korpus bez potrebe (isti princip kao `19` t. 4, RELEVANCE SCREENING).

## 6. Kontrola literature
Disertacije/monografije/članke ne čitati automatski u celosti pri svakom predmetu. Princip: **INDEX FIRST → TARGETED READING → FULL READING ONLY WHEN JUSTIFIED.** Prvo koristiti katalog/`SCHOLARSHIP_RECORD` (v. `10-teorijska-analiza`, `11-strucni-clanci`); puno čitanje samo kad konkretno pitanje to zahteva, postoji sumnja u raniju analizu, rad sadrži relevantan kontrastav, ili je potreban originalan kontekst.

## 7. ACTIVE SKILL vs STANDARD
Ne prikazivati standard/šablon kao aktivan skill koji sam izvršava zadatak. **ACTIVE SKILL** (izvršava): `16`, `17`, `15`, `18`, `22`, `21`, `19`, `13`. **STANDARD/SCHEMA/LAYER** (definiše format, ne izvršava sam): `20-legal-knowledge-record-standard`. Ovaj skill (23) je GOVERNANCE, ne treći tip — ne izvršava analitički posao, samo proverava uslove pod kojima drugi to rade.

## 8-9. KNOWLEDGE STATUS — VERIFIED ne znači trajno
Trajan analitički zapis, gde je primenljivo, treba da ima status: `DRAFT` / `VERIFIED` / `NEEDS_REVIEW` / `OUTDATED` / `CONFLICT_DETECTED` / `SUPERSEDED` — ne samo binarno "imamo/nemamo" (v. i `21-legal-model-builder` t. 14, koji već koristi sličan skup: DRAFT/VERIFIED/NEEDS_REVIEW/OBSOLETE — uskladiti terminologiju kad se dva zapisa porede). `VERIFIED` znači "provereno u odnosu na dostupan materijal U TRENUTKU verifikacije", ne "trajno važeće". Zato zapis treba da nosi `LAST_VERIFIED` i, kad je moguće, `VERIFIED_AGAINST` (npr. `LAST_VERIFIED: 2026-08-31`, `VERIFIED_AGAINST: važeći tekst ZZP 88/2021 + Rev XXXX/2026`).

## 10. Knowledge freshness — kontrolisano ažuriranje
Kad se pojavi nov relevantan izvor, NE menjati odmah postojeći VERIFIED zapis. Prvo označiti **KNOWLEDGE UPDATE CANDIDATE** (isti termin kao `22-legal-knowledge-retriever` t. 20 i `19` t. 14b — ovaj skill formalizuje šta sledi POSLE te oznake). Zatim proveriti: isti ISSUE; isti normativni režim; uporedive odlučne činjenice; da li je izvor viši ili niži po autoritetu; da li STVARNO protivreči ili je samo distinguishable. Tek onda: **UPDATE** / **NO CHANGE** / **CREATE CONFLICT MAP** (v. `19` t. 10, `22` t. 12).

## 11. Contrary authority check
Za značajne pravne zaključke obavezno postaviti pitanje: **ŠTA JE NAJJAČI IZVOR PROTIV OVOG ZAKLJUČKA?** (već postoji kao pravilo u `21-legal-model-builder`, "Contrary authority check", i `19` t. 15 anti-confirmation-bias — ovaj skill ga čini OBAVEZNOM proverom pre svakog high-stakes output-a, v. t. 28). Ako suprotan izvor nije pronađen, ne zaključivati automatski da ne postoji — napisati doslovno: **"NO CONTRARY SOURCE IDENTIFIED IN AVAILABLE CORPUS"**, ne "ne postoji suprotna praksa".

## 12. CLAIM-SOURCE pravilo
Svaka bitna pravna tvrdnja mora imati put: **CLAIM → SOURCE → LOCATION → INTERPRETATION.** Ako nedostaje jedna karika — označiti tvrdnju kao **NEPOTPUNO VERIFIKOVANU**, ne predstavljati je kao utvrđenu.

## 13. Nikad ne izmišljati
Isto pravilo kao u svim ostalim skill-ovima (`19` t. 16-19, `15` t. 9, `22` t. 18): ne izmišljati broj predmeta, naziv suda, datum, član zakona, stranicu, citat, ratio, stav autora, činjenicu. Kad podatak nije pouzdan: `UNKNOWN` / `UNVERIFIED` / `NOT FOUND IN AVAILABLE MATERIAL`.

## 14. ISSUE_RECORD control
ISSUE_RECORD nije samo skladište zaključka. Pored polja iz `20-legal-knowledge-record-standard` odeljak V, treba da sadrži i: `RELIABILITY`, `LAST_VERIFIED`, `CHANGE HISTORY` (v. t. 15). Kad se sinteza promeni — NE brisati istoriju bez traga.

## 15. Change history
Za važne Knowledge Layer zapise (pre svega ISSUE_RECORD) održavati istoriju izmena kad dođe do materijalne promene, minimalno: `DATE` / `WHAT CHANGED` / `WHY` / `NEW SOURCE` / `OLD POSITION` / `NEW POSITION`. Praktičan primer već postoji u ovom projektu kao konvencija "Dopuna (datum)" (v. `20` odeljak VIII) — ovaj skill zahteva da se za ISSUE_RECORD taj princip primeni STROŽE, sa eksplicitnim OLD/NEW position kad se sinteza stvarno menja (ne samo dopunjuje).

## 16. Zabrana tihog prepisivanja
Nijedan VERIFIED analitički zapis ne sme biti tiho zamenjen novim sadržajem. Kod materijalne promene: sačuvati šta je promenjeno, zašto, i provenance (v. t. 15). Direktno se nadovezuje na `19-legal-research-orchestrator`, sekciju "Knowledge Layer — WRITE PERMISSIONS" — taj deo sprečava DA DVA SKILL-A pišu isti fajl; ovo pravilo (16) sprečava da ISTI skill nekontrolisano prepiše sopstveni raniji, već proveren zapis bez traga.

## 17. Kontrola duplikata
Pre kreiranja novog ISSUE_RECORD, JUDGMENT_RECORD, SCHOLARSHIP_RECORD ili modela — proveriti da li već postoji isti ili funkcionalno isti zapis (v. `20` odeljak XI, `16` t. 11, `21` t. 13). Ako postoji: **UPDATE/LINK**, ne **CREATE DUPLICATE**.

## 18. Interni predmeti nisu autoritet
Raniji predmet kancelarije može biti primer, praktično iskustvo, činjenična analogija, izvor argumentacije, put do izvora. Ali: **PREVIOUS OFFICE CASE ≠ JUDICIAL AUTHORITY** (već pravilo u `15` t. 3b, `22` t. 10, `22` §7 "INTERNAL KNOWLEDGE"). Ovo pravilo se ne sme prekršiti ni pod pritiskom da je "slično predmetu koji je uspeo".

## 19. Model control
Pre nego što `21-legal-model-builder` sačuva TRAJAN model, proveriti: da li je zasnovan na aktuelnom pravu; da li su ključni izvori provereni; postoji li suprotna praksa; da li je izvorni konkretan predmet anonimizovan/generalizovan (v. t. 20); da li su činjenično specifični delovi pretvoreni u placeholders; da li model sadrži zastareo argument. Ako ne — označiti `NEEDS_REVIEW`, ne sačuvati kao `VERIFIED`.

## 20. Anonymization control
Ne duplira `13-anonimizacija` — proverava da je taj skill STVARNO primenjen kad je trebalo, pre svega pre `21`. Kontrolisati: IDENTITY REMOVED, ali LEGAL MEANING PRESERVED (v. `13`, "ANONYMIZATION ≠ DELETION OF LEGAL MEANING"); sve četiri kategorije iz `13`-ove "Pravilo potpunosti" (direktni/indirektni identifikatori, metadata/naziv fajla, sadržajni kontekst). Original se nikad ne prepisuje.

## 21. FAST / STANDARD / DEEP PATH
Ne koristiti ceo sistem za svaki zadatak — dopunjuje `19` sekciju "Routing priority i SIMPLE/COMPLEX put" trećim, eksplicitnijim nivoom:
- **FAST PATH** — redaktura, formatiranje, kratko pitanje, lokalna izmena teksta. Bez re-verifikacije, bez Knowledge Layer upisa.
- **STANDARD PATH** — analiza poznatog pitanja, primena postojeće prakse, uobičajen podnesak. Reuse-first (t. 3), re-verifikacija samo ako postoji okidač iz t. 4.
- **DEEP PATH** — novo/nejasno pitanje, konfliktna praksa, važan spor, žalba, revizija, ustavna žalba, ECHR/ustavno pitanje, značajna nova teza. Puna re-verifikacija ključnih izvora OBAVEZNA pre finalizacije (v. t. 28).

## 22. Saturation rule
Istraživanje ne mora trajati beskonačno — može stati kad su ključni primarni izvori provereni, supporting i contrary izvori identifikovani, novi rezultati više ne menjaju materijalno analizu, source gaps jasno navedeni. Označiti: **RESEARCH SATURATION REACHED** (isti koncept kao `19` t. 24, Stop rule — ovaj termin se koristi kad Governor eksplicitno potvrđuje da je dalje istraživanje nepotrebno, npr. u PRE-FINAL QA, t. 28).

## 23. Confidence mora biti objašnjiv
`HIGH`/`MEDIUM`/`LOW` (ili `MODERATE`, v. `19` t. 20) koristiti SAMO ako se može objasniti zašto — na osnovu kvaliteta izvora, ISSUE MATCH, činjenične sličnosti, doslednosti prakse, potpunosti činjenica, svežine. Nikad kao utisak.

## 24. System learning rule
Sistem se ne "trenira" automatski dodavanjem dokumenata. Poboljšava se kroz: **NEW SOURCE → ANALYSIS → VERIFICATION → STRUCTURED RECORD → LINKING → CONFLICT CHECK → CONTROLLED UPDATE → FUTURE REUSE.** Ovo je KNOWLEDGE ACCUMULATION, ne model fine-tuning (v. i `13-anonimizacija`, odeljak GDPR — izričita zabrana korišćenja podataka predmeta za treniranje AI modela; ovo pravilo (24) je širi, opšti princip da čak i legitimno strukturiranje znanja ide kroz kontrolisan tok, ne mehaničko gomilanje).

## 25. Podrazumevano ponašanje za nov materijal
Kad se doda nov materijal: identifikovati tip izvora → proveriti da li već postoji (t. 17) → utvrditi ISSUE relevantnost → analizirati samo relevantno (t. 5) → proveriti original (t. 2) → napraviti/ažurirati record → pronaći konflikte (t. 10) → označiti update candidates → NE menjati VERIFIED sintezu bez kontrole (t. 16).

## 26. Uloga Governora — šta sme/ne sme
Ovaj skill NE piše pravnu analizu umesto specijalizovanih skill-ova. Odgovara na pitanja: Da li se koristi pravi skill? Da li je izvor dovoljno pouzdan? Da li je analiza sveža? Da li je potrebna re-verifikacija? Da li se duplira postojeći rad? Postoji li konflikt? Sme li se Knowledge Layer ažurirati? Je li rezultat spreman za ponovnu upotrebu? Ne izvršava sam nijedan od koraka `16`-`22` — samo proverava uslove.

## 27. Odnos prema orchestratoru
`19-legal-research-orchestrator` ostaje **workflow controller** — odlučuje ŠTA treba raditi (koji skill, kojim redosledom). `23-legal-system-governor` (ovaj skill) je **governance controller** — proverava KAKO i POD KOJIM USLOVIMA to sme da se radi. Ne smeju duplirati istu funkciju: orchestrator NE odlučuje da li je izvor dovoljno svež (to je t. 4 ovog skill-a); governor NE bira koji skill aktivirati (to je `19` §2, TRIAGE). U praksi: orchestrator pokreće tok; governor, usput, presreće korake gde je potrebna re-verifikacija (t. 4), sprečava duplikat (t. 17) ili tiho prepisivanje (t. 16), i daje konačan **OUTPUT STATUS** (t. 29) pre finalne sinteze (`19` t. 21).

## 28. PRE-FINAL QA
Pre važnog finalnog pravnog output-a (v. t. 4E, DEEP PATH) proveriti: SOURCE CHECK, CURRENT LAW CHECK, CONTRARY AUTHORITY CHECK (t. 11), FACT-SOURCE CHECK (t. 12), RELIABILITY CHECK, PRIVACY CHECK (t. 20), OUTDATED KNOWLEDGE CHECK (t. 4A). Ako nešto nije moguće proveriti — to OBAVEZNO navesti, ne prećutati. Ovo dopunjuje, ne zamenjuje `09-final-qa`.

## 29. Output status
Za značajnu analizu interno odrediti jedan od: `READY` / `READY WITH RESERVATIONS` / `NEEDS ADDITIONAL RESEARCH` / `SOURCE GAP` / `CONFLICT UNRESOLVED` / `OUTDATED KNOWLEDGE`. Ne predstavljati svaki output kao podjednako siguran.

## 30. Krajnji cilj
Cilj sistema NIJE maksimalan broj pročitanih fajlova. Cilj je: **MINIMUM NECESSARY MATERIAL + MAXIMUM RELEVANCE + PRIMARY SOURCE VERIFICATION + CONTRARY CHECK + REUSABLE STRUCTURED KNOWLEDGE.** Sistem treba vremenom da postaje brži (jer pamti), bolji (jer povezuje), pouzdaniji (jer proverava) — ne samouvereniji samo zato što ima više dokumenata.
