---
name: teorijska-analiza
description: Proverava i potkrepljuje pravno istraživanje i pravnu analizu kroz doktorske disertacije i druge doktrinarne radove iz 05_IZVORI/LITERATURA. Poprečni (cross-cutting) skill — ne predstavlja poseban korak u WORKFLOW redosledu, već se primenjuje UNUTAR skillova 04-pravno-istrazivanje i 06-pravna-analiza, svaki put kad se oni pokreću.
---

# TEORIJSKA ANALIZA

## Kada se koristi
**Uvek** kada se radi `04-pravno-istrazivanje` ili `06-pravna-analiza` — kao treći, dopunski sloj potkrepljenja uz zakon i sudsku praksu. Nije zamena ni za jedno od to dvoje, već dodatna provera.

## Zadatak
1. Pre ili tokom pravne analize, pregledati katalog u `05_IZVORI/LITERATURA/README.md` i identifikovati radove čija je tema relevantna za pravno pitanje koje se analizira (po ključnim rečima/institutu, ne samo po nazivu oblasti).
2. Za svaki identifikovan rad, pretražiti PUN TEKST (ne samo naslovnu stranu/apstrakt) na konkretne pojmove i članove zakona koji su predmet analize.
3. Razlikovati DIREKTNU relevantnost (rad domaćeg prava koji tumači baš tu odredbu/institut) od ANALOŠKE/uporednopravne relevantnosti (rad o stranom, međunarodnom ili srodnom, ne identičnom institutu) — uvek jasno označiti koja je u pitanju, nikad predstaviti analošku podršku kao direktnu.
4. Citirati samo ono što je EKSPLICITNO napisano u radu, po mogućstvu uz naznaku strane/pasusa — ne pripisivati autoru stav koji nije jasno izražen.
5. Proveriti da li rad možda OSPORAVA (ne samo potvrđuje) liniju analize — ako da, to obavezno uneti, ne prećutkivati.
6. Uneti nalaz u zaseban odeljak pravne analize po formatu ispod.
7. Ako se u katalogu ne nalazi nijedan relevantan rad za dato pravno pitanje, to eksplicitno napisati ("Nije pronađen relevantan rad u dostupnoj literaturi") — ne izostaviti odeljak ćutke i ne pretpostaviti da doktrina ćuti ili da se slaže.

## Pravilo (zero hallucination za literaturu)
- Ne izmišljati autora, naslov, godinu ili stav.
- Doktrina NIJE izvor prava (za razliku od zakona) niti obavezujući autoritet (za razliku, delimično, od više sudske instance) — koristi se da POTKREPI ili DOVEDE U PITANJE zaključak već izveden iz zakona i prakse, nikad kao samostalan, dovoljan osnov za pravni zaključak.
- Sekundarne izvore/praksu KOJE rad citira (npr. sudsku odluku pomenutu u disertaciji) tretirati kao NEVERIFIKOVANE dok se ne pribave i pročitaju nezavisno — jasno to naznačiti.
- Kad se katalog literature vremenom proširi novim radovima, ažurirati `05_IZVORI/LITERATURA/README.md`.

## Output format (poseban odeljak unutar pravne analize)
`## TEORIJSKA POTKREPLJENOST (LITERATURA)`

Za svaki pretraženi/relevantan rad:
- Autor, naslov, fakultet, godina (iz kataloga).
- Nalaz — verno prenet stav iz rada, sa naznakom strane/pasusa gde je moguće.
- Ocena: **POTVRĐUJE** / **OSPORAVA** / **ANALOŠKI RELEVANTNO** / **NIJE PRONAĐENO**.
- Napomena o dometu (direktna vs. uporednopravna relevantnost; da li rad citira dalje, neverifikovane izvore).

Zaključni pasus: da li teorijska potkrepljenost, sagledana zajedno sa zakonom i sudskom praksom, JAČA ili SLABI prethodni zaključak analize — i za koliko (npr. "dodatni, nezavisan sloj potvrde" nasuprot "usamljen, sporedan nalaz bez težine naspram jasnog teksta zakona").

## Baza
`05_IZVORI/LITERATURA/` — katalog radova u `README.md` tog foldera, sa oznakom relevantnosti po oblasti. Radovi su doktorske disertacije pravnih fakulteta (Beograd, Novi Sad, Niš i dr.); po potrebi dopuniti katalog novim radovima (monografije, članci) kad postanu dostupni.

## Dodatni živi izvor: NaRDuS (od 30.8.2026)

**NaRDuS** (Nacionalni repozitorijum disertacija u Srbiji, `nardus.mpn.gov.rs`) — nacionalni DSpace repozitorijum doktorskih disertacija sa svih univerziteta u Srbiji, u nadležnosti Ministarstva prosvete, nauke i tehnološkog razvoja. Tretira se kao **ŽIVI izvor** (pretražuje se ciljano, po potrebi), isto kao baza Vrhovnog suda (skill `05-sudska-praksa`) i CASOPISI (skill `11-strucni-clanci`) — ne uvozi se u celini unapred.

- `robots.txt` sajta zabranjuje botovima stranice `/discover` i `/search-filter` (ugrađenu pretragu) — zato se pretraga NE vrši direktno na sajtu, već preko `WebSearch` (npr. `site:nardus.mpn.gov.rs <pojam>` ili ime autora/naslov), a zatim se pojedinačna stranica rada (`/handle/...`) otvara i čita direktno (te stranice nisu na listi zabrana).
- Kad se pronađe relevantna disertacija, primeniti isti postupak kao za `05_IZVORI/LITERATURA`: pretražiti pun tekst na konkretan pojam/institut, citirati samo eksplicitno napisano, oceniti DIREKTNA/ANALOŠKI RELEVANTNO/OSPORAVA/NIJE PRONAĐENO.
- Ako se rad sa NaRDuS-a stvarno iskoristi u analizi i korisnik potvrdi da vredi trajno sačuvati, preuzeti PDF i dodati ga u `05_IZVORI/LITERATURA/` (novi ili postojeći autorski potfolder) uz unos u katalog — isto kao ostali radovi. Do tada, tretirati nalaz kao rezultat pretrage uživo, ne kao već uvezen izvor.
