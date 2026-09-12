---
name: case-law-analyzer
description: CASE_LAW_ANALYZER — analitičko (ne sažeto) čitanje JEDNE sudske odluke. Utvrđuje šta je sud STVARNO odlučio, zbog kojih činjenica, primenom kog pravila, i dokle doseže pravni stav iz te odluke — razdvaja ratio decidendi od obiter dicta, i aktivno traži granice dometa odluke. Koristiti pri obradi svake pojedinačne odluke koja ulazi u CASE CARD (`05-sudska-praksa`) pre nego što se ta odluka koristi za poređenje (`15-poredjenje-sudske-prakse`) — ovaj skill je korak DUBLJEG čitanja JEDNE odluke; 15 je korak POREĐENJA više odluka/predmeta.
---

# CASE_LAW_ANALYZER

Cilj: NE praviti običan rezime presude. Utvrditi domet i granice pravnog stava.

## 1. Metapodaci
Sud; broj predmeta; datum; vrsta odluke; pravna oblast; instanca; ishod postupka.

## 2. Procesna istorija
Ukratko rekonstruisati: šta je traženo; šta je odlučio prvostepeni sud; šta je odlučio drugostepeni sud; koji pravni lek je podnet; šta je predmet razmatranja odluke koja se analizira (npr. da li je ovo presuda po reviziji, žalbi, ili prvostepena).

## 3. Materijalno relevantne činjenice
NE prepisivati celokupno činjenično stanje. Izdvojiti samo činjenice koje su uticale na primenu pravnog pravila i ishod, i označiti ih: **DECISIVE FACTS** — činjenice bez kojih bi ishod potencijalno mogao biti drugačiji.

## 4. Pravno pitanje
Formulisati što uže. Izbegavati uopštene formulacije ("pitanje je pravo svojine"). Umesto toga: "Da li lice koje je..., ima pravo da..., ako je...". Pravno pitanje mora omogućiti KASNIJE poređenje sa drugim predmetom (v. `15-poredjenje-sudske-prakse`).

## 5. Primenjeni izvori prava
Izdvojiti: propis; član; međunarodni izvor; raniju sudsku praksu; ustavnosudsku praksu; praksu ESLJP; druga pravna pravila. **Razlikovati izvor koji je sud STVARNO primenio od izvora koji je samo pomenut** (usput, u pregledu argumenata stranaka, bez oslanjanja u odluci).

## 6. Ratio decidendi
Formulisati u obliku: **"ako [odlučne činjenice], onda [pravna posledica], zato što [pravni razlog]"**. Ne izvlačiti ratio iz jedne rečenice izolovane od činjeničnog konteksta.

## 7. Obiter dicta
Odvojeno identifikovati: opšte konstatacije; dodatne argumente; hipotetičke stavove; pravne stavove koji NISU bili neophodni za ishod. Ne predstavljati obiter kao ratio.

## 8. Domet odluke
Utvrditi: šta odluka zaista potvrđuje; šta odluka NE potvrđuje; za koje činjenične situacije je primenljiva; koje činjenične promene mogu dovesti do drugačijeg rezultata.

## 9. Potencijalni distinguishing
Pitanje: *"Koja činjenica bi morala biti drugačija da ova odluka više ne predstavlja snažan presedan/analogiju?"* — izdvojiti te činjenice unapred, pre nego što ih suprotna strana pronađe.

## 10. Odnos prema drugim odlukama
Ako su dostupne druge odluke: identifikovati koje SLEDI, koje RAZLIKUJE, koje NAPUŠTA, sa kojima je u POTENCIJALNOM KONFLIKTU.

**Ne proglašavati konflikt samo zato što su ishodi različiti — prvo proveriti da li su materijalno relevantne činjenice iste** (v. primer `05_IZVORI/SUDSKA-PRAKSA/UPRAVNI-SUD/20-U-26267-20.md` vs `9-U-23869-2010.md`/`U-1103-2018.md` — na prvi pogled različiti ishodi, ali NIJE konflikt jer se tiču različitog procesnog koraka: obaveza da se odluči, naspram ISHODA te odluke).

