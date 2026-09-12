---
name: sudska-praksa
description: Pronalaženje, verifikacija i uporedna analiza sudskih odluka.
---

# SUDSKA PRAKSA

## Zero hallucination
Ne izmišljaj sud, broj, datum, citat ili pravno shvatanje.

Status odluke:
- VERIFIED
- PARTIALLY VERIFIED
- UNVERIFIED

UNVERIFIED se ne koristi kao autoritet u finalnom aktu.

## CASE CARD
- Sud:
- Broj:
- Datum:
- Pravno pitanje:
- Relevantne činjenice:
- Pravno shvatanje:
- Ratio:
- Sličnosti:
- Razlike:
- Upotreba: SUPPORT / DISTINGUISH / BACKGROUND
- Status:
- Izvor:

Obavezno traži i odluke koje mogu biti nepovoljne.

Za PUNU komparativnu analizu primenljivosti (ratio decidendi, odlučne činjenice, distinguishing, klasifikacija A-E) — ne samo osnovni CASE CARD — v. `15-poredjenje-sudske-prakse`. Za trajan, unakrsno-povezan zapis (JUDGMENT_RECORD) kad se očekuje česta ponovna upotreba odluke — v. `20-legal-knowledge-record-standard`.

## Obavezna provera: baza Vrhovnog suda (Građanska materija)

Kad se analizira TUŽBA, PRESUDA, ŽALBA ili bilo koji drugi akt u PARNIČNOM POSTUPKU, uvek proveriti relevantnu praksu kroz pretragu Vrhovnog suda po ovom obrascu (parametar `matter=19` = Građanska materija, verifikovano 29.8.2026):

```
https://www.vrh.sud.rs/sr/solr-search-page/results?court_type=sc&matter=19&registrant=_none&subject_number=&date_from%5Bdate%5D=&date_to%5Bdate%5D=&keywords=<KLJUČNA_REČ>&phrase=&sorting=by_date_down&results=10&level=1
```

- Popuniti `keywords=` (ili `subject_number=` za tačan broj predmeta) konkretnim pravnim institutom/pojmom iz predmeta koji se analizira (npr. "измакла корист", "солидарна обавеза", "застарелост") — NIKAD pretraživati bez filtera (bez filtera vraća >12.000 rezultata, neupotrebljivo).
- Baza pokriva SAMO Vrhovni sud (`court_type=sc`); za niže instance koristiti druge dostupne izvore (Bilteni u `05_IZVORI/SUDSKA-PRAKSA/BILTENI/`, itd.).
- Svaku pronađenu, stvarno korišćenu odluku obavezno svesti na CASE CARD (format iznad) i status VERIFIED/UNVERIFIED — sama pretraga nije dovoljna, mora se otvoriti i pročitati odluka.
- Ovo je STANDING metod provere (ne jednokratan uvoz) — baza se ne preuzima lokalno u celini (12.446+ odluka, raste svakodnevno), već se pretražuje uživo, ciljano, za svaki predmet posebno.
