---
name: legal-position-synthesizer
description: LEGAL_POSITION_SYNTHESIZER — identifikuje, izdvaja, proverava, poredi i sintetiše PRAVNE STAVOVE I MIŠLJENJA o konkretnom pravnom pitanju iz SVIH relevantnih izvora (propisi, sudska praksa, akti iz predmeta, modeli, literatura, članci) — ne samo propis+praksa+AI zaključak, nego i šta je već zastupano u aktima kancelarije, u modelima, i u doktrini, sa jasnim razdvajanjem KO šta tvrdi. Aktivirati kod ozbiljne pravne analize, istraživanja pravnog pitanja, ocene osnovanosti teze, izrade strategije/mišljenja/značajnog podneska, ili modela koji zahteva pravno obrazloženje. NE aktivirati za jezičku redakturu, formatiranje, tehničku izmenu, ili prostu anonimizaciju.
---

# LEGAL_POSITION_SYNTHESIZER

## Svrha
Osnovni tok: **LEGAL ISSUE → ŠTA IZVORI KAŽU O TOME? → KO ŠTA KAŽE? → NA KOM OSNOVU? → SLAŽU LI SE STAVOVI ILI SU U KONFLIKTU? → KOLIKO JE SVAKI STAV JAK? → SINTEZA.** Ne zamenjuje postojeće skillove — koristi NJIHOVE rezultate i dodaje poseban sloj: **POSITION/OPINION SYNTHESIS**. Ne radi ponovo posao koji je drugi skill već pouzdano obavio (v. §Integracija ispod).

## 1. Primarni objekat — LEGAL ISSUE
Ne tražiti stavove apstraktno. Prvo identifikovati KONKRETNO pravno pitanje (isti standard kao `17-case-law-analyzer` t. 4 i `20-legal-knowledge-record-standard` odeljak V) — npr. ne "faktička eksproprijacija", nego "Da li vlasnik nepokretnosti koja je faktički privedena javnoj nameni ima, pored tržišne naknade, i pravo na naknadu za njeno korišćenje do dosuđenja te naknade?". Svaki pronađen stav mora biti povezan sa TIM konkretnim pitanjem.

## 2. Izvori za pretragu
Prema ISSUE-u, po potrebi: **PROPISI** (`05_IZVORI/PROPISI/`); **SUDSKA PRAKSA** (`05_IZVORI/SUDSKA-PRAKSA/` + postojeći JUDGMENT_RECORD); **INTERNI AKTI** (`01_PREDMETI/` — tužbe, odgovori, žalbe, revizije, ustavne žalbe, mišljenja); **MODELI** (`04_OBRASCI/`, `04_OBRASCI/GENERISANI_MODELI/`); **LITERATURA** (`05_IZVORI/LITERATURA/`); **ČLANCI** (`05_IZVORI/CASOPISI/`); **KNOWLEDGE LAYER** (ISSUE/SCHOLARSHIP/JUDGMENT/CASE_RECORD i postojeće sinteze).

## 3. Retrieval first
Ne čitati automatski ceo korpus. Prvo `22-legal-knowledge-retriever` (+ Knowledge Layer) da pronađe potencijalno relevantne izvore, tek onda **TARGETED SOURCE READING**: RETRIEVE → FILTER → READ RELEVANT PARTS → EXTRACT POSITIONS → VERIFY → SYNTHESIZE. Ne duplirati retrieval ako je korpus već pouzdano identifikovan (v. §11 ispod).

## 4. Šta je "pravni stav"
Tvrdnja o: značenju norme; uslovima primene; pravnoj kvalifikaciji; pravnoj posledici; odnosu dve norme; dometu prakse; procesnom pitanju; dokaznom standardu; pravnoj prirodi instituta; postojanju/nepostojanju prava; tumačenju spornog pitanja. Ne izdvajati kao "pravni stav" svaku rečenicu iz dokumenta.

## 5. Obavezna klasifikacija izvora (nikad ih ne mešati)
Svaki izdvojen stav mora biti označen KO ga zastupa — najmanje ovih 7 kategorija:

| Tip | Kad se koristi | Šta obavezno navesti |
|---|---|---|
| **NORMATIVE RULE** | Stav neposredno proizlazi iz propisa | propis, član, verzija u vremenu — ne predstavljati TUMAČENJE norme kao sam njen tekst |
| **COURT POSITION** | Stav potiče iz sudske odluke | sud, broj, datum, pravno pitanje, ratio, odlučne činjenice, ograničenje primene, reliability. Ako je preuzet samo iz literature/starog podneska (ne iz same odluke) → **COURT POSITION — SECONDARY REFERENCE**, dok original nije proveren (v. `20` odeljak X) |
| **SCHOLARLY POSITION** | Stav potiče iz literature | autor, delo, godina, poglavlje, strana (ili `PAGE NOT VERIFIED` ako nije pouzdano utvrđena — nikad izmišljati), suština stava, argumenti, da li autor podržava/kritikuje praksu |
| **OFFICE POSITION** | Teza već zastupana u aktu iz nekog predmeta | predmet, vrsta akta, datum ako poznat, suština, argumenti, izvori na koje se akt oslanja, ishod ako poznat. **OFFICE POSITION ≠ LAW** — raniji podnesak ne dokazuje da je stav tačan |
| **PARTY POSITION** | Akt NIJE stav kancelarije (podnesak protivne strane, tuđe mišljenje) | isto kao OFFICE POSITION, ali jasno označeno da nije naš stav — ne pripisivati tuđi stav kancelariji |
| **MODEL POSITION** | Teza pronađena u modelu (`04_OBRASCI/`) | na kojim izvorima model počiva, kad je napravljen, da li je VERIFIED, da li je pravo od tada promenjeno. Model NIJE pravni autoritet — služi za otkrivanje/ponovnu upotrebu argumentacije, ne kao dokaz ispravnosti |
| **AI SYNTHESIS** | Sopstveni zaključak sistema | uvek eksplicitno "Iz navedenih izvora proizlazi..." — nikad predstaviti kao stav suda/zakonodavca/autora/kancelarije |

