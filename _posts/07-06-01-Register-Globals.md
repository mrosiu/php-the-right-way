---
title: register_globals
isChild: true
---

## register_globals

<strong>UWAGA:</strong> od wersji PHP 5.4.0 dyrektywa `register_globals` została usunięta i nie ma możliwości
korzystania niej. Jej dostępność w wersjach >= 5.4.0 ogranicza się do wyświetlenia odpowiedniego komunikatu w przypadku
omyłkowego użycia.

W poprzednich wersjach PHP, po włączeniu dyrektywy `register_globals`, zmienne pochodzące od użytkownika (m.in.
`$_POST`, `$_GET` i `$_REQUEST`) były "spłaszczane" do zwykłych zmiennych dostępnych w globalnej zakresie widoczności.
To w łatwy sposób mogło prowadzić do problemów bezpieczeństwa, gdyż aplikacja nie była w stanie stwierdzić skąd
pochodzą wartości poszczególnych zmiennych.

Przykładowo, po włączeniu `register_globals`, zmienna `$_GET['foo']` byłaby dostępna jako $foo, co może nadpisać inną
zmienną $foo i powodować problemy.

Podsumowując, jeżeli używasz PHP < 5.4.0 __upewnij się__, że dyrektywa `register_globals` ma wartość `__off__`.

* [Artykuł na ten temat w manualu](http://www.php.net/manual/pl/security.globals.php)