# ADVOKAT-AI — STARTER

Ovo je početna struktura za AI podršku advokatskoj kancelariji.

## Cilj
Ne praviti jedan veliki prompt, već odvojiti:
- PREDMETE — konkretna dokumentacija;
- SKILLS — metodologije rada;
- TAKSONOMIJU — pravne oblasti/deskriptore;
- OBRASCE — strukture akata i analiza;
- IZVORE — propise i proverenu praksu;
- OUTPUT — radne rezultate.

## Preporučeni početak
1. Kopiraj dokumentaciju jednog dobro poznatog predmeta u `01_PREDMETI/TEST-01/00_ULAZNI_DOKUMENTI/`.
2. Popuni `CASE.md` samo poznatim osnovnim podacima.
3. AI-u zadaj da prvo pročita `02_SKILLS/19-legal-research-orchestrator/SKILL.md` (meta-skill koji bira koje druge skill-ove aktivirati i kojim redosledom — za jednostavan, brz start dovoljan je i direktno `02_SKILLS/01-analiza-predmeta/SKILL.md`).
4. Ne dozvoli pisanje tužbe dok nisu završeni intake, činjenice, dokazi i pravna pitanja.
5. Svaki put kada AI napravi sistemsku grešku, unapredi odgovarajući SKILL, a ne samo pojedinačni prompt.

## Važno
Primeri su šabloni. Ne sadrže pravne zaključke za konkretan predmet.