## 6. POSITION RECORD (interni format)
Za svaki materijalno relevantan stav interno formirati: `POSITION-ID`, `ISSUE-ID`, `POSITION TYPE` (v. §5), `SOURCE`, `AUTHOR/COURT/DOCUMENT`, `PROPOSITION`, `LEGAL BASIS`, `SUPPORTING REASONING`, `SOURCE LOCATION`, `DATE`, `TEMPORAL RELEVANCE`, `SUPPORTS`/`CONTRADICTS`/`QUALIFIES`/`DISTINGUISHES` (v. relacije u `20-legal-knowledge-record-standard` odeljak VI), `RELIABILITY`.

## 7. Ne tražiti samo podršku
Za svako važno pitanje tražiti: **SUPPORTING** (podržava tezu), **CONTRARY** (protivreči), **QUALIFYING** (prihvata samo pod određenim uslovima), **ALTERNATIVE** (drugačija pravna konstrukcija istog problema), **UNRESOLVED** (izvori ne daju jasan odgovor). Isti anti-confirmation-bias princip kao `19` t. 15 i `22` t. 6, primenjen posebno na STAVOVE, ne samo na praksu.

## 8. POSITION MAP
Za svako važno ISSUE napraviti internu mapu: ISSUE → NORMATIVE BASIS → COURT POSITION A/B (ako ih ima više, uklj. suprotne) → SCHOLARLY POSITION A/B → OFFICE POSITION → MODEL POSITION → CONFLICT (gde se stavovi razilaze) → SYNTHESIS (šta celina izvora pokazuje).

## 9. Obavezan deo finalnog output-a
Kod ozbiljne pravne analize, finalni output sadrži poseban odeljak **"STAVOVI I MIŠLJENJA O RELEVANTNIM PRAVNIM PITANJIMA"**, za svako važno pitanje: Normativni okvir → Sudska praksa → Stavovi iz postojećih akata → Stavovi iz modela → Pravna literatura → Suprotna mišljenja → Sinteza. Ovo se NADOVEZUJE na `19-legal-research-orchestrator` t. 21 (Final synthesis struktura) kao dodatan, dublji sloj kad je pitanje dovoljno važno da to opravda — ne zamenjuje tu strukturu, dopunjuje je.

## 10. Ne pretvarati u katalog
Finalni tekst NIJE "Autor A kaže X. Autor B kaže Y. U predmetu C piše Z." — posle predstavljanja stavova mora slediti PRAVNA SINTEZA: gde se podudaraju, gde se razlikuju, zašto, koji ima jači normativni oslonac, koji je prihvaćen u praksi, koji zavisi od drugačijih činjenica, koji je zastareo, koji je relevantan za konkretan predmet.

## 11. Authority ≠ persuasiveness
Ne svoditi sve izvore na jednu skalu (isti princip kao `15-poredjenje-sudske-prakse` t. 3, AUTHORITY vs FACTUAL SIMILARITY, i `22` §7 hijerarhija izvora) — dobro obrazložena disertacija može imati visoku analitičku vrednost, ali nije sudska odluka; stari podnesak može sadržati odličan argument, ali nije izvor prava; odluka suda može biti autoritativnija, ali činjenično distinguishable.

## 12. Akti i modeli kao "argument mines"
Postojeće akte i modele tretirati kao izvor za RUDARENJE argumenata — pravne teze, kontraargumente, tumačenja, procesne konstrukcije, formulacije zahteva, korišćenu praksu/literaturu, ranije otkrivene slabosti. Ali svaku materijalnu tezu proveriti prema izvorima PRE prihvatanja (v. §11, §5 OFFICE/MODEL POSITION ≠ LAW).

## 13. Outcome feedback
Ako je poznat ishod predmeta u kom je OFFICE POSITION zastupan, evidentirati ga (`accepted`/`rejected`/`not addressed`/`unclear`). Ne zaključivati automatski "sud je dobio spor = svaki argument prihvaćen" — proveriti šta je sud STVARNO prihvatio.

