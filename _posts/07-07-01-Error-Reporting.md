---
title: Raportowanie błędów
isChild: true
---

## Raportowanie błędów {#error_reporting_title}

Wyświetlanie błędów jest pomocne przy szukaniu problematycznych miejsc w Twojej aplikacji, ale ma jeden poważny minus:
eksponuje systemowe, być może kluczowe z punktu widzenia bezpieczeństwa, informacje całemu światu. Pamiętaj o tym, że
środowisko produkcyjne (live) powinno być skonfigurowane pod tym względem inaczej niż deweloperskie. 

### Środowisko deweloperskie

W środowisku <strong>deweloperskim</strong> lub <strong>testowym</strong> wyświetlanie komunikatów błędów może być
przydatne podczas śledzenia problemów z aplikacją. W tym środowisku powinieneś skonfigurować raportowanie błędów w ten
sposób:

- display_errors: On
- error_reporting: -1
- log_errors: On

Za [php.net](http://pl1.php.net/manual/pl/function.error-reporting.php):

> Passing in the value -1 will show every possible error, even when new levels and constants are added in future PHP versions. The E_ALL constant also behaves this way as of PHP 5.4.

Poziom raportowania `E_STRICT` jest dostępny od wersji 5.3.0 nie będąc częścią poziomu `E_ALL`. W wersji 5.4.0
zmieniono to zachowanie i `E_STRICT` jest częścią `E_ALL`. Co oznacza to dla programisty? To, że jeżeli potrzebuje
wyświetlać wszystkie możliwe błędy w 5.3.0, należy użyć wartości `-1` lub `E_ALL | E_STRICT`.

Podsumowując:

* dla PHP &lt; 5.3 - `-1` lub `E_ALL`
* dla PHP = 5.3 - `-1` lub `E_ALL | E_STRICT`
* dla PHP &gt; 5.3 - `-1` lub `E_ALL`

### Środowisko produkcyjne

W środowisku <strong>produkcyjnym</strong> wszystkie błędy powinny być ukryte i logowane do zewnętrznego pliku. W tym
środowisku powinieneś skonfigurować raportowanie błędów w ten sposób: 

- display_errors: Off
- error_reporting: E_ALL
- log_errors: On

Aby uzyskać więcej informacji na temat funkcji kontrolujących sposób raportowania błędów, zajrzyj do manuala:

* [Error_reporting](http://www.php.net/manual/pl/errorfunc.configuration.php#ini.error-reporting)
* [Display_errors](http://www.php.net/manual/pl/errorfunc.configuration.php#ini.display-errors)
* [Log_errors](http://www.php.net/manual/pl/errorfunc.configuration.php#ini.log-errors)