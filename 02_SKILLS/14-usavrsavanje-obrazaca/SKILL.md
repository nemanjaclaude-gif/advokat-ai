---
name: usavrsavanje-obrazaca
description: Automatski, pri svakom uvozu novog dokumenta u 01_PREDMETI, upoređuje novopristigli dokument sa postojećim obrascima u 04_OBRASCI/ (ako pripada istoj vrsti akta) i ažurira/usavršava obrazac kad novi dokument otkrije precizniju formulaciju, stvarnu praksu suda/organa, ili grešku u postojećem obrascu. Poprečni (cross-cutting) skill — ne predstavlja poseban korak u WORKFLOW redosledu, primenjuje se AUTOMATSKI pri svakom uvozu dokumenta, isto kao skill 13-anonimizacija.
---

# USAVRŠAVANJE OBRAZACA

## Svrha
Obrasci u `04_OBRASCI/` treba da s vremenom postaju SVE TAČNIJI i SVE BLIŽI stvarnoj praksi sudova/organa — ne da ostanu zamrznuti na nivou znanja u trenutku kad su prvi put napisani. Svaki novi stvaran dokument uvezen u sistem (podnesak koji je advokat stvarno sastavio i predao, ili odluka koju je sud/organ stvarno doneo) je prilika da se provere i, po potrebi, poboljšaju postojeći obrasci — isto onako kako je to već rađeno ad-hoc tokom rada na predmetima Milić-Zoran, Roković i Ignjatović (v. primer niže), samo sada kao stalan, automatski korak, ne nešto što se radi samo kad korisnik izričito zatraži.

## Kada se koristi
**Automatski, pri svakom uvozu novog dokumenta** u `01_PREDMETI/<predmet>/00_ULAZNI_DOKUMENTI/` (ili `02_OUTPUT/` kad se sačini nov nacrt akta) — bilo da se uvozi jedan fajl ili čitav predmet. Nije jednokratna radnja niti nešto što čeka da ga korisnik pokrene — proverava se pri SVAKOM unosu, isto kao anonimizacija (skill 13).

## Zadatak

1. **Identifikovati vrstu akta** novog dokumenta — kome je upućen (sud/organ), koja je vrsta podneska (zahtev, žalba, tužba, punomoćje, izveštaj, rešenje...), i koji pravni institut/postupak pokriva.

2. **Proveriti da li postoji odgovarajući obrazac** u `04_OBRASCI/` za tu vrstu akta (po nazivu fajla i po sadržini — obrazac ne mora imati identičan naziv da bi bio relevantan, npr. "ZAHTEV-ZA-UPIS-PRAVA-SVOJINE-NA-KATASTARSKOJ-PARCELI.md" je relevantan i za zahtev za promenu indikacija imaoca prava, ne samo za kupoprodaju).

3. **Ako obrazac postoji, UPOREDITI ga sa novim dokumentom** po sledećim tačkama:
   - Format zaglavlja (naziv/adresa organa, način navođenja podnosioca, broj primeraka/priloga).
   - Nivo detalja i tačna terminologija koju organ/sud stvarno očekuje (npr. JMBN broj, tačan naziv katastarske kulture/klase, format iznosa/razmera).
   - Pravni osnov (članovi zakona) koji je STVARNO korišćen i, ako je moguće, potvrđen kao ispravan (v. tačku 5 o razlikovanju izvora).
   - Elementi koje obrazac NEMA a novi dokument pokazuje da su uobičajeni/očekivani (npr. troškovnik, konkretna klauzula, prilog).
   - Elementi koje obrazac ima a novi dokument pokazuje da su suvišni, pogrešni ili zastareli.

4. **Ako se nađe razlika koja obrazac čini tačnijim ili potpunijim, AŽURIRATI obrazac** (Edit, ne prepravljanje iz osnova) — uz kratku, jasnu napomenu u samom obrascu odakle nalaz potiče (koji predmet, koji dokument, koji datum), po istom obrascu kao postojeće napomene tipa *"Stvarna praksa RGZ korišćena za ovaj obrazac: ... preuzeti su iz stvarnih podnesaka ... u predmetu ..."* (v. `04_OBRASCI/ZAHTEV-ZA-UPIS-PRAVA-SVOJINE-NA-KATASTARSKOJ-PARCELI.md` kao već postojeći primer ovog obrasca napomene). Ovo obezbeđuje sledljivost — svako ko kasnije koristi obrazac zna ZAŠTO je neki deo formulisan baš tako, ne samo teorijski nego na osnovu čega.

