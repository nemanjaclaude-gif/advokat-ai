# MODEL: Zahtev za oglašavanje presude pravnosnažnom i izvršnom

**Tip modela**: BASE_MODEL (kratka varijanta) + MODULE (dodatak za punu varijantu) | **Status**: VERIFIED (generalizovano iz 3 stvarna, redovno korišćena podneska) | **Datum kreiranja**: 31.8.2026 | **Pravni režim**: ZPP (pravnosnažnost/izvršnost presude)

Popuniti [zagrade]; ukloniti napomene u *kurzivu* pre upotrebe.

---

## CORE (kratka varijanta — dovoljna kad presuda ima jednostavnu izreku i broj predmeta je već poznat sudu iz zaglavlja)

[Назив суда]                                                              [број предмета]
[адреса суда]

Тужилац/Тужиља: [Име и презиме], из [место], Ул. [адреса], кога/коју заступа адвокат [име] из [место], Ул. [адреса], по приложеном пуномоћју

Тужени: „[НАЗИВ]“ DOO, из [место], Ул. [адреса], МБ: [број], ПИБ: [број], којег заступа директор [име]

ЗАХТЕВ ЗА ОГЛАШАВАЊЕ

Тражимо од суда да огласи правноснажном и извршном пресуду овог суда, [OPTIONAL: донету] у предмету [OPTIONAL: под наведеним бројем / број [број предмета]].

У [место], дана [датум]. године                                    Пуномоћник тужиоца/тужиље,
                                                                       _________________________
                                                                       Адвокат [име]

---

## OPTIONAL MODULE — puna varijanta (kad presuda ima VIŠE stavova izreke, ili kad se od suda traži da se prvo prisetimo tačne sadržine pre same molbe — korisno ako je od presude prošlo dosta vremena, ili se šalje sudu koji nije isti kao onaj koji je sudio pa nije "pri ruci" spis)

[Назив суда]                                                              [број предмета]
[адреса суда]

Тужилац/Тужиља: [Име и презиме], из [место], Ул. [адреса], ЈМБГ [ЈМБГ — ako se koristi u ovom sudu/predmetu], коју/кога заступа адвокат [име] из [место], Ул. [адреса], по приложеном пуномоћју

Тужени: „[НАЗИВ]“ DOO, из [место], Ул. [адреса], МБ: [број], ПИБ: [број], којег заступа директор [име]

ПОДНЕСАК ТУЖИОЦА/ТУЖИЉЕ

Пресудом [број предмета], од дана [датум], ставом [број]. изреке, усвојен је захтев тужиоца/тужиље, и обавезан тужени да тужиоцу/тужиљи исплати износ од [износ] динара са законском затезном каматом, почев од дана [датум], па све до коначне исплате, све у року од 8 дана од дана пријема писменог отправка пресуде, под претњом принудног извршења, [OPTIONAL: а ставом [број]. усвојен је захтев тужиоца/тужиље, и обавезан тужени да тужиоцу/тужиљи исплати износ од [износ] динара [опис — нпр. "на име накнаде штете"] са законском затезном каматом, почев од дана [датум], па све до коначне исплате, у истом року,] [OPTIONAL: а ставом [број]. обавезан тужени да тужиоцу/тужиљи исплати износ од [износ] динара [опис — нпр. "на име трошкова поступка"], у року од 8 дана од дана пријема писменог отправка пресуде, под претњом принудног извршења].

У складу са напред наведеним, тражимо од суда да Пресуду [број предмета], од дана [датум], огласи правноснажном и извршном.

У [место], дана [датум]. године                                    Пуномоћник тужиоца/тужиље,
                                                                       _________________________
                                                                       Адвокат [име]

---

## Kontrolna lista pre upotrebe
- [ ] Proveriti da li je presuda STVARNO pravnosnažna (protekao rok za žalbu bez izjavljene žalbe, ILI odluka po žalbi potvrđena) — ovaj zahtev ne pokreće ispitivanje pravnosnažnosti, PRETPOSTAVLJA je
- [ ] Odlučiti između CORE (kratka) i OPTIONAL MODULE (puna) varijante — puna je bezbednija kad ima više stavova izreke ili je prošlo više vremena
- [ ] Ako se prepisuje izreka (puna varijanta), prepisati je VERNO iz same presude, ne parafrazirati ako je precizna formulacija bitna za dalje izvršenje
- [ ] Proveriti tačan naziv/adresu suda (posebno ako je predmet u međuvremenu menjao sud ili sudsko odeljenje)

## MODEL_SOURCE_NOTE
*Napomena o pristupu izvorima: po `13-anonimizacija` (odeljak ROUTING), identitet klijenata iz izvornih predmeta NIJE naveden ovde — samo broj predmeta, dovoljno za internu sledljivost bez otkrivanja identiteta stranke u modelu.*
- **Korišćeni stvarni dokumenti (interna sledljivost, bez identiteta klijenta)**: predmet 76 П-22027/19 (23.10.2020, kratka varijanta); predmet П-9801/2020 (8.7.2024, kratka varijanta); predmet 15 П-4505/2021 (13.6.2022, puna varijanta sa prepisanom izrekom u 3 stava).
- **Propisi**: ZPP (odredbe o pravnosnažnosti/izvršnosti presude — tačan član NIJE nezavisno pribavljen u ovoj sesiji, sami izvorni dokumenti ga ne citiraju eksplicitno).
- **Šta je preuzeto kao strukturni princip**: dve varijante (kratka/puna) su STVARNO korišćene u različitim situacijama u istoj kancelariji (birane, ne slučajne) — model ih objedinjuje kao CORE + OPTIONAL MODULE.
- **Šta je novo sintetizovano**: eksplicitna kontrolna lista (izvorni dokumenti je nisu imali) i jasno razdvajanje kad koristiti koju varijantu.
- **Datum provere izvora**: 31.8.2026.
