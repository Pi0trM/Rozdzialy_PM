Działania konserwacyjne
~~~~~~~~~~~~~~~~~~~~~~~

Autor: Piotr Mikołajczyk

Uruchamianie, zatrzymywanie i restartowanie serwera bazy danych należy wcześniej zaplanować. Działanie te muszą zostać przeprowadzone w czasie, gdy mamy pewność, że żaden klient nie będzie podłączony, nie będą przeprowadzane żadne transakcje. Użytkownicy powinni być uprzednio poinformowani o czasie przeprowadzenia konserwacji. Mimo to, należy wcześniej sprawdzić, czy nie ma aktywnych sesji.

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
