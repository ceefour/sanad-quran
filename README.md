sanad-quran
===========

Holy Quran SQL database dump for use with Sanad.
Compiled by [Hendy Irawan](http://www.hendyirawan.com/).

Source: [QuranDatabase.org](http://qurandatabase.org/)

Quran Database XML files signed by [Hendy Irawan](http://www.hendyirawan.com)
using Hendy Irawan <ceefour666@gmail.com> [key 5A9AC703](https://keyserver.pgp.com/vkd/DownloadKey.event?keyid=0xFEDB960B5A9AC703) 
are available at https://github.com/ceefour/qurandatabase

## Usage

1. Create the necessary tables using https://github.com/soluvas/sanad SQL schema migration tools.
2. Import data using `psql` and `COPY` command.

## How to Generate These Files

1. Prepare Quran Database files from [QuranDatabase.org](http://qurandatabase.org/) or https://github.com/ceefour/qurandatabase
2. Use `org.soluvas.sanad.cli.qurandatabase.ImportQuranDatabase` from https://github.com/soluvas/sanad project.
3. Dump from PostgreSQL:

		psql -hlocalhost -Upostgres sanad_sanad_dev

		COPY (SELECT * FROM sanad.quranchapter) TO '/tmp/quranchapter.tsv';
		COPY (SELECT * FROM sanad.quranverse) TO '/tmp/quranverse.tsv';
		COPY (SELECT * FROM sanad.literal WHERE id LIKE 'quran%') TO '/tmp/literal-quran.tsv';
		COPY (SELECT * FROM sanad.transliteration WHERE id LIKE 'quran%') TO '/tmp/transliteration-quran.tsv';
		COPY (SELECT * FROM sanad.spellingproperty WHERE id LIKE 'quran%') TO '/tmp/spellingproperty-quran.tsv';
		COPY (SELECT * FROM sanad.authenticityproperty WHERE id LIKE 'quran%') TO '/tmp/authenticityproperty-quran.tsv';
		COPY (SELECT * FROM sanad.successionproperty WHERE id LIKE 'quran%') TO '/tmp/successionproperty-quran.tsv';

		cp -v /tmp/quran*.tsv /tmp/*-quran.tsv ~/git/sanad-quran/
		