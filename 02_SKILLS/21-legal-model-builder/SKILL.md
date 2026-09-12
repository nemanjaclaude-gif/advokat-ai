---
name: legal-model-builder
description: LEGAL_MODEL_BUILDER — na zahtev korisnika kreira visokokvalitetne, ponovo upotrebljive pravne modele/obrasce/šablone sintezom najboljih proverenih elemenata iz VIŠE relevantnih izvora (postojeći obrasci, stvarni predmeti, propisi, sudska praksa, literatura, Knowledge Layer) — NIKAD kopiranjem jednog starog dokumenta sa zamenjenim imenima. Koristiti kad korisnik traži "napravi model/obrazac/nacrt X", ili kad `14-usavrsavanje-obrazaca` prepozna da je nov generički obrazac vredan izrade.
---

# LEGAL_MODEL_BUILDER

Model NIJE kopija jednog postojećeg dokumenta. Model je **sinteza najboljih proverenih elemenata iz više relevantnih izvora, pretvorena u generalizovan i ponovo upotrebljiv pravni obrazac.**

## 1. Šta se može praviti
Model tužbe, odgovora na tužbu, žalbe, revizije, ustavne žalbe, predloga za izvršenje, prigovora, upravne žalbe, tužbe u upravnom sporu, zahteva, ugovora, punomoćja, pravnog mišljenja, pravne analize, istraživačkog memoranduma, dopisa, internog akta, dokazne liste, strukture argumentacije.

## 2. Izvori koje treba proveriti (samo relevantne, ne mehanički ceo korpus)
`04_OBRASCI/` (uklj. `USAVRSENI-MODELI/`), `01_PREDMETI/` (stvarno korišćeni akti), `05_IZVORI/PROPISI/`, `05_IZVORI/SUDSKA-PRAKSA/` (uklj. `_ANALIZE/`), `05_IZVORI/LITERATURA/` (uklj. `_ANALIZE/`), `05_IZVORI/CASOPISI/`, `03_TAKSONOMIJA/PRAVNA-PITANJA/`, postojeći Knowledge Layer (`_AI/` zapisi).

Kad model zahteva PRAVNU ARGUMENTACIJU (ne samo procesnu formu bez spornog pravnog pitanja) — pre PHASE 2 ispod, koristiti `24-legal-position-synthesizer` da se izvori klasifikuju (NORMATIVE/COURT/SCHOLARLY/OFFICE/MODEL POSITION) i sintetizuju. Model se tada gradi na TOJ sintezi, ne samo na najsličnijem starom modelu (v. §Osnovno pravilo ispod).

## 3. Workflow
- **PHASE 1 — IDENTIFY**: vrsta dokumenta; pravna oblast; procesna faza; svrha; tipičan podnosilac/protivnik; obavezni elementi; varijabilni elementi.
- **PHASE 2 — RETRIEVE**: najrelevantniji postojeći obrasci; uspešno korišćeni dokumenti iz ranijih predmeta; propisi; sudska praksa; `ISSUE_RECORD`; literatura ako doprinosi strukturi/argumentaciji. Ne birati dokument samo zato što ima sličan naziv — oceniti stvarnu primenljivost.

## 4. Ne kopirati jedan stari predmet
Iz VIŠE relevantnih primera izdvojiti: zajedničku strukturu; najbolje formulacije; obavezne procesne elemente; dobre pravne argumente; tipične dokazne predloge; uspešne formulacije petituma; rezervne argumente; tipične greške koje treba izbegavati. Zatim napraviti sintezu.

## 5. Pravilo generalizacije
Model mora biti generalizovan — ukloniti/zameniti konkretne podatke starog predmeta zagradama: `[SUD]`, `[TUŽILAC]`, `[TUŽENI]`, `[BROJ PREDMETA]`, `[DATUM]`, `[IZNOS]`, `[NEPOKRETNOST]`, `[PRAVNI OSNOV]`, `[ČINJENICA]`, `[DOKAZ]`, itd. **Nikad ne ostavljati lične podatke iz starog predmeta u generalizovanom modelu** — OBAVEZNO pokrenuti `13-anonimizacija` PRE trajnog čuvanja generičkog modela (v. taj skill, odeljak ROUTING: "KONKRETAN PREDMET → GENERIČKI MODEL" — ANONYMIZATION prethodi ovom skillu, ne obrnuto).

## 6. Model ≠ automatski važeće pravo
I kad postoji stari dobar obrazac, pre upotrebe proveriti: da li je propis i dalje važeći; relevantnu verziju; da li su se procesna pravila promenila; da li je praksa promenjena; da li postoji novija odluka; da li se stari model oslanja na prevaziđen pravni stav. Stari dokument se ne sme nekritički reprodukovati.

