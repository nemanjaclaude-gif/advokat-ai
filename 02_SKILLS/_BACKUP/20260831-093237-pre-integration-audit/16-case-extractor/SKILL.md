---
name: case-extractor
description: CASE_EXTRACTOR — pretvara kompletan sudski/upravni predmet (svi dokumenti — tužba, odgovori, podnesci, dokazi, odluke) u preciznu, proverljivu, strukturisanu mapu predmeta, PRE nego što se donese ijedan pravni zaključak. Razdvaja tvrdnje stranaka od utvrđenih činjenica, spornih činjenica, dokaza, pravnih argumenata i sudskih odluka — navod stranke nije isto što i dokazana činjenica. Dublja, potpunija verzija onoga što `01-analiza-predmeta` i `03-analiza-dokaza` rade u skraćenom obliku — koristiti OVAJ skill kad predmet ima mnogo dokumenata i slojeva (više ročišta, više instanci, kontradiktorni navodi), a skill 01/03 kad je predmet jednostavan i ne treba puna mapa.
---

# CASE_EXTRACTOR

Osnovno pravilo: **navod stranke nije isto što i dokazana činjenica.** Ne donositi pravni zaključak pre nego što se razdvoje: tvrdnje stranaka, utvrđene činjenice, sporne činjenice, dokazi, pravni argumenti, odluke suda/organa.

## 1. Identifikacija predmeta
Utvrditi: sud/organ; broj predmeta; vrstu postupka; stranke; punomoćnike; predmet spora; vrednost spora; fazu postupka. Ako podatak nije dostupan — označiti kao **nepoznato**, ne pretpostavljati.

## 2. Hronologija
Hronologija SVIH pravno relevantnih događaja, format: **datum | događaj | izvor | pravni značaj**. Razlikovati: događaje PRE postupka; pokretanje postupka; procesne radnje; izvođenje dokaza; odluke; pravne lekove.

## 3. Zahtevi stranaka
Precizno izdvojiti: glavni zahtev; eventualni zahtev; protivtužbeni zahtev; sporedna potraživanja; kamatu; troškove. Ne parafrazirati petitum ako je njegova tačna formulacija pravno značajna — prepisati doslovno.

## 4. Činjenične tvrdnje
Za svaku stranku posebno, struktura: **tvrdnja → dokaz → protivargument → dokaz protivne strane → status**.

Status (ZAMENJUJE/precizira skraćenu listu iz skill 01 — CONFIRMED/INFERRED/ALLEGED/DISPUTED/UNKNOWN — kad se radi puna mapa):
- nesporno
- sporno
- priznato
- dokazano
- nedokazano
- sud još nije ocenio
- nije moguće utvrditi

Nikad samostalno ne proglašavati činjenicu dokazanom samo zato što je navedena u podnesku.

## 5. Dokazna mapa
Za svaki dokaz utvrditi: ko ga je predložio; šta njime dokazuje; da li je izveden; šta dokaz NEPOSREDNO pokazuje (ne više od toga); ograničenja dokaza; da li mu protivreči drugi dokaz; kako ga je sud ocenio (ako postoji odluka).

Posebno identifikovati situacije u kojima stranka tvrdi VIŠE nego što dokaz stvarno pokazuje — ovo je čest izvor slabosti u sopstvenoj argumentaciji, važno ga uočiti pre protivnika.

## 6. Pravni argumenti
Za svaku stranku: **pravna teza → pravni osnov → činjenice na kojima teza počiva → izvor prava/prakse → protivargument**. Ne mešati činjenične i pravne argumente.

## 7. Odluke suda/organa
Za svaku odluku utvrditi: šta je odlučeno; šta je prihvaćeno; šta je odbijeno; koje činjenice je sud utvrdio; koje dokaze je prihvatio; koje dokaze nije prihvatio; koje pravno pravilo je primenio; ratio decidendi (v. `17-case-law-analyzer` za dublju analizu ako je odluka sama po sebi važan presedan); da li je odluka pravnosnažna; da li je ukinuta ili preinačena — AKO JESTE, to mora biti jasno označeno, ne prećutano.

## 8. Protivrečnosti u spisima
Aktivno tražiti: različite datume istog događaja; različite iznose; različite površine; različite opise iste nepokretnosti; promene iskaza; neslaganje podneska i dokaza; neslaganje nalaza veštaka i dokumentacije; neslaganje prvostepene i drugostepene odluke.

Ne pokušavati SAM da "pomiri" protivrečne podatke — označiti: **CONFLICT — potrebna provera.**

## 9. Nedostajući materijal
Utvrditi šta nedostaje za pouzdanu analizu (npr. ugovor, aneks, nalaz veštaka, list nepokretnosti, dostavnica, žalba, drugostepena odluka, dokaz na koji se stranka poziva). Ne pretpostavljati sadržinu dokumenta koji nije dostupan.

## 10. Završni CASE MAP
- **A. Predmet** — identifikacija
- **B. Hronologija**
- **V. Zahtev**
- **G. Nesporne činjenice**
- **D. Sporne činjenice**
- **Đ. Dokazna mapa**
- **E. Argumentacija tužioca/predlagača**
- **Ž. Argumentacija tuženog/protivnika**
- **Z. Dosadašnji stav suda**
- **I. Ključna pravna pitanja**
- **J. Protivrečnosti**
- **K. Nedostajući materijal**
- **L. Pitanja koja zahtevaju dalju pravnu analizu**

## Osnovno pravilo pouzdanosti
Za svaku značajnu tvrdnju mora biti moguće odgovoriti: *"Iz kog dokumenta ovo proizlazi?"* Ako to nije moguće, ne predstavljati tvrdnju kao utvrđenu činjenicu.

## Gde ide rezultat / odnos prema drugim skill-ovima
- Ovo JE, u proširenom obliku, ono što `01-analiza-predmeta` (CASE INTAKE/DOCUMENT INDEX/CHRONOLOGY/FACT MATRIX/...) i `03-analiza-dokaza` rade skraćeno — kad se koristi ovaj skill za kompleksan predmet, njegov izlaz zamenjuje/nadograđuje output tih skill-ova, ne radi se duplo.
- Rezultat (CASE MAP) ide u `01_RADNI_MATERIJALI/` konkretnog predmeta (npr. kao `CASE-MAP.md`, ili integrisano u postojeće `HRONOLOGIJA.md`/`EVIDENCE-MATRIX.md` po ustaljenoj konvenciji — v. primer `2026-009-ARAMBASIC-ZIVOJIN/01_RADNI_MATERIJALI/`).
- Kad CASE MAP identifikuje sudsku odluku koja je sama po sebi vredan presedan (ne samo deo hronologije OVOG predmeta), tu odluku obraditi zasebno kroz `17-case-law-analyzer`, i po potrebi upoređivati kroz `15-poredjenje-sudske-prakse`.