## 14. Source chaining
Kad akt ili literatura upućuju na važnu presudu ili drugi izvor, ne zaustavljati se na sekundarnom navodu: ACT/LITERATURE → CITED SOURCE → ORIGINAL SOURCE → VERIFY → POSITION (isti princip kao `20` odeljak X, PRIMARY > SECONDARY). Akt i literatura tako služe i kao discovery mehanizam za dalje istraživanje.

## 15. Citatna kontrola
Prednost ima TAČNA PARAFRAZA + SOURCE LOCATION, ne dugi citati bez potrebe. Doslovan citat samo kad je sama formulacija pravno značajna. Nikad navodnici oko parafraze.

## 16. Vremenska kontrola
Za svaki stav proveriti: CURRENT / HISTORICAL / POTENTIALLY OUTDATED / SUPERSEDED (isti princip kao `19` t. 11, Temporal control, i `23-legal-system-governor` t. 4A). Stari akt/model može biti koristan za argumentaciju, ali pravni stav mora biti proveren prema SADA važećem režimu.

## 17. Primena na konkretan predmet
Ako se analiza odnosi na konkretan predmet, posle sinteze stavova dodati odeljak "PRIMENA NA KONKRETAN PREDMET" — razdvojiti SOURCE POSITION od APPLICATION TO OUR FACTS: koje odlučne činjenice odgovaraju, koje se razlikuju, koji stav je primenljiv, koji je distinguishable, najjači argument, najveći rizik.

## Integracija sa drugim skill-ovima
- **`22-legal-knowledge-retriever`** odgovara na "ŠTA IMAMO?" (pronalazi korpus) — ovaj skill (24) odgovara na "KOJE STAVOVE taj materijal sadrži i kako se odnose?" (izvlači i sintetiše). Ne duplirati retrieval ako je korpus već pouzdano identifikovan.
- **`17-case-law-analyzer`** utvrđuje šta presuda STVARNO kaže — rezultat se koristi kao COURT POSITION. Ako nema pouzdane analize važne presude, pozvati `17` pre finalne sinteze.
- **`15-poredjenje-sudske-prakse`** utvrđuje PRIMENLJIVOST stava na konkretan predmet — ovaj skill ne sme sam zaključiti da je pronađen stav primenljiv samo zato što postoji; to ide kroz `15`.
- **`18-devils-advocate`** posle POSITION MAP-a i preliminarne sinteze proverava: da li je zanemaren suprotan stav; da li je literatura selektivno korišćena; da li je OFFICE POSITION nekritički prihvaćen; da li je presuda distinguishable; da li postoji drugačije tumačenje. Sinteza se revidira ako nalaz to zahteva (isti REVISION LOOP kao `19` t. 13-14).
- **`21-legal-model-builder`** kad pravi model sa pravnom argumentacijom, koristi POSITION SYNTHESIS umesto da se osloni samo na stari akt: ISSUE → `22` → `24` (ovaj skill) → po potrebi `17`/`15` → `21` → `18` → finalni model.
- **`23-legal-system-governor`**: ne menjati VERIFIED ISSUE synthesis samo zato što je pronađen nov OFFICE POSITION ili MODEL POSITION — označiti **KNOWLEDGE UPDATE CANDIDATE** i proslediti pod pravilima `23` t. 10, ne ažurirati direktno.

## 18. Provenance
Minimalan lanac: POSITION → SOURCE → LOCATION. Poželjno: POSITION → SOURCE → PAGE/SECTION → ORIGINAL FILE → ISSUE. Ako provenance nije moguće utvrditi — smanjiti RELIABILITY, ne prećutati.

## 19. Pravilo kvaliteta analize
Dobra analiza ne odgovara samo "Šta je pravo?", nego i "Ko je o ovom pitanju šta rekao, na osnovu čega, gde se stavovi slažu, gde se razilaze, i koji je najbolje potkrepljen za konkretan slučaj?"

## 20. Pravilo finalnog output-a
Relevantne stavove iz akata/modela/literature NE prećutkivati u ozbiljnoj finalnoj analizi. Istovremeno, ne unositi nebitne stavove samo zato što su pronađeni — kriterijum je **MATERIAL RELEVANCE TO LEGAL ISSUE**.

## 21. Osnovno razgraničenje (nikad ne mešati u jednu neodređenu kategoriju "pravni stav")
PROPIS KAŽE → normative rule. SUD JE ZAUZEO STAV → court position. AUTOR SMATRA → scholarly position. U RANIJEM AKTU JE ZASTUPANO → office position. MODEL POLAZI OD → model position. IZ CELINE IZVORA PROIZLAZI → synthesis (AI).

## Krajnji cilj
Cilj nije da sistem samo PRONAĐE dokument. Cilj je da iz raspoloživog znanja rekonstruiše: LEGAL ISSUE → POSITIONS → AUTORI/SUDOVI/AKTI/MODELI → RAZLOZI → PODRŠKA → SUPROTSTAVLJANJE → KONFLIKT → PRIMENA → SINTEZA. Konačna analiza treba da pokaže ne samo zaključak, nego i intelektualnu mapu pravnog pitanja koja do tog zaključka vodi.
