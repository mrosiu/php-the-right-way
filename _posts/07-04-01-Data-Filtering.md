---
title: Filtrowanie danych
isChild: true
---

## Filtrowanie danych

Nigdy, przenigdy nie ufaj zewnętrznym danym wprowadzonym do Twojego kodu. Zawsze waliduj i zabezpieczaj je przed
użyciem. Możesz użyć do tego funkcji `filter_var()` i `filter_input()`, które pomagają w tych czynnościach - potrafią
przykładowo w prosty sposób sprawdzić poprawność składniową wprowadzego przez użytkownika adresu e-mail.

Zewnętrzne dane mogą znaleźć się wszędzie: głównym ich źródłem sa tablice `$_GET` i `$_POST` zawierające parametry
żądania. Niektóre wartości w tablicy `$_SERVER` pochodzą wprost z nagłówków, które wysyła użytkownik, czy
`fopen('php://input', 'r')` - ciało żądania HTTP. Pamiętaj, że zewnętrzne dane to nie tylko dane z formularzy
wysłanych przez uzytkownika. Pliki, które ściągasz, dane sesji, ciasteczka, czy nawet dane z zewnętrznych
webservice'ów powinny być traktowane jako dane, którym nie można ufać.

Z uwagi na to, że zewnętrzne dane mogą być przechowywane w bazach danych, należy pamiętać o tym, żeby przy ich odczycie
również zadbać o ich zabezpieczenie. Za każdym razem, gdy próbujesz użyć takich danych zadaj sobie pytanie, czy są one
odpowiednio zabezpieczone i czy można im ufać.

Sposób zabezpieczania zewnętrznych danych zależy od sposobu ich użycia. Przykładowo gdy chcesz użyć danych pochodzących
od użytkownika w HTML'u, musisz zadbać o usunięcie bądź zamianę znaczników sterujących, takich jak '<', '>' na
odpowiednie encje HTML, gdyż w przeciwnym razie odpowiednio spreparowany ciąg znaków może uruchomic skrypt JS, co może
być bardzo opłakane w skutkach - może przykładowo pomóc w przejęciu sesji użytkownika. Taki rodzaj ataku to XSS
(Cross-Site Scripting).

Innym przykładem jest przekazywanie danych od użytkownika jako fragment lub całość komendy do wykonania z poziomu linii
poleceń. Nieodpowiednie zabezpieczenie takich danych przed użyciem w ten sposób może doprowadzić do wykonania
niepożądanego polecenia, co może być poważnym zagrożeniemn bezpieczeństwa aplikacji i/lub systemu na którym ona działa.
Aby bezpiecznie przekazać takie dane do wiersza poleceń, zabezpiecz je za pomocą funkcji `escapeshellarg()`.

Niebezpieczeństwo może czyhać również tam, gdzie za pomocą danych z zewnątrz ustalasz ścieżkę w systemie plików.
Atakujący może wykorzystać to poprzez odpowiednią zmianę przekazanych wartości. Twoja aplikacja wczyta wtedy inny plik
niż powinna, co może spowodować wyciek prywatnych danych lub pomóc w przeprowadzeniu innego ataku. Aby zabezpieczyć się
przed tym, usuwaj "/", ".." i tzw. "[null bytes][6]" ze zmiennych przy użyciu których ustalasz ścieżkę pliku do
wczytania.

* [Dowiedz się więcej na temat filtrowania danych][1]
* [Dowiedz się więcej na temat funkcji `filter_var()`][4]
* [Dowiedz się więcej na temat funkcji `filter_input()`][5]
* [Dowiedz się więcej na temat "null bytes"][6]

### Zabezpieczanie danych z zewnątrz (escaping)

Dane pochodzące z zewnątrz mogą posiadać niebezpieczne znaki. Aby bezpiecznie się nimi posługiwać w aplikacji (np. aby
bezpiecznie skorzystać z danych wejściowych w HTML'u bądź zapytaniu SQL), należy się ich pozbyć. Proces ten nazywany
jest escapingiem.

W przypadku zapytań SQL najlepszym sposobem na automatyczne zabezpieczenie się przez niebezpiecznymi znakami jest
użycie PDO, które zrobi to za Ciebie. Jeżeli chodzi o HTML, częstym wyzwaniem jest konieczność dopuszczenia kilku
wybranych tagów, aby umożliwić użytkownikowi proste formatowanie wpisanego tekstu. W takim przypadku jednym z wyjść
jest użycie formatowania Markdown lub BBCode, bądź bibliotek takich jak [HTML Purifier][html-purifier].

[Lista filtrów escape'ujących][2]

### Walidacja

Dzięki walidacji możesz upewnić się, że wprowadzone przez użytkownika dane są tym, czego się spodziewasz. Dobrym
przykładem jest walidacja danych takich jak adres e-mail, numer telefonu, czy wiek, wprowadzonych w formularzu
rejestracji.

[Lista filtrów walidujących][3]

[1]: http://www.php.net/manual/pl/book.filter.php
[2]: http://www.php.net/manual/pl/filter.filters.sanitize.php
[3]: http://www.php.net/manual/pl/filter.filters.validate.php
[4]: http://php.net/manual/pl/function.filter-var.php
[5]: http://www.php.net/manual/pl/function.filter-input.php
[6]: http://php.net/manual/pl/security.filesystem.nullbytes.php
[html-purifier]: http://htmlpurifier.org/
