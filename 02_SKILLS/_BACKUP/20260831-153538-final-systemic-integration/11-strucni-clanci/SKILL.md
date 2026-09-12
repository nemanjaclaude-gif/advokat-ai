---
name: strucni-clanci
description: Proverava i potkrepljuje pravno istraživanje i pravnu analizu kroz stručne/naučne članke iz tri određena pravna časopisa u 05_IZVORI/CASOPISI (Pravo i privreda; Zbornik radova Pravnog fakulteta u Novom Sadu; Zbornik radova Pravnog fakulteta u Nišu). Poprečni (cross-cutting) skill — ne predstavlja poseban korak u WORKFLOW redosledu, već se primenjuje UNUTAR skillova 04-pravno-istrazivanje i 06-pravna-analiza, svaki put kad se oni pokreću — uz skill 10-teorijska-analiza, ne umesto njega.
---

# STRUČNI ČLANCI

## Kada se koristi
**Uvek** kada se radi `04-pravno-istrazivanje` ili `06-pravna-analiza` — kao dodatni, četvrti sloj potkrepljenja uz zakon, sudsku praksu i doktorske disertacije (skill `10-teorijska-analiza`). Ide UZ skill 10, ne umesto njega — oba se pokreću zajedno.

## Razlika prema skillu 10-teorijska-analiza
- Skill 10 pokriva `05_IZVORI/LITERATURA` (doktorske disertacije).
- Skill 11 (ovaj) pokriva `05_IZVORI/CASOPISI` (članci iz tri konkretna pravna časopisa: Pravo i privreda ISSN 0354-3501; Zbornik radova Pravnog fakulteta, Novi Sad ISSN 0550-2179; Zbornik radova Pravnog fakulteta u Nišu ISSN 0350-8501).
- Isto pravilo (zero-hallucination, DIREKTNA vs ANALOŠKA relevantnost, obavezno navesti kad nema pogotka) važi za oba.

## Zadatak
1. Pregledati katalog u `05_IZVORI/CASOPISI/README.md` i identifikovati članke čija je tema relevantna za pravno pitanje koje se analizira (po ključnim rečima/institutu, ne samo po nazivu časopisa/oblasti).
2. Za svaki identifikovan članak, pretražiti pun tekst (ako je dostupan u folderu) na konkretne pojmove i članove zakona koji su predmet analize.
3. Razlikovati DIREKTNU relevantnost (članak domaćeg prava koji tumači baš tu odredbu/institut) od ANALOŠKE/uporednopravne relevantnosti — uvek jasno označiti koja je u pitanju.
4. Citirati samo ono što je EKSPLICITNO napisano u članku, po mogućstvu uz naznaku strane/pasusa — ne pripisivati autoru stav koji nije jasno izražen.
5. Proveriti da li članak OSPORAVA (ne samo potvrđuje) liniju analize — ako da, to obavezno uneti.
6. Ako katalog `05_IZVORI/CASOPISI/README.md` još nema unetih članaka (prazan), ili nijedan uneti članak nije relevantan za dato pitanje, to eksplicitno napisati ("Nije pronađen relevantan članak u dostupnom katalogu časopisa — katalog trenutno prazan/ne sadrži rad na ovu temu") — ne izostaviti odeljak ćutke.
7. **Ne pretraživati sam SCIndeks uživo za svaki predmet.** Katalog se popunjava samo kad advokat ručno doda članak (v. napomenu u `05_IZVORI/CASOPISI/README.md` o robots.txt i Cloudflare ograničenju) ili kad je za KONKRETAN, imenovan članak izvršena pojedinačna, ciljana provera (npr. WebSearch da se potvrdi da citat postoji) — nikad masovno prikupljanje uživo tokom analize predmeta.
8. Uneti nalaz u zaseban odeljak pravne analize po formatu ispod — ako i skill 10 daje nalaz, oba nalaza mogu ići u isti odeljak `## TEORIJSKA POTKREPLJENOST (LITERATURA)`, jasno razdvojena po izvoru (disertacija vs. časopis), ili u zaseban pododeljak "Stručni članci" ako je preglednije.

## Pravilo (zero hallucination za članke)
- Ne izmišljati autora, naslov, godinu, broj sveske ili stav.
- Članak NIJE izvor prava niti obavezujući autoritet — koristi se da POTKREPI ili DOVEDE U PITANJE zaključak već izveden iz zakona i prakse.
- Sekundarne izvore/praksu koje članak citira tretirati kao NEVERIFIKOVANE dok se ne pribave i pročitaju nezavisno.
- Kad korisnik ubaci nove članke u `05_IZVORI/CASOPISI/`, ažurirati katalog u `README.md` tog foldera.

## Output format
Isti format kao u skillu `10-teorijska-analiza`, sa naznakom izvora (časopis, broj, godina) umesto (fakultet, godina disertacije):
- Autor, naslov, časopis, broj/godina (iz kataloga).
- Nalaz — verno prenet stav iz članka, sa naznakom strane/pasusa gde je moguće.
- Ocena: **POTVRĐUJE** / **OSPORAVA** / **ANALOŠKI RELEVANTNO** / **NIJE PRONAĐENO**.
- Napomena o dometu.

## Baza
`05_IZVORI/CASOPISI/` — katalog u `README.md` tog foldera. Trenutno prazan; popunjava se ručnim uvozom (v. napomenu tamo o tehničkim i pravnim razlozima zašto nije automatizovano preuzeto).
