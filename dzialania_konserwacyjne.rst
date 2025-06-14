Działania konserwacyjne
~~~~~~~~~~~~~~~~~~~~~~~

Uruchamianie, zatrzymywanie i restartowanie serwera bazy danych należy wcześniej zaplanować. Działanie te muszą zostać przeprowadzone w czasie, gdy mamy pewność, że żaden klient nie będzie podłączony, nie będą przeprowadzane żadne transakcje. Użytkownicy powinni być uprzednio poinformowani o czasie przeprowadzenia konserwacji. Mimo to, należy wcześniej sprawdzić, czy nie ma aktywnych sesji.

Linux
^^^^^

Uruchamianie:
.. code-block:: bash
	
	sudo systemctl start postgresql

Zatrzymywanie:
.. code-block:: bash
	
	sudo systemctl stop postgresql

Restartowanie:
.. code-block:: bash
	
	sudo systemctl restart postgresql


Windows CMD
^^^^^^^^^^^

Uruchamianie:
.. code-block:: batch
	
	net start postgresql-x64-15

Zatrzymywanie:
.. code-block:: batch
	
	net stop postgresql-x64-15

Nie istnieje osobne polecenie dla restartowania. Należy najpierw zatrzymać serwer, a następnie uruchomić go ponownie.

Windows Powershell
^^^^^^^^^^^^^^^^^^

Uruchamianie:
.. code-block:: powershell
	
	Start-Service -Name postgresql-x64-15

Zatrzymywanie:
.. code-block:: powershell
	
	Stop-Service -Name postgresql-x64-15


Restartowanie:
.. code-block:: powershell
	
	Restart-Service -Name postgresql-x64-15

Poza powyższymi, można również korzystać z poleceń dostępnych w PowerShellu.
