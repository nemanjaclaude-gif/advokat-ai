---
name: anonimizacija
description: Anonimizuje/pseudonimizuje lične podatke iz uvezenih dokumenata i radnih materijala predmeta, po uzoru na zvanični "Pravilnik o zameni i izostavljanju (pseudonimizaciji/anonimizaciji) podataka u sudskim odlukama" Vrhovnog kasacionog suda (u primeni od 1.1.2017). Poprečni skill — primenjuje se NA ZAHTEV (izvoz, deljenje, arhiviranje predmeta), ne kao automatski korak u svakoj analizi.
---

# ANONIMIZACIJA

## Kada se koristi
**Automatski, pri svakom uvozu NOVOG predmeta** (od 30.8.2026) — čim se za predmet napravi `CASE.md`, u istom koraku se pravi anonimizovana verzija.

**Podrazumevano ponašanje je IN-PLACE (od 30.8.2026, izričita odluka korisnika)**: sam radni fajl (`CASE.md`, i dalji radni materijali kad se anonimizuju) se ZAMENJUJE anonimizovanom verzijom — original sa stvarnim podacima se ne čuva paralelno. `MAPA-PSEUDONIMA.md` (pravo ime → pseudonim) se i dalje pravi i čuva — ona je jedino mesto gde veza između pseudonima i stvarnog lica ostaje rekonstruktivna, i tretira se kao lični podatak (v. odeljak GDPR/ZZPL ispod).

Korisnik je eksplicitno potvrdio (30.8.2026) da razume posledicu: radni fajlovi u ovom obliku više ne sadrže stvarna imena/JMBG i ne mogu se direktno koristiti za sastavljanje pravih podnesaka bez ručnog vraćanja podataka iz `MAPA-PSEUDONIMA.md`.

**Izuzetak — originalni skenirani dokumenti** (`00_ULAZNI_DOKUMENTI/`, slike/skenovi): ovi se NE brišu automatski, jer se ne mogu pouzdano anonimizovati (v. "Pravilo potpunosti" ispod) — brisanje bez postojeće anonimizovane zamene bio bi čist, nepovratan gubitak primarnog izvora, ne anonimizacija. Ako korisnik izričito zatraži i njihovo brisanje, to učiniti tek uz posebno, nedvosmisleno potvrđivanje za TAJ konkretan dokument.

## Domet (scope) — SAMO predmeti, NIKAD autori izvora

Anonimizacija se primenjuje ISKLJUČIVO na `01_PREDMETI/` (klijenti, protivne strane, svedoci i druga fizička/pravna lica iz konkretnog spora). **Nikad se ne primenjuje na `05_IZVORI/`** — autore doktorskih disertacija i članaka u `LITERATURA/` i `CASOPISI/`, sudije/veštake/stranke pomenute u već objavljenoj sudskoj praksi u `SUDSKA-PRAKSA/`, niti na bilo koga drugog ko se pominje ISKLJUČIVO kao autor/izvor citiranog rada. Ti ljudi su javno objavili rad pod sopstvenim imenom — anonimizacija tu nema svrhu (ništa se ne štiti) i samo bi upropastila tačnost citata.

**Praktična posledica**: pre nego što se ime iz predmeta (npr. "Zoran Milić") automatski zameni pseudonimom kroz ceo fajl, PROVERITI da li se isto ili slično ime pojavljuje i kao ime CITIRANOG AUTORA u istom fajlu (npr. u odeljku `TEORIJSKA POTKREPLJENOST`) — ako da, ograničiti zamenu na tačno one pojave koje se odnose na stranku u predmetu, ne na sve pojave tog imena/prezimena u fajlu. (Ovo je već jednom pogrešno urađeno — v. napomenu o ispravci od 30.8.2026 — i otad je obavezna provera pre svake nove zamene.)

## Model: Pravilnik VKS o zameni i izostavljanju podataka

Metodologija je preuzeta iz zvaničnog pravilnika po kome sudovi u Srbiji anonimizuju/pseudonimizuju svoje odluke pre objavljivanja (isti obrazac se vidi u citiranim odlukama Ustavnog suda i VKS u `05_IZVORI/SUDSKA-PRAKSA/` — oznake "АА", "ББ", "ВВ"...).

