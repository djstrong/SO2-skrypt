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
Blokujemy cały ruch przychodzący na TCP i ustawiamy możliwość logowania przez ssh z hosta:
```
~$ sudo iptables -A INPUT -p tcp -j DROP
~$ sudo iptables -A INPUT -s iphosta -p tcp --dport 22 -j ACCEPT
```
Aby sprawdzić czy działa tak jak powinno możemy spróbować się zalogować z hosta i z innego komputera, używając ssh. Logowanie powinno być możliwe z hosta i niemożliwe z innego komputera.
Zablokowanie ruchu wychodzącego na tcp dla portu 80 i wszystkich hostów oprócz localhosta:
```
~$ sudo iptables -A OUTPUT -p tcp --dport 80 -j DROP
~$ sudo iptables -A OUTPUT -d localhost -p tcp --dport 80 -j ACCEPT
```
Forwardowanie przy użyciu ssh: 
```
ssh -L 8080:ip_virtual:80 nazwa_hosta #wymaga potwierdzenia
```
