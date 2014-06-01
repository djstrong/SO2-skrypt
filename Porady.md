# Porady

Zamieszczone są tutaj ogólne porady, niezwiązane z konkretnym laboratorium.

### Czytamy wszystkie komunikaty wypisywane na ekran

Komunikaty wskazują potencjalne błędy lub upewniają nas o poprawnym wykonaniu polecenia.

```
$ git clone repozytorium1 repozytorium2
Cloning into 'repozytorium2'...
warning: You appear to have cloned an empty repository.
done.
```
### Orientujemy się w jakiej lokalizacji wykonujemy polecenia

Aktualna lokalizacja jest podawana przed znakiem zachęty:

* `student@laboratorium:/$` - korzeń
* `student@laboratorium:~$` - katalog domowy użytkownika `student`
* `student@laboratorium:/home$` - katalog `/home`, to nie jest katalog domowy
* `student@laboratorium:~/public_html$` - katalog `public_html` w katalogu domowym użytkownika `student`

Bezwzględną ścieżkę, w której obecnie jesteśmy możemy poznać używając polecenia `pwd` (_print working directory_):

```
student@laboratorium:~/public_html$ pwd
/home/stduent/public_html
```

### Korzystamy z tabulatora

Tabulator podpowiada nam lub uzupełnia polecenia (w szczególności ścieżki), które wpisujemy.

1. Wpisujemy `vim /e` i naciskamy tabulator. Ścieżka zostaje uzupełniona: `vim /etc/`.
2. Dopisujemy `my` (`vim /etc/my`) i naciskamy tabulator. Ścieżka zostaje uzupełniona: `vim /etc/mysql/`.
3. Naciskamy dwkrotnie tabulator. Otrzymujemy podpowiedzi (nazwy plików w tym katalogu): `conf.d/       debian.cnf    debian-start  my.cnf`.

### Upewniamy się czy polecenie dało porządany efekt

Np. usuwając katalog `rm -r katalog`, sprawdzamy czy faktycznie go nie ma:

* `ls` - szukamy czy jest na liście
* `ls katalog` - wygodniej, lista może być długa; już podczas wpisywania, tabulator nie powinien podpowiadać nazwy `katalog`

### Nie korzystamy z Ctrl+Z

`Ctrl+Z` zatrzymuje aktualny proces - można go wznowić używając `jobs`, `fg` i `bg`. Proces taki nie jest zakańczany (zabijany) i może blokować pewne operacje. Np. zatrzymanie poleceń `git` (w szczególności `commit`) uniemożliwi wykonywanie kolejnych na tym repozytorium.

### Restartowanie usług i sprawdzanie statusu

Status usługi sprawdzamy poleceniem: `sudo service nazwa_usługi status`.

Restartujemy usługę za pomocą analogicznego polecenia ze zmienioną komendą, np. `sudo service apache2 restart`. Restartowanie usług za pomocą `/etc/init.d/nazwa_usługi restart` jest starszym sposobem i mniej uniwersalnym.

### Użytkownicy systemowi i baz danych MySQL są niezależni



## Dodatkowe

### Dodatkowe terminale

W środowisku graficznym możemy otworzyć nowe terminale lub zakładki. W przypadku braku środowiska graficznego kolejne terminale są dostępne przez kombinację `Alt+F1-F6` (dodatkowo `Ctrl` jeśli chcemy się przełączyć ze środowiska graficznego; `Alt+F7` powraca do środowiska graficznego). Konsola dostępna pod `Alt+F1` jest domyślną.
