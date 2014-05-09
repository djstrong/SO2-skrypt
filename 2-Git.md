#Lab 2 - Git
Instalacja gita za pomocą apt-get:    
``` ~$ sudo apt-get install git ```    
> Jeżeli ktoś ma ochotę wiedzieć więcej lub woli zainstalować git'a ze źródeł odsyłam na [stronę gita.](http://git-scm.com/book/pl/Pierwsze-kroki-Instalacja-Git)   

Konfiguracja polega na przedstawieniu się gitowi:
```
***** na hoście:
~$ git config --global user.name "Imię Nazwisko"
~$ git config --global user.email imie.nazwisko@host.com
***** na maszynie wirtualnej:
~$ git config --global user.name "Imię Nazwisko"
~$ git config --global user.email imie.nazwisko@virtual.com
```
Oraz pokolorowaniu składni:    
```
***** na hoście i virtualu:
~$ git config --global color.ui true
````    
więcej na [stronie gita.](http://git-scm.com/book/pl/Dostosowywanie-Gita-Konfiguracja-Gita)    
Tworzymy katalog projektowy poleceniem mkdir, przechodzimy do niego i zakładamy repozytorium git'a.
```
~$ mkdir /home/nazwisko/project
~$ cd /home/nazwisko/project
~$ git init
```   
Teraz naszym zadaniem jest utworzenie pliku data.txt zawierającego imię i nazwisko, dodanie go do repozytorium, i commit:
```
~$ echo "Imię Nazwisko" >> data.txt
~$ git add *    lub   ~$ git add data.txt      **** pierwsze polecenie doda wszystkie pliki, a drugie tylko ten który nas interesuje
~$ git commit -m "Dodano plik data.txt"          **** jeśli mamy ciekawszy pomysł na treść commitu to do dzieła
```    
