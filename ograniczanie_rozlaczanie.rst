Zarządzanie połączeniami użytkowników
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Autor: Piotr Mikołajczyk

Oprócz sytuacji, gdy trzeba zamknąć dostęp do bazy danych na czas konserwacji, połączenia użytkowników należy ograniczyć także wtedy, gdy sesja użytkownika została zawieszona lub zbyt wiele połączeń skutkuje nadmiernym zużyciem pamięci i mocy obliczeniowej, uniemożliwiając nawiązywanie nowych połączeń i spowolniając działanie serwera.

Ograniczanie użytkowników
^^^^^^^^^^^^^^^^^^^^^^^^^

Istnieje kilka sposobów ograniczenia dostępu użytkownika:

- Odebranie użytkownikowi prawa dostępu do bazy:

	.. code-block:: sql

		REVOKE CONNECT ON DATABASE baza FROM user;

- Limit liczby jednoczesnych połączeń:

	.. code-block:: sql

		ALTER ROLE user CONNECTION LIMIT 3;

Ręczne rozłączanie użytkowników
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Według nazwy danego użytkownika:

	.. code-block:: sql

		SELECT pg_terminate_backend(pid)
		FROM pg_stat_activity
		WHERE usename = 'user';

Według PID (np. 12340):

	.. code-block:: sql

		SELECT pg_terminate_backend(12340);

Automatyczne rozłączanie użytkowników
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sesja użytkownika lub jego zapytania mogą zostać rozłączone automatycznie, jeśli wprowadzimy pewne ograniczenia czasowe:

- Rozłączenie sesji po przekroczeniu limitu czasu bezczynności podczas zapytania:

	- dla bieżącej sesji:

		.. code-block:: sql

			SET idle_in_transaction_session_timeout = '5min';

	- dla danego użytkownika:

		.. code-block:: sql

			ALTER ROLE user SET idle_in_transaction_session_timeout = '5min';

- Limit czasu zapytania:

	.. code-block:: sql

		ALTER ROLE user SET statement_timeout = '30s';

Zapobieganie nowym połączeniom
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zablokowanie logowania konkretnego użytkownika:

	.. code-block:: sql

		ALTER ROLE user NOLOGIN;

	Odblokowanie:

	.. code-block:: sql

		ALTER ROLE user LOGIN;

Blokowanie nowych połączeń do bazy danych:

	.. code-block:: sql

		REVOKE CONNECT ON DATABASE baza FROM PUBLIC;
	
	PUBLIC oznacza wszystkich użytkowników. Nadal połączeni użytkownicy nie są rozłączani.

