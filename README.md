sanad-quran
===========

Holy Quran SQL database dump for use with Sanad.
Compiled by [Hendy Irawan](http://www.hendyirawan.com/).

Source: [QuranDatabase.org](http://qurandatabase.org/)

Quran Database XML files signed by [Hendy Irawan](http://www.hendyirawan.com)
using Hendy Irawan <ceefour666@gmail.com> [key 5A9AC703](https://keyserver.pgp.com/vkd/DownloadKey.event?keyid=0xFEDB960B5A9AC703) 
are available at https://github.com/ceefour/qurandatabase

## Usage

1. Install [PostgreSQL 9.5 or later](http://www.postgresql.org/).
2. Create the necessary tables using https://github.com/soluvas/sanad SQL schema migration tools.
    For PostgreSQL you can quickly use https://github.com/soluvas/sanad/blob/master/export/sanad.schema.sql

3. Import data using `psql` and `COPY` (PostgreSQL server's) or `\copy` (locally) command.

   a. Make sure you've added `C:\Program Files\PostgreSQL\9.5\bin` to your `PATH`.

   b. Run _Command Prompt_.

   c. Change to sanad-quran directory: `cd git\sanad-quran`

   d. Run: `psql -Upostgres sanad_sanad_dev`

   e. Execute these statements inside `psql`:

		\copy sanad.quranchapter from 'quranchapter.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.literal from 'literal-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.quranverse from 'quranverse.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.transliteration from 'transliteration-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.spellingproperty from 'spellingproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.authenticityproperty from 'authenticityproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy sanad.successionproperty from 'successionproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')

## (Hendy's Internal Note) How to Generate DB Files from QuranDatabase.org dataset

1. Prepare Quran Database files from [QuranDatabase.org](http://qurandatabase.org/) or https://github.com/ceefour/qurandatabase
2. Use `org.soluvas.sanad.cli.qurandatabase.ImportQuranDatabase` from https://github.com/soluvas/sanad project.
3. Dump from PostgreSQL:

		psql -hlocalhost -Upostgres sanad_sanad_dev

		\copy sanad.quranchapter to 'quranchapter.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.literal WHERE id LIKE 'quran%') TO 'literal-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.quranverse WHERE id LIKE 'quran%') TO 'quranverse.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.transliteration WHERE id LIKE 'quran%') TO 'transliteration-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.spellingproperty WHERE id LIKE 'quran%') TO 'spellingproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.authenticityproperty WHERE id LIKE 'quran%') TO 'authenticityproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
		\copy (SELECT * FROM sanad.successionproperty WHERE id LIKE 'quran%') TO 'successionproperty-quran.tsv' (format csv, delimiter E'\t', header true, escape E'\\', encoding 'UTF-8')
