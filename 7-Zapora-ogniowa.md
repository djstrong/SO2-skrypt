#Lab 7 – Zapora ogniowa
Zapora sieciowa polega na odpowiednim wykorzystaniu iptables. Jeżeli nie mamy iptables instalujemy za pomocą apt-get. Do wykonania punktu w niniejszym labolatorium dotyczącego logów programu warto od razu zainstalować syslog-ng. Później gdy np. zablokujemy sobie połączenia wychodzące i przychodzące może to być niemożliwe.
Kiedy już uda się zainstalować sysloga. Otwieramy plik /etc/syslog-ng/syslog-ng.conf i w nim dopisujemy:
``` 
destination iptables {file("/var/log/syslog");};
```
W ten sposób mamy już zainstalowany pakiet iptables oraz logi iptables w pliku systemowym.
Aby udostępnić ruch przychodzący z loopback należy wpisać
```
~$ sudo iptables -A INPUT -i lo -j ACCEPT
```
Blokujemy cały ruch przychodzący i ustawiamy możliwość logowania przez ssh z hosta:
```
~$ sudo iptables -P INPUT DROP
~$ sudo iptables -A INPUT -s iphosta -p tcp --dport 22 -j ACCEPT
```
Aby sprawdzić czy działa tak jak powinno możemy spróbować się zalogować z hosta i z innego komputera, używając ssh. Logowanie powinno być możliwe z hosta i niemożliwe z innego komputera.
Kolejnym krokiem jest zablokowanie ruchu wychodzacego na localhost na porcie 80. Jako, że nasza domyślna polityka dla ruchu wychodzącego jest accept. To musimy tylko zablokować ruch dla localhosta. Robimy to analogicznie, a więc:
```
~$ sudo iptables -A OUTPUT -s localhost -p tcp --dport 80 -j DROP  #wymaga potwierdzenia
```
Forwardowanie przy użyciu ssh: 
```
ssh -L 8080:ip_virtual:80 nazwa_hosta #nazwą hosta może być względnie IP - wymaga potwierdzenia
```
