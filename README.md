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
2. Import data using `psql`.

## How to Generate These Files

Use `org.soluvas.sanad.cli.qurandatabase.ImportQuranDatabase` from https://github.com/soluvas/sanad project.