## 11. Izlaz
- **Odluka**
- **Pravno pitanje**
- **Odlučne činjenice**
- **Primenjeno pravilo**
- **Ratio decidendi**
- **Obiter**
- **Ishod**
- **Domet pravnog stava**
- **Šta ova odluka NE dokazuje**
- **Potencijalni distinguishing**
- **Značaj za buduće predmete**
- **Nivo sigurnosti analize**: Visok / Srednji / Nizak — ako je dostupan samo izvod, sentenca ili sekundarni izvor (npr. doktrinarni prikaz, ne pun tekst presude), to mora biti IZRIČITO navedeno (v. status VERIFIED/posredno u CASE CARD-ovima nastalim iz doktrinarnih beležaka, npr. `VSS-U-2205-2007.md`).

## Gde ide rezultat
Izlaz iz odeljka 11 mora biti usklađen sa **JUDGMENT_RECORD** standardom (`20-legal-knowledge-record-standard`, odeljak II) — polja se direktno preslikavaju (Odluka→IDENTIFICATION, Pravno pitanje→LEGAL ISSUE, Odlučne činjenice→DECISIVE FACTS, Primenjeno pravilo→APPLICABLE LAW, Ishod→OUTCOME, Domet→SCOPE, Šta NE dokazuje→LIMITATIONS, Nivo sigurnosti→RELIABILITY). Za odluke koje su **stvarno dubinski analizirane** (ne mehanički, v. `19-legal-research-orchestrator` t. 4, RELEVANCE SCREENING) — kreirati ili ažurirati zapis u `05_IZVORI/SUDSKA-PRAKSA/_ANALIZE/` po formatu `04_OBRASCI/KNOWLEDGE_RECORDS/JUDGMENT_RECORD_TEMPLATE.md`, sa obaveznim poljima: DECISIVE FACTS, LEGAL ISSUE, APPLICABLE LAW, HOLDING, RATIO DECIDENDI, OUTCOME, SCOPE, LIMITATIONS, DISTINGUISHING FACTORS, RELATED ISSUES, RELIABILITY. Uvek zadržati provenance (izvor dokumenta) prema originalnoj odluci — original ostaje netaknut na svom postojećem mestu (`UPRAVNI-SUD/`, `USTAVNI-SUD/`, itd., ili unutar predmeta). **Analitički zapis NIKAD ne zamenjuje original kad je potrebna provera** (tačan citat, sumnja u raniju analizu, nova praksa) — v. `20-legal-knowledge-record-standard`, odeljak XIV (REUSE RULE).

Lakši CASE CARD format (`05-sudska-praksa`) ostaje dovoljan za odluke koje su samo uzgredna potvrda, ne centralni presedan.

## Odnos prema drugim skill-ovima
- Prethodni korak: `05-sudska-praksa` (pronalaženje/osnovni CASE CARD) i `04-pravno-istrazivanje`.
- Ovaj skill PRODUBLJUJE polja "Pravno shvatanje"/"Ratio decidendi" u CASE CARD-u — koristiti ga pre popunjavanja tih polja kad je odluka centralna za predmet, ne samo uzgredna potvrda.
- Sledeći korak (kad se odluka poredi sa VIŠE drugih ili sa konkretnim predmetom): `15-poredjenje-sudske-prakse`.
- Kad se čitava sudska/upravna stvar (ne samo jedna odluka) mapira iz mnogo dokumenata: `16-case-extractor`.
- Ovaj skill NE poredi predmete niti pravne stavove (to radi isključivo `15-poredjenje-sudske-prakse`) i NE napada sopstveni nalaz (to radi `18-devils-advocate`) — samo dubinski čita JEDNU odluku.