### Šta se ZAMENJUJE (fizička lica)
- Ime i prezime svakog fizičkog lica čiji je identitet predmet zaštite (stranke, zakonski zastupnici, svedoci, treća lica pomenuta u činjeničnom opisu) — zamenjuje se sa **dva ista velika slova**, redom pojavljivanja u predmetu: prvo pomenuto lice **АА**, drugo **ББ**, treće **ВВ**, itd.
- Uz slovnu oznaku OBAVEZNO zadržati procesnu ulogu tog lica (npr. "АА (тужилац)", "ББ (сведок)") — anonimizacija ukida IDENTITET, ne SVOJSTVO u postupku, jer je svojstvo često nužno za razumevanje analize.
- **Isto lice mora dobiti ISTI pseudonim kroz CEO predmet i kroz SVE fajlove tog predmeta** (CASE.md, HRONOLOGIJA, EVIDENCE-MATRIX, PRAVNA-ANALIZA, izvorni dokumenti) — nedosledna dodela čini anonimizovanu verziju nekoherentnom i, gore, može posredno odati identitet unakrsnim poređenjem.

### Šta se IZOSTAVLJA (potpuno briše, ne zamenjuje placeholderom)
JMBG, adresa prebivališta/sedišta, broj telefona, email, broj tekućeg računa/kartice, biometrijski i zdravstveni podaci, potpis/faksimil. Ovi podaci se NE zamenjuju sličnim placeholderom (npr. lažnim JMBG-om) koji bi mogao delovati kao stvaran — jednostavno se brišu ili označavaju kao `[IZOSTAVLJENO]`.

### Šta se zamenjuje sa "..." (pravna lica i ostali identifikacioni podaci)
Naziv privrednog društva/drugog pravnog lica, matični broj, PIB i sl. — zamenjuju se sa tri tačke (`...`), uz zadržavanje OZNAKE VRSTE podatka (npr. `"... д.о.о."`, `"МБ ..."`) kad je to potrebno za razumljivost teksta.

### Šta se NIKAD ne anonimizuje
- Nazivi državnih organa, sudova, javnih preduzeća, teritorijalnih jedinica.
- Sudije, javni tužioci, javni beležnici, sudski veštaci, tumači, advokati **kao zastupnici/punomoćnici u službenom svojstvu** — oni deluju u javnoj/profesionalnoj funkciji, ne kao privatna lica čiji se identitet štiti.
- Sam pravni sadržaj: brojevi članova zakona, pravna kvalifikacija, argumentacija, već javno objavljena sudska praksa — anonimizacija menja SAMO identifikatore fizičkih/pravnih lica čiji se identitet štiti, nikad suštinu analize.

## Usklađenost sa GDPR i Zakonom o zaštiti podataka o ličnosti