## 7. Strukturni model — dva sloja
- **A. CORE** — elementi koji gotovo uvek pripadaju toj vrsti dokumenta.
- **B. OPTIONAL MODULES** — delovi koji se dodaju samo ako su uslovi ispunjeni, npr. `[OPTIONAL: PRIGOVOR ZASTARELOSTI]`, `[OPTIONAL: NENADLEŽNOST]`, `[OPTIONAL: SUPROTNA SUDSKA PRAKSA]`, `[OPTIONAL: ESLJP ARGUMENT]`, `[OPTIONAL: PREDLOG ZA VEŠTAČENJE]`.

## 8. Uslovna logika
Kad je korisno, u model uneti kratke instrukcije: `IF [uslov] → koristi modul X`; `IF NOT [uslov] → izostavi modul X` (npr. "Ako je rok za žalbu sporno pitanje → uključi odeljak o blagovremenosti").

## 9. Kontrola petituma
Kod procesnih dokumenata posebno proveriti: da li petitum odgovara vrsti postupka; da li se traži nešto o čemu sud/organ može odlučiti; da li sadrži nepotrebne činjenične kvalifikacije; da li je izvršiv i dovoljno određen. Ne preuzimati petitum iz starog predmeta bez provere.

## 10. Provenance — MODEL_SOURCE_NOTE
Za svaki model napraviti internu belešku: koji postojeći modeli su korišćeni; koji predmeti; koji propisi; koje presude; koji `ISSUE_RECORD`; šta je preuzeto kao strukturni princip; šta je novo sintetizovano. Ova beleška NIJE deo dokumenta koji se podnosi sudu — v. odeljak 13 ispod za format.

## 11. DEVILS_ADVOCATE provera
Za složene procesne/materijalnopravne modele, pre finalizacije primeniti `18-devils-advocate`: da li nedostaje obavezan element; procesna opasnost; zastareo pravni osnov; problematičan petitum; preterano kategorična tvrdnja; da li je citirana sudska praksa stvarno primenljiva. Posle provere ispraviti model.

## 12. Tipovi modela
Svaki model označiti kao: **BASE_MODEL** (osnovni univerzalni), **SPECIALIZED_MODEL** (za konkretnu podvrstu situacije), **MODULE** (samostalan deo dodaje se drugim modelima), **CLAUSE** (pojedinačna pravna formulacija), **CHECKLIST**.

## 13. Skladištenje
Kad korisnik traži da se model sačuva kao trajan resurs: `04_OBRASCI/GENERISANI_MODELI/`, podeljeno po pravnoj oblasti i vrsti dokumenta (npr. `PARNICNO/TUZBE/`, `PARNICNO/ZALBE/`, `UPRAVNO/`, `IZVRSENJE/`, `UGOVORI/`). Ne čuvati svaki ad hoc draft kao trajan model — samo kad je korisnik to izričito zatražio ili kad je model stvarno generalizovan/proveren.

MODEL_SOURCE_NOTE (v. tačka 10) čuvati kao poseban prateći fajl uz model (npr. `<MODEL>.SOURCE-NOTE.md`), ne mešati sa samim tekstom akta.

## 14. Verzionisanje
Za trajne modele čuvati: datum kreiranja; datum poslednje revizije; pravni režim; relevantne propise; status provere. Oznake: **DRAFT** / **VERIFIED** / **NEEDS_REVIEW** / **OBSOLETE**.

## 15. Poboljšanje modela
Kad se u novom predmetu pojavi bolje rešenje — NE menjati automatski postojeći VERIFIED model. Prvo uporediti novo rešenje sa postojećim. Ako je poboljšanje stvarno: predložiti izmenu, napraviti novu verziju, zabeležiti šta je promenjeno i zašto (isti princip kao `14-usavrsavanje-obrazaca`, tačka "Šta ovaj skill NE sme da radi" — dodaje se, retko briše).

## 16. Komande korisnika
- "Napravi model..." → samostalno: identifikuj vrstu → pretraži resurse → izdvoji najbolje relevantne primere → proveri važeće pravo → sintetizuj → generalizuj → quality control → prikaži model.
- "Napravi model na osnovu naših predmeta" → veća težina proverenim dokumentima iz `01_PREDMETI/`, ali proveriti prema aktuelnim izvorima.
- "Napravi najbolji model koji imamo" → NE birati jedan dokument — sintetizovati najbolje elemente iz više izvora.
- "Sačuvaj kao model" → smestiti proverenu verziju u `04_OBRASCI/GENERISANI_MODELI/`.

## SOURCE-GROUNDED MODEL DRAFTING (obavezna dubinska provera pre finalizacije)
Model mora biti rezultat: **POSTOJEĆI AKTI + VAŽEĆI PROPISI + SUDSKA PRAKSA + LITERATURA + KNOWLEDGE LAYER + KONKRETNA PRAVNA METODOLOGIJA** — ne osloniti se samo na postojeće obrasce i ranije akte.

### Hijerarhija izvora
Ne davati svim izvorima istu težinu: **VAŽEĆE PRAVO ≠ SUDSKA PRAKSA ≠ PRAVNI STAVOVI/TUMAČENJA ≠ LITERATURA ≠ RANIJA KANCELARIJSKA PRAKSA.** Stari podnesak nije dokaz da je pravni stav tačan. Literatura nije pozitivno pravo. Sudska odluka se ne sme koristiti van granica svog ratio decidendi.

