Proces VACUUM
~~~~~~~~~~~~~

Autor: Piotr Mikołajczyk

DELETE nie usuwa rekordów z tabeli, jedynie oznacza je jako martwe. Podobnie UPDATE pozostawia stare wersje zaktualizowanych krotek.

Proces VACUUM przeszukuje tabele i indeksy, szukając martwych wierszy, które można fizycznie usunąć lub oznaczyć do nadpisania.

Może zostać przeprowadzony na kilka sposobów:

.. code-block:: sql

	VACUUM;

Usuwa martwe krotki, ale nie odzyskuje miejsca z dysku, a jedynie udostępnia je dla przyszłych danych,

.. code-block:: sql

	VACUUM FULL;

Kompaktuje tabelę do nowego pliku, zwalnia miejsce w pamięci,

.. code-block:: sql

	VACUUM ANALYZE

Usuwa martwe krotki i przeprowadza aktualizację statystyk, nie odzyskuje miejsca.

Autovacuum
^^^^^^^^^^

Autovacuum działa w tle, automatycznie wykonując VACUUM na odpowiednich tabelach. Dzięki niemu nie trzeba ręcznie uruchamiać VACUUM po każdej modyfikacji tabeli. Autovacuum posiada wiele parametrów, od których zależy kiedy wykonany zostanie proces, między innymi:

- autovacuum - parametr logiczny, decyduje, czy serwer będzie uruchamiał launcher procesu autovacuum,

- autovacuum_max_workers - liczba całkowita, określa maksymalną ilość procesów autovacuum mogących działać w tym samym czasie, domyślnie 3,

- autovacuum_vacuum_threshold - liczba całkowita, określa ile wierszy w jednej tabeli musi zostać usunięte lub zmienione, aby wywołano VACUUM, domyślnie 50,

- autovacuum_vacuum_scale_factor - liczba zmiennoprzecinkowa, jaki procent tabeli musi zostać zmieniony aby wywołano VACUUM, domyślna wartość to 0.2 (20%).

Analogiczne parametry warunkują również wywołanie ANALYZE, na przykład autovacuum_analyze_threshold.

Próg uruchamiania VACUUM ustala się wzorem:

	autovacuum_vacuum_threshold + autovacuum_vacuum_scale_factor * liczba_wierszy
	
Podobnie dla ANALYZE:

	autovacuum_analyze_threshold + autovacuum_analyze_scale_factor * liczba_wierszy
