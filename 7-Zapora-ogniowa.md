#Lab 7 – Zapora ogniowa
Zapora sieciowa polega na odpowiednim wykorzystaniu iptables. Jeżeli nie mamy iptables instalujemy za pomocą apt-get. Do wykonania punktu w niniejszym labolatorium dotyczącego logów programu warto od razu zainstalować syslog-ng. Później gdy np. zablokujemy sobie połączenia wychodzące i przychodzące może to być niemożliwe.
Kiedy już uda się zainstalować sysloga. Otwieramy plik /etc/syslog-ng/syslog-ng.conf i w nim dopisujemy:
``` 
destination iptables {file("/var/log/syslog");};
```
Oraz wprowadzamy informację, żeby zapisywać logi:
```
~$ sudo iptables -A INPUT -j LOG --log-level 7
```
W ten sposób mamy już zainstalowany pakiet iptables oraz logi iptables w pliku systemowym.
Aby udostępnić ruch przychodzący z loopback należy wpisać
```
~$ sudo iptables -A INPUT -i lo -j ACCEPT
```
Blokujemy cały ruch przychodzący na TCP i ustawiamy możliwość logowania przez ssh z hosta:
```
~$ sudo iptables -A INPUT -s iphosta -p tcp --dport 22 -j ACCEPT
~$ sudo iptables -A INPUT -p tcp -j DROP
```
Aby sprawdzić czy działa tak jak powinno możemy spróbować się zalogować z hosta i z innego komputera, używając ssh. Logowanie powinno być możliwe z hosta i niemożliwe z innego komputera.
Zablokowanie ruchu wychodzącego na tcp dla portu 80 i wszystkich hostów oprócz localhosta:
```
~$ sudo iptables -A OUTPUT -d localhost -p tcp --dport 80 -j ACCEPT
~$ sudo iptables -A OUTPUT -p tcp --dport 80 -j DROP
```
Forwardowanie przy użyciu ssh: 
```
~$ ssh -L 8080:localhost:80 ip_virtual
```
Ponieważ forwardowanie to przekierowanie wywołania zapytania na naszym porcie na inny komputer na dowolnym porcie sposób jego wywołania nie jest intuicyjny, albo przynajmniej "nietrywialny". Powyższe polecenie wywołujemy na maszynie hosta. Interesujące jest dla nas aby wywołanie zapytania na port 8080 na hoście przekierowało nas gdzie indziej, tzn. na ip_virtual i tam wywołało zapytanie na domenę localhost na porcie 80.
Tak więc składnia jest następująca:
```
~$ ssh -L port_naszej_maszyny:domena_do_wywołania:port_wywołania ip_gdzie_wywołujemy
```
Przy okazji tego tematu warto znać również poniższe komendy:
```
~$ sudo iptables -L #to polecenie wyświetla aktualny stan naszej tabelki, warto również pamiętać, że w przypadku dwóch pasujących do naszego wpisu zapytań, zostanie wybrane to, które w tabelce znajduje się jako pierwsze. Dlatego KOLEJNOŚĆ wprowadzania powyzszych komend MA ZNACZENIE.
~$ sudo iptables -F #usuwa wszystkie wpisy do tabelek, akcje domyślne dla zapytań są ustawiane na accept
~$ sudo iptables -P INPUT DROP #ustawia domyślną politykę na odrzuć, dla pakietów przychodzących, można zamiast INPUT naturalnie podać FORWARD i OUTPUT, a zamiast DROP - ACCEPT lub REJECT
```