5. **Razlikovati DVA IZVORA nalaza — nikad ih ne mešati**:
   - **Stvarna praksa organa/suda** (format koji Služba/sud STVARNO zahteva ili prihvata — npr. kako RGZ opisuje katastarsku parcelu, koji podaci se traže) — ovo je pouzdan osnov za ažuriranje obrasca, jer odražava ono što organ stvarno očekuje, nezavisno od toga da li je advokat koji je pisao podnesak bio u pravu o pravnim pitanjima.
   - **Kvalitet argumentacije advokata koji je sastavio dokument** (pravna teza, citirani član zakona, strategija) — ovo NIJE automatski pouzdan osnov, jer i stvaran, predat dokument može sadržati grešku (v. primer niže — netačno citiranje ZUP čl. 5/10 umesto čl. 11 u tužbi Roković, ili netačan rok u žalbi Roković-02). Pre nego što se neka PRAVNA teza iz novog dokumenta unese u obrazac kao "ispravna", proveriti je nezavisno (kroz `04-pravno-istrazivanje`/`10-teorijska-analiza`), ne preneti je samo zato što je neko iskusan advokat tako napisao.

6. **Ako obrazac za tu vrstu akta NE POSTOJI**, ne kreirati ga automatski bez procene — proceniti da li je akt dovoljno generičkog, ponovljivog karaktera da bi budući obrazac imao vrednost (npr. zahtev RGZ-u, žalba na tipičan upravni propust) naspram jednokratnog, usko specifičnog podneska koji se teško uopštava. Ako procena govori DA, predložiti korisniku izradu novog obrasca (v. skill `07-izrada-akta`/postojeća praksa u `04_OBRASCI/`) — ne nužno odmah ga i napraviti bez potvrde, osim ako je već ranije uspostavljen obrazac ponašanja da se to radi automatski (kao kod obrasca za upis svojine na katastarskoj parceli, koji je nastao na direktan zahtev).

7. **Zabeležiti šta je urađeno** — ako je obrazac ažuriran, to pomenuti korisniku u odgovoru (kratko, ne praviti od toga poseban izveštaj osim ako korisnik pita) — isto onako kako je već rađeno pri uvozu Milić-Zoran/Roković dokumenata.

## Gde ide šta — obavezno razdvajanje generičkih modela od predmeta (pravilo od 30.8.2026, izričita odluka korisnika)

**Usavršeni, generički modeli NIKAD ne idu direktno u `01_PREDMETI/`.** Oni idu isključivo u poseban odeljak `04_OBRASCI/USAVRSENI-MODELI/` — odvojeno od običnih, prvobitnih obrazaca u korenu `04_OBRASCI/` (koji ostaju kao teorijski/generički prvi nacrti), da bi se jasno razlikovalo: (a) prvobitan, generički obrazac napisan iz teorije/zakona, od (b) obrazac koji je prošao kroz uporedbu sa stvarnim, uspešno sprovedenim predmetima i sadrži dodatnu, iz prakse potvrđenu argumentaciju (npr. verifikovanu sudsku praksu koja podupire pravni osnov).

**U `01_PREDMETI/<predmet>/02_OUTPUT/`, nacrt akta za taj konkretan predmet sadrži SAMO "izvorno"** — sam tekst akta, popunjen stvarnim imenima/brojevima/činjenicama tog predmeta, spreman za pregled advokata. NE sadrži:
- Napomene koje porede taj nacrt sa nacrtima u drugim predmetima ("ovaj je jači od onog u predmetu X jer...").
- Objašnjenja odakle potiče neki deo obrazloženja (koji predmet/skill ga je otkrio) — to spada u napomenu "Poreklo i istorija ovog obrasca" u generičkom modelu u `04_OBRASCI/USAVRSENI-MODELI/`, ne u sam nacrt za podnošenje.
- Uputstva za popunjavanje budućih, drugih predmeta.

