---
name: sinteza-izvora
description: Pre pisanja bilo kog akta (skill 07-izrada-akta), sistematski prikuplja i koristi SVE što je do tada urađeno i uneto u sistem za dati predmet — radne materijale, izvore, ranije napravljene CASE CARD-ove i nalaze iz srodnih predmeta — tako da nijedan raniji rad ne bude zaboravljen ili neiskorišćen. Poprečni (cross-cutting) skill — ne predstavlja poseban korak u WORKFLOW redosledu, primenjuje se UVEK neposredno pre skilla 07-izrada-akta.
---

# SINTEZA IZVORA

## Svrha
Sprečiti situaciju u kojoj se akt piše "iz glave" ili samo iz poslednje pročitane napomene, dok ostatak već obavljenog rada (istraživanje, analiza, pronađena praksa, doktrina) ostaje neiskorišćen. Pre svakog pisanja akta, napraviti kratak, eksplicitan INVENTAR svega relevantnog što već postoji.

## Kada se koristi
Uvek neposredno pre `07-izrada-akta` — bez obzira da li je akt tužba, odgovor na tužbu, replika, žalba, podnesak, zahtev ili bilo koji drugi dokument koji se predaje sudu/organu ili klijentu.

## Redosled prikupljanja (checklist)

1. **Radni materijali PREDMETA** (`01_PREDMETI/<predmet>/`) — pročitati sve što postoji, ne samo poslednji fajl koji je otvoren:
   - `CASE.md` (činjenice, rokovi, stranke, cilj klijenta)
   - `01_RADNI_MATERIJALI/HRONOLOGIJA.md`
   - `01_RADNI_MATERIJALI/EVIDENCE-MATRIX.md`
   - `01_RADNI_MATERIJALI/KLASIFIKACIJA.md`, `LEGAL-ISSUES.md`
   - `01_RADNI_MATERIJALI/PRAVNO-ISTRAZIVANJE.md`
   - `01_RADNI_MATERIJALI/PRAVNA-ANALIZA.md` — **uključujući odeljke `TEORIJSKA POTKREPLJENOST` i sve naknadne `Dopuna (datum)` blokove** — ovi se lako previde jer su dodavani u više navrata.
   - `01_RADNI_MATERIJALI/STRATEGIJA.md` — posebno odeljke "Šta NE raditi u ovoj fazi" i eksplicitne preduslove za pisanje akta.
   - Sve prethodne verzije akata u `02_OUTPUT/` za isti predmet (da se ne ponavlja već urađen nacrt niti se gubi kontinuitet numeracije/argumentacije).

2. **Izvori prava** (`05_IZVORI/PROPISI`) — koristiti već verifikovane članove zakona iz PRAVNA-ANALIZA/PRAVNO-ISTRAZIVANJE, ne ponovo nagađati broj člana.

3. **Sudska praksa** (`05_IZVORI/SUDSKA-PRAKSA/`):
   - CASE CARD-ovi već napravljeni ZA OVAJ predmet.
   - CASE CARD-ovi u `VRHOVNI-SUD/`, `USTAVNI-SUD/`, `UPRAVNI-SUD/` — proveriti da li neki od već pronađenih (za DRUGI predmet) rešava isto ili srodno pravno pitanje.
   - `BILTENI/` — ako pitanje još nije pretraživano u bilтenima, uraditi to pre pisanja (v. `05-sudska-praksa`).
   - Živi izvor VKS (Građanska materija) — ako relevantno pravno pitanje još nije provereno kroz njega u ovoj analizi, uraditi pre pisanja akta, ne posle.

4. **Doktrina** — `05_IZVORI/LITERATURA` (skill `10-teorijska-analiza`) i `05_IZVORI/CASOPISI` (skill `11-strucni-clanci`) — preuzeti već postojeće nalaze iz PRAVNA-ANALIZA.md; ako predmet još nije prošao kroz ta dva skilla, pokrenuti ih pre pisanja akta.

5. **Srodni predmeti** (`01_PREDMETI/`) — proveriti da li postoji drugi predmet sa istim protivnikom, istim sudijom, istim činjeničnim obrascem ili istim pravnim pitanjem (odeljak `VEZA SA DRUGIM PREDMETIMA`, ako postoji, ili pretraga po ključnim rečima). Nalaz iz drugog predmeta može poslužiti kao dodatni argument/analogija — uz jasnu naznaku da je iz DRUGOG, formalno nepovezanog postupka.

6. **Obrasci** (`04_OBRASCI/`) — proveriti da li postoji već ustaljen format/struktura za tu vrstu akta pre nego što se format izmišlja iznova.

## Pravilo (zero hallucination)
- Ne tvrditi da je nešto "već urađeno/pronađeno/verifikovano" ako se to ne može pronaći u navedenim izvorima — ako neki korak (npr. skill 10/11 ili VKS pretraga) nije ranije sproveden za ovo pravno pitanje, to znači da GA TREBA sprovesti SADA, pre pisanja akta, ne pretpostaviti rezultat.
- Ako se posle pregleda svih izvora ustanovi da je ključan preduslov za pisanje akta i dalje nedostupan (npr. original dokumenta, kako je zabeleženo u `STRATEGIJA.md` odeljku "Šta NE raditi"), to eksplicitno preneti korisniku PRE pisanja, ne tek u napomenama unutar gotovog nacrta.

## Output
Kratak "INVENTAR IZVORA ZA OVAJ AKT" (interni, ne unosi se u sam podnesak) — nabraja šta je od gore navedenog stvarno pronađeno i iskorišćeno, a šta nije postojalo/nije pronađeno. Ide neposredno pre teksta nacrta iz skilla `07-izrada-akta`, u istom formatu kao napomene koje taj skill već zahteva (oznaka NACRT — ZA REVIZIJU ADVOKATA).
