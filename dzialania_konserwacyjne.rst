Planowanie konserwacji bazy danych
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Konserwację bazy danych należy przeprowadzać regularnie, np. co tydzień lub co miesiąc. Nie powinna mieć miejsca w godzinach szczytu. Przeprowadzenie konserwacji może również okazać się koniecznie po wykryciu błędu lub wystąpieniu awarii.

Konserwacja może obejmować m.in. zmianę parametrów konfiguracji bazy, przeprowadzenie procesu VACUUM, zmianę uprawnien użytkowników, aktualizacje systemowe i wykonanie backupów lub przywrócenie danych.

Działanie te muszą zostać przeprowadzone w czasie, gdy mamy pewność, że żaden klient nie będzie podłączony, nie będą przeprowadzane żadne transakcje. Użytkownicy powinni być uprzednio poinformowani o czasie przeprowadzenia konserwacji. Mimo to, należy wcześniej sprawdzić, czy nie ma aktywnych sesji.

Uruchamianie, zatrzymywanie i restartowanie serwera bazy danych
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Autor: Piotr Mikołajczyk

Działania, takie jak aktualizacja oprogramowania, instalacja rozszerzeń, wprowadzenie pewnych zmian w plikach konfiguracyjnych, migracja danych, wykonanie backupów bazy, wymagają zrestartowania, zatrzymania bądź ponownego uruchomienia serwera bazy danych.

Uruchamianie
^^^^^^^^^^^^

Linux:

.. code-block:: bash

	sudo systemctl start postgresql

Windows CMD:

.. code-block:: batch

	net start postgresql-x64-15


Windows PowerShell

.. code-block:: powershell

	Start-Service -Name postgresql-x64-15

Zatrzymywanie
^^^^^^^^^^^^^

Linux:

.. code-block:: bash

	sudo systemctl stop postgresql

Windows CMD:

.. code-block:: batch

	net stop postgresql-x64-15


Windows PowerShell

.. code-block:: powershell

	Stop-Service -Name postgresql-x64-15

Restartowanie
^^^^^^^^^^^^^

Linux:

.. code-block:: bash

	sudo systemctl restart postgresql

W CMD nie istnieje osobne polecenie restartowania. Należy zatrzymać serwer, a następnie uruchomić go ponownie.

Windows PowerShell

.. code-block:: powershell

	Restart-Service -Name postgresql-x64-15

Polecenia CMD mogą zostać również użyte w PowerShell.