- **Pravni okvir**: Zakon o zaštiti podataka o ličnosti ("Sl. glasnik RS", br. 87/2018) i, za obradu koja dotiče lica/subjekte iz EU, Opšta uredba o zaštiti podataka (GDPR, EU 2016/679. Advokatska obrada podataka klijenata i suprotnih stranaka po pravilu počiva na pravnom osnovu izvršenja ugovora o zastupanju / ostvarivanja pravnog zahteva (čl. 12 ZZPL / čl. 6 st. 1 tač. b, f GDPR) — anonimizacija/pseudonimizacija je DODATNA mera zaštite, ne zamena za taj osnov.
- **Bitna terminološka razlika (ne mešati)**: Metod opisan u ovom skillu (zamena imena sa АА/ББ + čuvanje `MAPA-PSEUDONIMA.md` na osnovu koje se veza može ponovo uspostaviti) je, u smislu GDPR čl. 4(5) i ZZPL čl. 4 tač. 9, **PSEUDONIMIZACIJA**, ne anonimizacija. Pseudonimizovan podatak i dalje JESTE "lični podatak" u pravnom smislu (jer je re-identifikacija moguća preko mape) i i dalje podleže ZZPL/GDPR obavezama — uključujući to da sam `MAPA-PSEUDONIMA.md` fajl mora biti čuvan i zaštićen kao lični podatak (ne slati nezaštićen, ne deliti bez potrebe), i da rok čuvanja tog fajla treba ograničiti na svrhu radi koje postoji.
- **Prava anonimizacija** (podatak trajno prestaje da bude "lični podatak") nastaje samo ako se mapa TRAJNO UNIŠTI i re-identifikacija postane nemoguća čak i posrednim putem (npr. unakrsnim poređenjem sa ostalim javno dostupnim podacima o predmetu — broj predmeta, datumi, iznosi mogu i sami, u kombinaciji, činiti lice odredivim, čak i bez imena). Kad korisnik zahteva "punu anonimizaciju" (ne pseudonimizaciju), to eksplicitno znači: (a) ne praviti mapu uopšte, ili je odmah uništiti, i (b) proceniti da li ostali, nezamenjeni podaci (kombinacija broja predmeta/suda/datuma/iznosa) sami po sebi čine lice odredivim — ako da, i te podatke generalizovati/ukloniti, ne samo ime.
- **Načelo minimizacije podataka** (čl. 5 ZZPL / čl. 5(1)(c) GDPR): anonimizovana kopija treba da sadrži SAMO podatke neophodne za svrhu radi koje se pravi (npr. za obuku/deljenje van kancelarije) — ne kopirati mehanički sve što postoji u radnom fajlu ako deo toga nije potreban za tu konkretnu svrhu.
- **Zabrana korišćenja za treniranje AI modela**: Fajlovi koji sadrže stvarne lične podatke (radni materijali predmeta, `00_ULAZNI_DOKUMENTI`, neanonimizovani `CASE.md` i dr.) **NE SMEJU** se koristiti kao trening/fine-tuning podaci za bilo koji AI/ML model, niti prosleđivati u tu svrhu bilo kom eksternom servisu. Ni ANONIMIZOVANA/pseudonimizovana verzija se ne sme koristiti u tu svrhu bez izričite, posebne saglasnosti korisnika i utvrđenog pravnog osnova za tu KONKRETNU, DRUGAČIJU svrhu obrade (svrha "vođenje predmeta" ≠ svrha "treniranje modela" — ZZPL čl. 7/8 i GDPR čl. 5(1)(b) zahtevaju da se podaci ne obrađuju dalje na način nespojiv sa svrhom za koju su prikupljeni).

## Gde i kako se primenjuje u ovom sistemu

**Podrazumevano (od 30.8.2026): IN-PLACE zamena.**
- Radni fajl (npr. `CASE.md`) se anonimizuje i ta anonimizovana verzija POSTAJE sadržaj tog fajla — stvarni podaci se ne čuvaju paralelno u samom radnom fajlu.
- `01_PREDMETI/<predmet>/03_ANONIMIZOVANO/MAPA-PSEUDONIMA.md` ostaje jedino mesto sa vezom pseudonim → pravo ime za taj predmet — čuvati je, ali NIKAD je ne deliti/objavljivati zajedno sa anonimizovanom verzijom.
- Originalni skenirani dokumenti u `00_ULAZNI_DOKUMENTI/` se NE brišu (v. izuzetak gore) — ostaju jedini nosilac stvarnih podataka u tom obliku van mape.
- Ako korisnik za KONKRETNU svrhu (npr. jednokratno deljenje van kancelarije) treba anonimizovanu verziju BEZ menjanja radnog fajla, to eksplicitno reći — tada se pravi zasebna kopija u `03_ANONIMIZOVANO/`, kao izuzetak od podrazumevanog in-place ponašanja.

## Pravilo potpunosti (zero-hallucination / zero-leftover)
- Anonimizacija se ne smatra završenom dok se ne izvrši PROVERA: pretražiti (grep/pretraga teksta) ceo anonimizovani fajl na originalne identifikatore (imena, JMBG, brojeve telefona, adrese) da bi se potvrdilo da ništa nije ostalo — ne osloniti se na jedan prolaz kroz tekst.
- Posebno paziti na identifikatore koji se pojavljuju IZVAN glavnog teksta: zaglavlja, fusnote, imena fajlova, metapodaci dokumenta (autor, naslov fajla), potpisi na kraju akata.
- **Skenirani dokumenti (slike, ne čist tekst)**: ako lični podaci postoje VIZUELNO na skeniranoj strani (rukom pisan potpis, pečat, faksimil), sama tekstualna anonimizacija transkripta NIJE dovoljna — original ostaje neizmenjen sa vidljivim podacima. To eksplicitno navesti korisniku kao ograničenje (anonimizacija transkripta ≠ anonimizacija skena), ne prećutati.
- Ako se posle provere ustanovi da nešto nije moglo biti pouzdano identifikovano/anonimizovano (npr. nejasan rukopis, dvosmislen kontekst), to eksplicitno navesti — ne tvrditi da je anonimizacija potpuna kad nije proverena do kraja.

## Izuzetak — akti namenjeni podnošenju (02_OUTPUT)
Nacrti akata u `02_OUTPUT/` (tužbe, replike, žalbe i sl., iz skilla `07-izrada-akta`) namenjeni su STVARNOM podnošenju sudu/organu — moraju sadržati prava imena, JMBG i adrese stranaka da bi uopšte bili pravno valjani i upotrebljivi. **Ovi fajlovi se NE anonimizuju automatski** — anonimizacija bi ih učinila neupotrebljivim za jedinu svrhu radi koje postoje. Anonimizovati ih samo ako korisnik izričito zatraži anonimizovanu verziju za DRUGU svrhu (npr. primer, deljenje van konteksta podnošenja).

## Šta anonimizacija NE sme da promeni
- Pravne zaključke, citate zakona, ocenu izgleda za uspeh — anonimizacija je isključivo tehnička obrada identifikatora, nikad prilika da se sadržaj "uredi" ili skrati.