Kratke, ČISTO PRAKTIČNE napomene vezane SAMO za taj konkretan nacrt (npr. "proveriti tačan iznos AT pre podnošenja", "proveriti punomoćje") mogu ostati uz nacrt ako je to korisno za samo podnošenje — razlika je: sve što pomaže PODNOŠENJU OVOG KONKRETNOG AKTA ostaje uz njega; sve što pomaže IZRADI BUDUĆIH, DRUGIH akata ide u generički model.

**Praktičan tok**: kad se iz uvezenog dokumenta i/ili sačinjenog nacrta prepozna generalizabilan obrazac (v. tačku 6 iznad), taj generički obrazac se piše/ažurira u `04_OBRASCI/USAVRSENI-MODELI/`, sa odeljkom na dnu "Poreklo i istorija ovog obrasca" koji objašnjava iz kojih je predmeta/nalaza nastao (v. primer u `04_OBRASCI/USAVRSENI-MODELI/ZALBA-ZBOG-CUTANJA-UPRAVE-RGZ.md` i `ZAHTEV-ZA-DONOSENJE-DOPUNSKOG-RESENJA-RGZ.md`) — dok konkretan nacrt u `02_OUTPUT/` ostaje čist, bez te istorije.

## Primer već primenjenog obrasca (pre formalizacije ovog skilla)
- Pri uvozu stvarnih RGZ podnesaka iz predmeta Milić-Zoran (30.8.2026), otkriveno je da RGZ Služba za katastar nepokretnosti Zvezdara opisuje katastarsku parcelu sa mnogo više detalja (JMBN broj, naziv poteza, kultura/klasa, tačan razmer poseda kao razlomak) nego što je generički obrazac `ZAHTEV-ZA-UPIS-PRAVA-SVOJINE-NA-KATASTARSKOJ-PARCELI.md` prvobitno predviđao — obrazac je odmah ažuriran uz napomenu o izvoru.
- Isti obrazac je dopunjen i verifikovanim doktrinarnim nalazom (Vukotić 2012 — konstitutivno/deklarativno dejstvo upisa) i nalazom o obaveznoj javnobeležničkoj formi (Jovanović 2025) — ovo pokazuje da usavršavanje obrasca ne mora doći samo iz novih PODNESAKA, već i iz doktrine/prakse otkrivene tokom rada na predmetu (v. skill `10-teorijska-analiza`) — isti princip usavršavanja, širi izvor.
- Suprotan primer (šta NE preneti automatski): u istom periodu, žalba u predmetu Roković-02 je netačno citirala opšti (30-dnevni) rok umesto tačnog, posebnog (15-dnevnog) roka iz Zakona o upisu u katastar; tužba u predmetu Roković-03 je netačno citirala ZUP čl. 5/10 umesto čl. 11. Ovakve greške iz STVARNIH, predatih dokumenata NE unose se u obrazac kao "praksa" — obrazac treba da odražava TAČNO pravo, ne grešku koju je neko ponovio u praksi.

## Odnos prema `21-legal-model-builder`
Ovaj skill (14) je AUTOMATSKO, organsko usavršavanje jednog obrasca iz jednog novopristiglog dokumenta (`04_OBRASCI/USAVRSENI-MODELI/`). Kad korisnik EKSPLICITNO zatraži model sintetizovan iz VIŠE izvora odjednom ("napravi model X", "napravi najbolji model koji imamo") — to je `21-legal-model-builder` (`04_OBRASCI/GENERISANI_MODELI/`), ne ovaj skill. Ne duplirati: ako 21 pri sintezi naiđe na obrazac koji je ovaj skill već usavršio, koristi ga kao jedan od ulaznih izvora.

## Šta ovaj skill NE sme da radi
- Ne menja SUŠTINU/pravni stav postojećeg obrasca na osnovu jednog dokumenta bez provere (v. tačka 5).
- Ne uklanja postojeće, već verifikovane napomene i upozorenja u obrascu radi "čišćenja" — dodaje se, retko se briše, a kad se nešto zaista pokaže pogrešnim, to se EKSPLICITNO ispravlja uz napomenu, ne tiho briše.
- Ne pravi nov obrazac za svaki pojedinačni, usko specifičan podnesak — samo za ponovljive, generičke vrste akata (v. tačka 6).
