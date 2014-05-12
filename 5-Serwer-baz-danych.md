#Lab 5 – Serwer baz danych
Zmiana nazwy serwera to po prostu podmienienie nazwy w pliku /etc/hostname - należy pamiętać o otwarciu z prawem edycji (sudo).
Druga zmiana w pliku /etc/hosts polega na podmienieniu nazwy przy odpowiednim adresie IP 127.0.0.1.
Kolejny krok to instalacja serwera mysql. Pakiet który potrzebujemy to mysql-server, można zainstalować również mysql-client.
Co ciekawe to polecenie możemy wykonać w jednej linii:    
```~$ sudo apt-get install mysql-client mysql-server ```   
Warto od razu ustawić hasło na root dla użytkownika root
Później należy zmienić ścieżkę, tak aby dane były przechowywane w /var/lib/mysql. Interesujący nas plik to /etc/mysql/my.cnf. Tak się składa, ze ta ścieżka jest ścieżką domyślną dla mysql, więc nie musimy nic zmieniać.

#####Uruchomienie, restart serwera. Hasło root'a.
Używamy do tego sudo service i kolejno start, restart, ew jeżeli chcemy zatrzymać proces to podajemy stop.
Jeżeli ktoś przeoczył punkt, w którym mowa aby ustawić hasło root'a na root już przy instalacji może użyć następujących komend:
```
~$ mysqladmin -u root password HASLO_DO_MYSQL_DLA_ROOT'a #jeżeli nie ustawiliśmy hasła
~$ mysqladmin -u root -p password NOWE_HASLO_DlA_ROOT'a #jeżeli hasło zostało ustawione na złe
```

#####Jak już mamy uruchomiony serwer, to możemy się zalogować na roota i wykonać kolejne polecenia.
```
mysql> CREATE USER 'nazwa_uzytkownika' IDENTIFIED BY 'haslo'; #dodanie użytkownika z hasłem
mysql> CREATE DATABASE IF NOT EXISTS `nazwa_bazy_danych`; #dodanie bazy danych
mysql> GRANT ALL PRIVILEGES ON ‚baza_danych’.* TO ‚uzytkownik’; #dodanie praw do bazy dla użytkownika
mysql> DROP DATABASE nazwa_bazy;
#Ważne!
#Należy pamiętać, aby nazwa użytkownika i hasło były w pojedynczym apostrofie, a nazwa bazy danych w "ząbku"(klawisz tyldy bez shift)
```

Przy opracowaniu wykorzystano materiały publicznie dostępne na stronach:
* http://locahost.net/porada/96/jak-zmienic-haslo-root-w-mysql-w-systemie-linux
* http://dziorki.wordpress.com/2009/05/25/dodawanie-nowego-uzytkownika-do-bazy-mysql/
