<strong>Uwaga: Napisany program nie zachowuje dobrych praktyk programistycznych w jezyku Java. Jest to wykonane
specjalnie by narzędzia używane w ćwiczeniu mogły się wykazać. Autor zaznacza, że większość kodu została zainspirowana "złym" (z punktu widzenia stylu i konwencji) kodem
z Internetu.</strong>

<h1>Zad 1</h1>
<p>Wynik wykonania komendy <strong>spotless:check</strong> został przedstawiony na zrzucie ekranu</p>
<img src="/zrzuty/a.jpg"/>

Jak widać w projekcie algorytmów sortowania (specjalnie napisanych w złym "stylu") mamy pełno 
ostrzeżeń odnośnie stylu w pliku Main.java. Przy pomocy uruchomienia komenty <strong>mvn spotless:apply </strong>
można owe problemy ze stylem usunąć co autor uczynił.

Jeśli chodzi o zapis <strong>@@ -33,7 +33,6 @@</strong> bądź (ze zrzutu ekranu  <strong>@@ -42,53 +36,49 @@</strong>)
jest zapisany w formacie jaki wyświetla się również np. w narzędziu Git. Ma on format @@ from-file-range to-file-range @@.
from-file-range składa się z <start-line>, <number-of-lines> oraz to-file-range <start_line>, <number_of_lines>. Jeśli <number_of_lines>
się nie wyswietla to oznacza, że jest równy zero. Znak minusa mówi o "starym pliku" natomiast "+" o nowym pliku. W kontekście narzędzia spotless
oznacza to różnicę między plikiem analizowanym i tym, który powstanie po uruchomieniu <strong>mvn spotless:apply</strong> a więc "poprawnym" ze względu
na zdefiniowane reguły.

<strong>mvn spotless:apply</strong>
<img src="zrzuty/2.JPG"/>

Różnice pokazane przy pomocy Diff:

<img src="zrzuty/3.JPG"/>
<img src="zrzuty/4.JPG"/>
<img src="zrzuty/5.JPG"/>

Jak widać różnice polegały głównie na znakach spacji oraz przeniesieniu znaków '{' do tych samych linijek, w których znajdują się np. instrukcje for.
Wyrównano również np. znaki komentarzy blokowych '/*'.
<h1>Zad 2</h1>


<h1> Zad 3 </h1>

Spotless używa UTF-8 domyślnie. Po zmianie na Cp1252. Zatem teraz będziemy używać Windowsowych znaków końca linii. Oczwyiście plik Main.java został
taki sam jak przed każdym z punktów tzn. nie jest on wynikiem wykonania np. komendy mvn spotless:apply.

Po samej zmianie:
<img src="Zrzuty/6.JPG"/>

Jak widać plik ma kodowanie UNIXOWE końca linii. Narzędzie spotless się "zgubiło" i nie mogło odczytać końcówek linii poprawnie stąd odczytało część pliku jako jedną linię.
Zmieniamy znak końca linii w konfiguracji i otrzymujemy poprawny wynik: 

<img src="Zrzuty/7.JPG"/>

