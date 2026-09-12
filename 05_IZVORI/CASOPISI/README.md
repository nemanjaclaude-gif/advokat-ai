# ČASOPISI — stručni/naučni pravni članci

Poseban izvor, odvojen od `05_IZVORI/LITERATURA` (doktorske disertacije). Ovde se čuvaju članci iz tri određena pravna časopisa, kao dodatni sloj provere uz propise, sudsku praksu i disertacije.

## Obuhvaćeni časopisi

| Časopis | ISSN | Izdavač/fakultet | SCIndeks |
|---|---|---|---|
| Pravo i privreda | 0354-3501 | Udruženje pravnika u privredi Srbije | https://scindeks.ceon.rs/JournalDetails.aspx?issn=0354-3501 (arhiva punog teksta: https://pravoiprivreda.rs/arhiva-idx/ — v. dopunu ispod) |
| Zbornik radova Pravnog fakulteta, Novi Sad | 0550-2179 | Pravni fakultet Univerziteta u Novom Sadu | https://scindeks.ceon.rs/JournalDetails.aspx?issn=0550-2179 |
| Zbornik radova Pravnog fakulteta u Nišu | 0350-8501 | Pravni fakultet Univerziteta u Nišu | https://scindeks.ceon.rs/JournalDetails.aspx?issn=0350-8501 |

## Dopuna (29.8.2026) — lokalne sveske uvezene od korisnika

Iz `/Users/nemanjazaric/Desktop/Pravni/` uvezene su CELE SVESKE (ne pojedinačni članci) za dva od tri gore navedena časopisa — korisnik je imao lokalni pristup, pa ograničenje robots.txt/Cloudflare (v. ispod) ovde nije bilo relevantno:
- `ZBORNIK-NIS/` — Zbornik radova Pravnog fakulteta u Nišu, sveske XLIII-LXIII (period ~2003-2012), 21 fajl.
- `ZBORNIK-NOVI-SAD/` — Zbornik radova Pravnog fakulteta, Novi Sad, sveske 2-3/2010-2014, 15 fajlova.

Ovo su cele sveske (po više članaka u svakom PDF-u), ne pojedinačno katalogizovani članci — kad se konkretan članak iz neke sveske stvarno koristi u analizi, navesti ga u tabeli "Katalog" ispod sa punim bibliografskim podatkom (autor, naslov, strana).

## Dopuna (4-5.9.2026) — "Pravo i privreda" preuzeto direktno sa sopstvenog sajta časopisa

Napomena od 29.8.2026 (ispod) o tehničkoj nedostupnosti odnosila se ISKLJUČIVO na SCIndeks (scindeks.ceon.rs). Otkriveno je da časopis ima i SOPSTVENI sajt, `https://pravoiprivreda.rs/`, koji NIJE iza Cloudflare provere i čiji `robots.txt` zabranjuje samo `/wp-admin/` (dozvoljava arhivu). Sadržaj je open access (CC BY 4.0), PDF linkovi dostupni direktno u HTML-u stranice.

Preuzeta je CELA dostupna arhiva sajta: **volumeni 39-64 (godine 2001-2026)** — sajt ne sadrži digitalizovane brojeve pre 2001, iako je časopis osnovan 1993 (nastavak još starijeg izdanja iz 1963). Ukupno **2133 kataloških jedinica, 2129 uspešno preuzetih PDF fajlova** (4 pojedinačna preuzimanja nisu uspela nakon ponovljenih pokušaja — v. `PRAVO-I-PRIVREDA/INDEKS.md`, odeljak "Neuspešna preuzimanja").

- Fajlovi: `PRAVO-I-PRIVREDA/<godina>/`, imenovani po konvenciji ispod.
- Pun mašinski generisan indeks (autor, naslov, sveska, fajl) za SVE preuzete članke: `PRAVO-I-PRIVREDA/INDEKS.md`. Ovo je poseban fajl od tabele "Katalog" ispod — INDEKS je puna bibliografija za pretragu, "Katalog" ostaje rezervisan za članke stvarno citirane u nekoj analizi.
- Stariji brojevi (2001-2019) objavljivani su u spojenim sveskama (npr. "5-8/2003", ne pojedinačno kvartalno) i pojedini brojevi sadrže i po 80-90 članaka odjednom — to su najčešće celi zbornici sa godišnjih "Susreta pravnika u privredi", ne uobičajeni kvartalni broj; ovo je normalno, ne greška uvoza.
- Uvoz je urađen skriptovano (Python + curl-style HTTP zahtevi uz poštovanje robots.txt), ne kroz WebFetch po članku — brže i bez nepotrebnog opterećenja modela za čisto mehaničko izvlačenje linkova.

## Napomena o uvozu (29.8.2026) — i dalje važi za SCIndeks i za druga dva časopisa

Puni tekst sa SCIndeks-a NIJE preuzet automatizovanim putem. Dva razloga:
1. `robots.txt` sajta SCIndeks (scindeks.ceon.rs) izričito zabranjuje automatizovan pristup celom sajtu (`Disallow: /` za sve korisničke agente osim Googlebot-a) — ne zaobilazi se.
2. Nezavisno od toga, stranice pojedinačnih članaka (`Article.aspx`, gde se nalazi PDF) zaštićene su Cloudflare JS proverom koju dostupni alati (curl, WebFetch) ne mogu rešiti — tehnički nedostupno bez alata za automatizaciju pravog pretraživača, koji nije na raspolaganju.

**Katalog izdanja (broj sveske, godina) JESTE dostupan** preko `JournalDetails.aspx` i `Issue.aspx` stranica (nisu iza Cloudflare provere) — ali se, poštujući robots.txt, ni ovaj katalog ne prikuplja automatizovano u većem obimu. Ovo i dalje važi za "Zbornik radova Pravnog fakulteta, Novi Sad" i "Zbornik radova Pravnog fakulteta u Nišu" — za njih SCIndeks ostaje jedini poznati elektronski izvor pojedinačnih članaka (v. lokalne sveske dopunu iznad za ono što je već pribavljeno ručno).

**Način uvoza za preostala dva časopisa: i dalje ručno, od strane advokata.** Korisnik preuzima PDF članke (npr. preko sopstvenog univerzitetskog/bibliotečkog pristupa) i stavlja ih u ovaj folder; ja ih zatim katalogizujem i uključujem u analizu, isto kao što je urađeno sa `05_IZVORI/LITERATURA`.

## Konvencija imenovanja fajlova

`Prezime-Ime_Kratak-naslov-clanka_Casopis-Godina.pdf`

Primer: `Djurdjevic-Marko_Ugovor-o-poklonu-forma_PravoIPrivreda-2015.pdf`

Ako originalni naziv fajla (npr. sa SCIndeks-a, tip `0354-35011303007P.pdf`) ne nosi identifikacionu vrednost, preimenovati pri uvozu — original se ne menja sadržinski, samo se preimenuje (v. pravilo iz `00_UPUTSTVO/NAMING-CONVENTION.md`).

## Katalog

_Prazno — popuniti kad prvi članci budu uneti._

| Autor | Naslov | Časopis | Godina | Relevantno za |
|---|---|---|---|---|

## Pravilo
Isto pravilo kao za `LITERATURA`: članak NIJE izvor prava niti obavezujući autoritet — koristi se za proveru i potkrepljenje argumentacije. Ne pripisivati autoru stav koji nije eksplicitno izražen. Ne pretpostavljati.
