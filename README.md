# Giorgio da Paluzza: a relational database of notarial registers

*Baza podatkov o notarskih dokumentih notarja Giorgia da Paluzza*

This repository publishes the database I designed and programmed for the
notarial registers of Giorgio da Paluzza, notary in San Daniele del Friuli,
together with the 2013 presentation of the project. Starting from this
application, the repository develops a relational data model based on the
FAIR principles and on current methods for the digital processing of
medieval notarial sources.

## The manuscripts

The registers survive in three volumes of the Fondo Fontanini, Biblioteca
Civica Guarneriana, San Daniele del Friuli:

| Volume | Shelfmarks | Registers | Status |
|---|---|---|---|
| Cod. 38 | Font. LXV / Mazzatinti 252-1 | 1383, 1384, 1388, 1389, 1391 | edited (Brunettin 2017) |
| Cod. 39 | Font. LXVI / Mazzatinti 252-2 | 1390, 1383 | unpublished |
| Cod. 40 | Font. LXVII / Mazzatinti 252-3 | 1392–1394, 1396, 1398, 1399 | unpublished |

The database also contains 73 acts drawn up by the same notary and preserved
in "Volume E" of the parchment collection of the Archivio Capitolare di Udine.

## The database

`database/Notai2013-11.mdb` is a Microsoft Access 2000–2003 application
(Jet 4). The table `Atto` holds 406 records: 331 acts from Cod. 38, 73 from
Volume E and 2 incomplete entries. Each act records year, month, day and
indiction, place of redaction, type of act, archival location and the full
Latin text.

Authority tables describe places (`Luogo`, 199 records), persons
(`PersoneN`, 113), types of act (`TipoAtto`, 102), professions, titles,
saints' days used in dating clauses and units of measure. A second group of
tables (sale, debt, lease, donation, apprenticeship, boundaries, clauses)
breaks the act down according to the scheme of Rolandino Passeggeri, which
separates the *publicationes* from the *negocii tenor*. These tables are
designed but still empty.

Relationships live in the application layer: 46 forms, 8 reports,
149 saved queries and the VBA code that drives them. The schema itself
declares almost no foreign keys; the forms and the joins in the queries
enforce them. A copy of the file without the embedded manuscript images is
published here.

## From the 2013 application to a FAIR data model

1. Export every table to UTF-8 CSV (`data/csv/`).
2. Write a data dictionary and an explicit schema with declared primary and
   foreign keys, reconstructed from the query joins and the VBA code.
3. Normalise controlled vocabularies (act types are currently recorded in
   mixed forms, e.g. `Debitum` / `DEBITUM`).
4. Add ISO 8601 dates next to the original dating elements.
5. Assign stable identifiers to acts, persons and places.

## Repository contents

- `database/` – the Access application (images removed)
- `data/csv/` – open export of all tables
- `presentation/` – the 2013 presentation (PDF)

## Credits

Database design and programming: Massimo Sbarbaro (ZRS Koper, ALDHI;
ORCID [0009-0006-8965-9013](https://orcid.org/0009-0006-8965-9013)).
Transcriptions of all acts, from Cod. 38 and from Volume E: Giordano
Brunettin (ORCID [0009-0001-1689-7815](https://orcid.org/0009-0001-1689-7815)).

Brunettin, Giordano. *I registri notarili di Giorgio da Paluzza. Anni 1388,
1383, 1384, 1389, 1391 (Fondo Fontanini LXV – Cod. 38)*. Quaderno
Guarneriano, n.s., 8. Cormons: Poligrafiche San Marco, 2017.

## Licence and citation

Database structure, application code, analytical data and documentation are
released under CC BY 4.0 (see `LICENSE`).

The Latin texts in the field `Regesto` (tables `Atto` and `AttoOld`) are
transcriptions by Giordano Brunettin and are excluded from the CC BY 4.0
licence. Full texts by Giordano Brunettin: reuse on request / pending
agreement. The Cod. 38 texts are also published in his 2017 edition,
available on the website of the
[Biblioteca Civica Guarneriana](https://www.guarneriana.it).

To cite this repository, see `CITATION.cff`.
