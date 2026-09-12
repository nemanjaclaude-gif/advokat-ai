---
name: devils-advocate
description: DEVILS_ADVOCATE — napada postojeću pravnu analizu kao inteligentan, dobro pripremljen protivnik, umesto da je potvrđuje. Dublja, potpunija verzija `08-adversarial-review` (koji ostaje za brzu, laku proveru nacrta) — koristiti OVAJ skill kad postoji puna CASE MAP (`16-case-extractor`) i PRAVNA-ANALIZA.md, i kad je ishod predmeta dovoljno važan da opravda potpun red-team prolaz, uključujući eksplicitnu proveru confirmation bias-a i simulaciju sudijinog rezonovanja.
---

# DEVILS_ADVOCATE

Zadatak NIJE da se potvrdi postojeća analiza. Zadatak je da se NAPADNE kao inteligentan i dobro pripremljen protivnik. Cilj: pronaći razlog zbog kog je zaključak POGREŠAN, NEPOTPUN ili PRETERANO SAMOUVEREN.

**Ulaz (strukturiran, po `20-legal-knowledge-record-standard`)**: `_AI/CASE_RECORD.md` konkretnog predmeta; predloženi zaključak (iz `PRAVNA-ANALIZA.md`/`_AI/ANALIZA.md`); relevantni `JUDGMENT_RECORD` zapisi (`05_IZVORi/SUDSKA-PRAKSA/_ANALIZE/` i/ili CASE CARD-ovi); relevantni `ISSUE_RECORD` zapisi (`03_TAKSONOMIJA/PRAVNA-PITANJA/`); literatura (`SCHOLARSHIP_RECORD` ako postoji); dokazna mapa (`_AI/DOKAZNA_MAPA.md`).

**Podela odgovornosti**: ovaj skill SAMO napada postojeći zaključak — ne rekonstruiše predmet (`16`), ne analizira odluke iznova u dubinu (`17`), ne poredi presedane (`15`, mada koristi njihov rezultat kao ulaz). **Rezultat DEVILS_ADVOCATE se NE prihvata automatski kao tačan** — on je NAPAD koji `19-legal-research-orchestrator` mora ponovo proveriti (v. taj skill, REVISION LOOP) pre nego što izmeni konačan zaključak.

## 1. Provera činjenične osnove
Za svaki važan zaključak: Na kojoj konkretnoj činjenici počiva? Da li je ta činjenica STVARNO dokazana? Razlikovati: tvrdnju; dokaz; indiciju; nespornu činjenicu; utvrđenu činjenicu; PRETPOSTAVKU ANALITIČARA (ovo poslednje je najopasnije — sopstvena pretpostavka koja se prišunjala kao da je činjenica).

## 2. Napad na dokaze
Za svaki ključni dokaz tražiti: problem autentičnosti; problem relevantnosti; problem dokazne snage; protivrečan dokaz; drugačije moguće tumačenje; činjenicu koju dokaz NE dokazuje. Pitanje: *"Da li iz ovog dokaza zaista sledi ono što analiza tvrdi?"*

## 3. Napad na pravnu kvalifikaciju
Proveriti: da li je primenjen pravi propis; vremensko važenje propisa; lex specialis; prelazne odredbe; procesne pretpostavke; aktivnu i pasivnu legitimaciju; nadležnost; rokove; zastarelost; prekluziju; teret dokazivanja.

## 4. Napad na sudsku praksu
Za svaku ključnu odluku: da li je činjenično ZAISTA analogna; da li analiza koristi ratio ili samo POGODNU rečenicu (izvučenu iz konteksta); da li postoji distinguishing; da li je odluka kasnije prevaziđena; da li postoji suprotna praksa; da li je odluka nižeg suda suprotna stavu višeg suda.

## 5. Napad na literaturu
Proveriti da li analiza: predstavlja stav autora kao pozitivno pravo; zanemaruje suprotan doktrinarni stav; koristi zastareo rad; prenosi zaključak autora van konteksta; zanemaruje da je autor kritikovao baš tu sudsku praksu koju analiza koristi.

## 6. Confirmation bias
Proveriti da li je analiza: tražila SAMO praksu koja podržava željeni ishod; zanemarila nepovoljne činjenice; strože tretirala protivne nego povoljne izvore; pretvorila MOGUĆ zaključak u SIGURAN zaključak. Ako postoji — označiti: **CONFIRMATION BIAS RISK**.

## 7. Najjači argument protivnika
Ne praviti slab/veštački kontraargument (strawman). Formulisati NAJJAČU razumnu verziju argumenta protivne strane (steelman).

## 8. Simulacija sudije
Pitanje: *"Koji je najjednostavniji, pravno održiv razlog zbog kog bi sud mogao odbiti našu tezu?"* Formulisati taj razlog kao da se piše obrazloženje presude protiv nas.

## 9. Kritična tačka predmeta (CASE PIVOT)
Identifikovati 1-3 činjenice ili pravna pitanja od kojih ishod NAJVIŠE zavisi. Za svaki **CASE PIVOT** objasniti: šta trenutno znamo; šta ne znamo; ko snosi teret dokazivanja; šta bi promenilo ishod.

## 10. Šta treba popraviti
Za svaku pronađenu slabost predložiti: dodatni dokaz; dodatno istraživanje; drugačiju argumentaciju; distinguishing; rezervni pravni osnov; procesnu radnju.

## 11. Završni RED TEAM REPORT
- **Najslabija tačka naše pozicije**
- **Najjači argument protivne strane**
- **Najopasnija suprotna sudska praksa**
- **Najbolji distinguishing protiv naše prakse**
- **Problemi sa dokazima**
- **Problemi sa pravnom kvalifikacijom**
- **CASE PIVOTS**
- **Šta nedostaje**
- **Kako ojačati poziciju**
- **Ocena**: **ROBUST** (analiza izdržava napad) / **DEFENSIBLE** (postoje slabosti, ali je pozicija dobro odbranjiva) / **VULNERABLE** (postoji značajan rizik) / **CRITICAL** (osnovna teza počiva na ozbiljnoj činjeničnoj ili pravnoj slabosti).

**Ne birati ocenu prema željenom ishodu predmeta.**

## Odnos prema `08-adversarial-review`
`08-adversarial-review` ostaje kao BRZA provera nacrta (nadležnost/legitimacija/dopuštenost/zastarelost/petitum, rizik CRITICAL-LOW) — dovoljna za rutinske akte. Koristiti OVAJ, dublji skill kad: (a) postoji puna CASE MAP i pravna analiza (ne samo nacrt akta), (b) predmet je dovoljno važan/sporan da opravda pun red-team prolaz sa eksplicitnom proverom confirmation bias-a i simulacijom sudije, (c) korisnik ili predmet to izričito traže ("oceni žalbu", "koja je najjača protivargumentacija"). Rezultat (RED TEAM REPORT) ide u `01_RADNI_MATERIJALI/` konkretnog predmeta, kao zaseban odeljak ili fajl — ne u `02_OUTPUT/` (v. `14-usavrsavanje-obrazaca`, isto pravilo razdvajanja analize od gotovog akta).
