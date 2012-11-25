---
title: Raportowanie błędów
isChild: true
---

## Raportowanie błędów

Wyświetlanie błędów jest pomocne przy szukaniu problematycznych miejsc w Twojej aplikacji, ale ma jeden poważny minus:
eksponuje systemowe, być może kluczowe z punktu widzenia bezpieczeństwa, informacje całemu światu. Pamiętaj o tym, że
środowisko produkcyjne (live) powinno być skonfigurowane pod tym względem inaczej niż deweloperskie. 

### Środowisko deweloperskie

W środowisku <strong>deweloperskim</strong> lub <strong>testowym</strong> wyświetlanie komunikatów błędów może być
przydatne podczas śledzenia problemów z aplikacją. W tym środowisku powinieneś skonfigurować raportowanie błędów w ten
sposób:

- display_errors: On
- error_reporting: E_ALL
- log_errors: On

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