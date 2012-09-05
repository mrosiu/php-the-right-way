---
title: Filtrowanie danych
isChild: true
---

## Filtrowanie danych

Nigdy, przenigdy nie ufaj zewnętrznym danym wprowadzonym do Twojego kodu. Zawsze waliduj i zabezpieczaj je przed
użyciem. Możesz użyć do tego funkcji `filter_var()` i `filter_input()`, które pomagają w tych czynnościach. Potrafią
przykładowo w prosty sposób sprawdzić poprawność składniową wprowadzego przez użytkownika adresu e-mail.

Zewnętrzne dane mogą znaleźć się wszędzie: głównym ich źródłem sa tablice `$_GET` i `$_POST` zawierająca parametry
żądania, niektóre wartości w tablicy `$_SERVER` które pochodzą wprost z nagłówków, które wysyła użytkownik, czy
`fopen('php://input', 'r')` - ciało żądania HTTP. Pamiętaj, że zewnętrzne dane, to nie tylko dane z formularzy
wysłanych przez uzytkownika. Pliki, które ściągasz, dane sesji, ciasteczka, czy nawet dane z zewnętrznych
webservice'ów powinny być traktowane jako dane, którym nie można ufać.

While foreign data can be stored, combined, and accessed later, it is still foreign input. Every
time you process, output, concatenate, or include data in your code, ask yourself if
the data is filtered properly and can it be trusted.

Data may be _filtered_ differently based on its purpose. For example, when unfiltered foreign input is passed
into HTML page output, it can execute HTML and JavaScript on your site! This is known as Cross-Site
Scripting (XSS) and can be a very dangerous attack. One way to avoid XSS is to sanitize all HTML tags
in the input by removing tags or escaping them into HTML entities.

Another example is passing options to be executed on the command line. This can be extremely dangerous
(and is usually a bad idea), but you can use the built-in `escapeshellarg` function to sanitize the executed
command's arguments.

One last example is accepting foreign input to determine a file to load from the filesystem. This can be exploited by
changing the filename to a file path. You need to remove "/", "../", [null bytes][6], or other characters from the file path so it can't
load hidden, non-public, or sensitive files.

* [Learn about data filtering][1]
* [Learn about `filter_var`][4]
* [Learn about `filter_input`][5]
* [Learn about handling null bytes][6]

### Escaping

Sanitization removes (or escapes) illegal or unsafe characters from foreign input.

For example, you should sanitize foreign input before including the input in HTML or inserting it
into a raw SQL query. When you use bound parameters with [PDO](#databases), it will
sanitize the input for you.

Sometimes it is required to allow some safe HTML tags in the input when including it in the HTML
page. This is very hard to do and many avoid it by using other more restricted formatting like
Markdown or BBCode, although whitelisting libraries like [HTML Purifier][html-purifier] exists for
this reason.

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
