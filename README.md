<h1>Tomasz Kot 233 978</h1>

<strong>Uwaga: Napisany program nie zachowuje dobrych praktyk programistycznych w jezyku Java. Jest to zabieg celowy
wykonany po to by narzędzia używane w ćwiczeniu mogły się wykazać. Autor zaznacza, że większość kodu została zainspirowana "złym" (z punktu widzenia stylu i konwencji języka Java) kodem
z Internetu. Ponadto sens samej implementacji jest wątpliwy - kod ma służyć tylko zapoznaniu z tematyką Fromatowania kodu w kontekście Tworzenia i utrzymywania czystego kodu, a nie pokazaniu zaawansowanego projektu programistycznego w Javie.</strong>

<h1>Zad 1</h1>
<p>Wynik wykonania komendy <strong>spotless:check</strong> został przedstawiony na zrzucie ekranu poniżej.</p>
<img src="/zrzuty/1.JPG"/>

Jak widać w projekcie algorytmów sortowania mamy pełno 
ostrzeżeń odnośnie stylu w pliku Main.java. Przy pomocy uruchomienia komenty <strong>mvn spotless:apply </strong>
można je usunąc.

Zapis <strong>@@ -33,7 +33,6 @@</strong> bądź (ze zrzutu ekranu  <strong>@@ -42,53 +36,49 @@</strong>)
jest podany w formacie jaki wyświetla się również np. w narzędziu Git. Ma on budowę @@ from-file-range to-file-range @@.
from-file-range składa się z <start-line>, <number-of-lines> oraz to-file-range <start_line>, <number_of_lines>. Jeśli <number_of_lines>
się nie wyswietla to oznacza, że jest on równy zero. Znak minusa mówi o "starym pliku" natomiast "+" o nowym pliku. W kontekście narzędzia spotless
oznacza to różnicę między plikiem analizowanym i tym, który powstanie po uruchomieniu <strong>mvn spotless:apply</strong> a więc "poprawnym" ze względu
na zdefiniowane reguły formatowania.

<strong>mvn spotless:apply</strong> <br/>
<img src="zrzuty/2.JPG"/>

Różnice pokazane przy pomocy Diff:

<img src="zrzuty/3.JPG"/>
<img src="zrzuty/4.JPG"/>
<img src="zrzuty/5.JPG"/>

Jak widać różnice polegały głównie na znakach spacji oraz przeniesieniu znaków '{' do tych samych linijek, w których znajdują się np. instrukcje for.
Wyrównano również np. znaki komentarzy blokowych '/*' - wcięcia.
<h1>Zad 2</h1>

Wyniki wywołania <strong>Reformat Code</strong> dla narzędzia <strong>Google Java Format</strong>

<img src="zrzuty/8.JPG"/>
<img src="zrzuty/9.JPG"/>
<img src="zrzuty/10.JPG"/>

Jak widać narzędzie Google Java Format, podobnie jak spotless, dołączyło wszystkie nawiasy klamrowe do linii, w których wywołana
została odpowiednia instrukcja. Ponadto poprawiło ono wcięcia oraz dodało spacje - np. w instrukcji for pomiędzy poszczególnymi średnikami.
Warto wspomnieć zgodnie z wątkiem na <a href="https://stackoverflow.com/questions/50027892/override-google-java-format-with-spotless-maven-plugin">StackOverflow</a>
że Java Google Formatter nie udostępnia takiej możliwości konfiguracji jak narzędzie spotless.

<h1> Zad 3 </h1>

Spotless używa UTF-8 domyślnie. Po zmianie na Cp1252 będziemy używać np. Windowsowych znaków końca linii. Oczwyiście plik Main.java został taki sam jak przed każdym z punktów tzn. nie jest on wynikiem wykonania np. komendy mvn spotless:apply oraz posiada UNIX-owe znaki końca linii.

Po samej zmianie:
<img src="zrzuty/6.JPG"/>

Narzędzie spotless "zgubiło" się i nie mogło odczytać końcówek linii poprawnie stąd odczytało część pliku Main.java jako jedną linię.
Po zmianie znaku końca linii w konfiguracji i został otrzymany poprawny wynik: 

<img src="zrzuty/7.JPG"/>

<h1>Zad 4</h1>
<strong>Uwaga: Z racji, że "projekt" posiada jedynie jedną klasę jako opis klasy dodano JavaDocs jedynie w pliku Main.java. W punkcie tym sztucznie dodano również pole do klasy Main.java w tym samym celu.</strong>

Zrzut ekranu przedstawiający część dokumentacji napisanej przy pomocy JavaDocs:
<img src="zrzuty/11.JPG" />

Wygenerowana dokumentacja przy pomocy JavaDocs:
<img src="zrzuty/13.JPG" />

Wynik formatowania JavaDocs:
<img src="zrzuty/12.JPG" />

Głównie zostały dodane puste linie pomiędzy głównym opisem danego elementu, a opisem pozostałych parametrów.

<h1>Pytania weryfikacyjne</h1>

<strong>Pytanie 1</strong><br/>
Na sformatowanie automatyczne kodu pozwala plugin <strong>Google Java Formatter</strong>.<br/>
<strong>Pytanie 2</strong><br/>
Dla języka Java - odpowiednio dla Google Java Format jest to <strong>Google Java Style</strong>. Wtyczka spotless również "supportuje" ten styl jednakże (dla języka Java)
dodaje również standard który można określić jako <strong>Eclipse Java Code Formatter</strong> <br/>
<strong>Pytanie 3</strong><br/>
Spośród poznanych wtyczek w ćwiczeniu największą możliwość dostosowania konfiguracji posiada wtyczka Spotless. Dzieje się to poprzez plik XML. <br/>
<strong>Pytanie 4</strong><br/>
Ważne jest by wykonywać automatyczne formatowanie ponieważ jakość (właściwie: czystość) kodu jest czymś o czym łatwo zapomnieć w czasie
rozwiązywania problemu programistycznego. Dzięki automatyzacji tego procesu, chociaż w ograniczym do dokładności działania danego narzędzia zakresie, zadbamy o taką czystość.
Ponadto pluginy często mają zaimplementowane pewne mechanizmy uznane jako "standard" w danej społeczności (ang. style guidelines) - np. Rubocop w języku Ruby. Dzięki temu po pierwsze - mamy możliwość 
ich poznania, a po drugie stosując je uczynimy nasz kod łatwiejszym w cztaniu i utrzymywaniu (a więc i tańszym w eksploatacji :) ) dla innych poprzez stosowanie umownych reguł. Jeśli w danej organizacji obecny jest również pewien <i>standard kodowania</i>
możemy poprzez współdzielony plik konfiguracyjny np. dla Rubocop rubocop.yml udostępnić naszym współpracownikom. Pozwala to szerzyć powszechną automatyzacje dbania o formatowanie w orgazniacji, w której pracujemy. Formatowanie kodu może również automatyzować generacje dokumentacji -np. Javadocs lub YARD dla Ruby.
