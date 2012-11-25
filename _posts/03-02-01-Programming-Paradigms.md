---
title: Paradygmaty programowania w PHP
isChild: true
---

## Paradygmaty programowania w PHP {#programming_paradigms_title}

PHP jest językiem, w którym możesz programować na wiele sposobów. Przez ostatnie lata mocno rozwinął swoje możliwości.
W wersji 5.0 (2004) dodano zupełnie nowy model programowania obiektowego, w 5.3 (2009) wprowadzono m.in. [anonimowe
funkcje][anonymous-functions] i [przestrzenie nazw][namespaces], a w 5.4 (2012) - [traity][traits].

### Programowanie obiektowe

PHP posiada rozbudowany model programowania obiektowego, który obsługuje m.in klasy, klasy abstrakcyjne, interfejsy,
dziedziczenie, konstruktory, klonowanie, czy wyjątki.

* [Czytaj dalej na temat programowania obiektowego][oop]
* [Dowiedz się więcej na temat traitów][traits]

### Programowanie funkcyjne

PHP od wersji 5.3 wspiera możliwość przypisania funkcji do zmiennej - są to tzw. funkcje anonimowe lub closure'y.
Zarówno funkcje wbudowane, jak i te stworzone przez programistę, mogą być dzięki temu wywołane w sposób dynamiczny,
przekazane jako argumenty wywołania innych funkcji lub nawet przez nie zwracane.

Funkcje mogą także wywoływać same siebie, czyli działać rekurencyjnie.

W PHP 5.4 dodano możliwość przypisania closure'a do zakresu obiektu w taki sposób, że mogą one być stosowane zamiennie
z funkcjami anonimowymi praktycznie w każdej sytuacji.

* Dowiedz sie więcej o [programowaniu funkcyjnym w PHP](/pages/Functional-Programming.html)
* [Artykuł o funkcjach anonimowych][anonymous-functions]
* [Artykuł o klasach typu closure][closure-class]
* [Więcej szczegółów znajdziesz w Closures RFC][closures-rfc]
* [Artykuł o Callables][callables]
* [Artykuł o dynamicznym wywoływaniu funkcji przy użyciu `call_user_func_array`][call-user-func-array]

### Metaprogramowanie

PHP wspiera metaprogramowanie udostępniając mechanizmy takie jak Reflection API i magiczne metody - m.in. `__get()`,
`__set()`, `__call()`, `__callStatic()`, `__clone()`, `__toString()` i `__invoke()`, które umożliwiają programiście
wywołanie danego kodu podczas konkretnych zdarzeń w cyklu życia obiektu.

* [Artykuł o Reflection API][reflection]
* [Artykuł o magicznych metodach][magic-methods]

[namespaces]: http://php.net/manual/pl/language.namespaces.php
[overloading]: http://uk.php.net/manual/pl/language.oop5.overloading.php
[oop]: http://www.php.net/manual/pl/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/pl/functions.anonymous.php
[closure-class]: http://php.net/manual/pl/class.closure.php
[callables]: http://php.net/manual/pl/language.types.callable.php
[magic-methods]: http://php.net/manual/pl/language.oop5.magic.php
[reflection]: http://www.php.net/manual/pl/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/pl/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
