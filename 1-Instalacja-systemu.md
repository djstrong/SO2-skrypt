#Lab 1 – Przygotowanie i uruchomienie ubuntu
Ubuntu jest cudownie prostym w obsłudze i szalenie użytecznym systemem operacyjnym opartym na debianie. Pozwala na zrobienie wszystkiego za pomocą kilku linijek kodu wpisanych do terminala.
#####Pierwsze zajęcia mają dwie części:

1. Przygotowanie virtualboxa do pracy.
2. Zainstalowanie i uruchomienie ubuntu

Virtualbox to narzędzie, które pozwala nam tworzyć sztuczną przestrzeń do uruchamiania innych systemów operacyjnych, bez potrzeby instalowania ich bezpośrednio na dysku naszego komputera.
Oprócz tego możemy łatwo przenosić wirtualne systemy z komputera na inny za pomocą np. pendrive'a.

#####Do dzieła:

Aby wykonać pierwsze kroki wystarczy „przeklikać” się przez konfigurację.
Zaczynamy oczywiście od nowa/new maszyna/machine.
Podajemy wszystkie parametry wg poleceń z laboratorium, problemem może być jedynie typ dysku – tutaj wybieramy vdi.
Przygotowanie virtualboxa polega również na tym, aby w jego ustawieniach zmienić ustawienia karty sieciowej z NAT na połączenie mostkowane bridged. 
Większość osób naprawdę o tym zapomina i jest to źródłem kłopotów niewiadomego pochodzenia.

#####Instalacja systemu:

Drugim krokiem jest instalacja systemu:
Uruchamiamy maszynę i wybieramy napęd (czyli plik .iso z naszym ubuntu).
Wybieramy język, który będzie wygodniejszy - ja polecam angielski. Jego techniczny język może przeszkadzać, ale prawdopobnie szukając rozwiązania naszych problemów w sieci, znajdziemy odpowiedzi właśnie w języku angielskim. Z drugiej jednak strony na potrzeby tego laboatorium doskonale nada się język polski, łatwiej nam też będzie czytać opowiedzi terminala. Wybór należy do ciebie.
Dalej wybieramy lokalizację i układ klawiatury. 

#####Wypełniamy wszystko wg wskazówek:
* hostname: nazwisko małymi literami, bez polskich znaków
* pełna nazwa użytkownika: własne imię i nazwisko
* nazwa użytkownika (login) jak nazwa hosta
* hasło: password
* brak szyfrowania katalogu domowego
* strefa czasowa: Warszawa
* dysk – “Use entire disk/Użycie całego dysku” (bez LVM, czyli pierwsza opcja)
* przy pytaniu o zapisanie zmian na dysku, należy wybrać “yes/tak”

#####Następnie czekamy, aż instalator załaduje pliki.
* brak serwera pośredniczącego/proxy
* brak automatycznej aktualizacji
* brak preinstalowanych składników
* instalacja programu GRUB

Weryfikujemy połączenie z internetem poleceniem ping.   
``` ping 8.8.8.8 ```   
Instalacja demona ssh - klient i serwer. Za pomocą apt-get oczywiście.  
``` sudo apt-get install openssh-client ```   
``` sudo apt-get install openssh-server ```   
Następnie musimy się zalogować - będzie to wytłumaczone tylko tutaj. Ponieważ każdy już 
Na maszynie virtualnej sprawdzamy jeszcze nasz adres ip.
Otwieramy terminal hosta i logujemy
