---
name: pravna-analiza
description: Primena proverenog prava na utvrđene činjenice predmeta.
---

# PRAVNA ANALIZA

Za svako ključno pitanje koristi:
ISSUE
RULE
AUTHORITIES
FACTS
APPLICATION
COUNTERARGUMENT
CONCLUSION

Jasno razdvoji činjenicu, izvor prava, argument i zaključak.

## Obavezna dopuna: sudska praksa
Za AUTHORITIES svakog ključnog pravnog pitanja, uvek pokreni skill `05-sudska-praksa` — obavezna provera baze Vrhovnog suda (vrh.sud.rs, `court_type=sc&matter=19`, v. taj skill za tačan obrazac pretrage) ciljanom pretragom po ključnom pojmu/institutu pitanja koje se analizira, ne samo oslanjanje na već poznate/citirane odluke. Svaku stvarno korišćenu odluku svesti na CASE CARD i status VERIFIED/UNVERIFIED po tom skillu, uključujući obaveznu potragu za nepovoljnim odlukama.

## Obavezna dopuna: teorijska analiza
Pre zaključivanja analize, uvek pokreni skillove `10-teorijska-analiza` i `11-strucni-clanci` — proveri i, gde je moguće, potkrepi (ili osporeni) zaključak kroz doktorske disertacije (`05_IZVORI/LITERATURA/`) i stručne članke iz tri određena pravna časopisa (`05_IZVORI/CASOPISI/`). Nalaz uneti u zaseban odeljak `## TEORIJSKA POTKREPLJENOST (LITERATURA)` po formatu iz ta dva skilla, jasno razdvojen po izvoru (disertacija vs. članak). Doktrina ne zamenjuje RULE/AUTHORITIES iz zakona i prakse — dopunjuje ih.
