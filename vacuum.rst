Proces VACUUM
~~~~~~~~~~~~~

Autor: Piotr Mikołajczyk

DELETE nie usuwa rekordów z tabeli, jedynie oznacza je jako martwe. Podobnie UPDATE pozostawia stare wersje zaktualizowanych wierszy.

Proces VACUUM przeszukuje tabele i indeksy, szukając martwych wierszy, które można fizycznie usunąć lub oznaczyć do nadpisania.

Może zostać przeprowadzony na kilka sposobów:
.. code-block:: sql
	VACUUM;

Usuwa martwe wiersze, ale nie odzyskuje miejsca z dysku, a jedynie udostępnia je dla przyszłych danych,
.. code-block:: sql
	VACUUM FULL;

Kompaktuje tabelę do nowego pliku, zwalnia miejsce w pamięci,
.. code-block:: sql
	VACUUM ANALYZE

Usuwa martwe wiersze i przeprowadza aktualizację statystyk, nie odzyskuje miejsca.

Autovacuum
^^^^^^^^^^

Autovacuum działa w tle, automatycznie wykonując VACUUM na odpowiednich tabelach. Dzięki niemu nie trzeba ręcznie uruchamiać VACUUM po każdej modyfikacji tabeli.