### Propisi
Pre upotrebe zakonske odredbe proveriti: da li je propis važeći; relevantnu verziju; vremensku primenu; prelazne/završne odredbe ako su bitne; lex specialis; povezane procesne odredbe; odluke Ustavnog suda koje mogu uticati na normu. Ne preuzimati član zakona iz starog podneska bez provere.

### Sudska praksa
Ne dodavati presude dekorativno. Za svaku odluku koja nosi značajan argument proveriti LEGAL ISSUE, DECISIVE FACTS, RATIO DECIDENDI, SCOPE, DISTINGUISHING FACTORS i njen odnos sa konkretnim argumentom modela — po potrebi aktivirati `17-case-law-analyzer` i `15-poredjenje-sudske-prakse`. Aktivno proveriti da li postoji suprotna ili novija praksa.

### Literatura
Koristiti za identifikovanje pravnih problema, sistematizaciju instituta, tumačenje normi, otkrivanje relevantne prakse, argumentaciju, kritičko preispitivanje. Ali: **SCHOLARLY POSITION ≠ POSITIVE LAW**, i **AUTOROVO TUMAČENJE PRESUDE ≠ SAMA PRESUDA** — kad literatura upućuje na važnu presudu, po mogućnosti proveriti originalnu odluku.

### Model Argument Map (interna, pre finalizacije složenog modela)
`TVRDNJA → PRAVNI OSNOV → IZVOR → PRIMENJIVOST`, npr.:
```
Tvrdnja A → član X Zakona → važeći tekst propisa → DIRECT
Tvrdnja B → Rev XXXX/20XX → ratio + decisive facts → STRONGLY ANALOGOUS
Tvrdnja C → autor X, str. Y → doktrinarna podrška → PERSUASIVE ONLY
```

### Source gap
Ako za važnu tvrdnju ne postoji dovoljno pouzdan izvor, ne predstavljati je kao nespornu — označiti interno **SOURCE GAP** i pokušati dodatno istraživanje; ako ni posle toga nema podrške, formulisati tvrdnju sa odgovarajućim stepenom opreza.

### Contrary authority check
Pre finalizacije značajnog modela obavezno postaviti pitanje: **ŠTA JE NAJJAČI IZVOR PROTIV OVOG MODELA ILI NJEGOVE CENTRALNE TEZE?** Ako postoji suprotna/novija praksa, drugačiji pravni stav, problem u literaturi, izmena propisa — model se MORA prilagoditi.

### SOURCE_NOTE.md
Uz svaki složen model — korišćeni propisi, sudske odluke, literatura, ISSUE zapisi, raniji predmeti, raniji modeli, datum provere izvora, eventualni suprotni izvori, nerešena pitanja. Nije deo akta koji se podnosi sudu/organu (v. tačka 10 iznad — isti koncept kao MODEL_SOURCE_NOTE).

## Osnovno pravilo
Nikad: **NAĐI SLIČAN STARI AKT → PREPIŠI → PROMENI IMENA.**

Uvek: **IDENTIFIKUJ PRAVNI PROBLEM → PRONAĐI NAJBOLJE POSTOJEĆE AKTE → PROVERI VAŽEĆE PRAVO → PROVERI SUDSKU PRAKSU → PROVERI LITERATURU → UPOREDI IZVORE → PROVERI SUPROTNE IZVORE → SINTETIZUJ → DEVILS_ADVOCATE → FINALNI MODEL.**

Cilj nije najsličniji stari dokument — cilj je najbolji pravno održiv model koji se može napraviti iz svih raspoloživih izvora.

## Odnos prema postojećim skill-ovima
- `07-izrada-akta` ostaje za izradu KONKRETNOG akta za KONKRETAN predmet (v. `19-legal-research-orchestrator`, TYPE F). Ovaj skill (21) je za GENERIČKI, ponovo upotrebljiv MODEL.
- `14-usavrsavanje-obrazaca` prepoznaje KADA vredi napraviti nov generički obrazac iz stvarno uvezenog dokumenta (automatski, pri uvozu) — kad prepozna takvu priliku, IZRADA modela ide kroz OVAJ skill (21), po punom workflow-u, ne ad hoc.
- Generički modeli, USAVRŠENI iz stvarne prakse konkretnih predmeta, i dalje idu u `04_OBRASCI/USAVRSENI-MODELI/` (pravilo od 30.8.2026, v. `14-usavrsavanje-obrazaca`). `04_OBRASCI/GENERISANI_MODELI/` (ovaj skill, tačka 13) je za modele nastale OVIM punim, višeizvornim workflow-om na EKSPLICITAN zahtev korisnika — razlika je u tome KAKO je model nastao (organski, iz jednog usavršavanja jednog predmeta, vs. namenski sintetizovan iz više izvora na zahtev), ne u kvalitetu. Kad se preklapaju, ne duplirati — uputiti na postojeći.
