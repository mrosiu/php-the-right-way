---
title: Przestrzenie nazw
isChild: true
---

## Przestrzenie nazw {#namespaces_title}

Jak wspomniano wcześniej, społeczność PHP jest tworzona przez niezliczoną ilość programistów. Powoduje to, że może
zdarzyć się sytuacja, w której dwie różne biblioteki użyją klasy o takiej samej nazwie. W takim przypadku pojawi się
problem.

Naprzeciw temu problemowi wychodzą _przestrzenie nazw_, których działanie można porównać z funkcją katalogów w systemie
plików. Tak samo jak dwa pliki o tej samej nazwie mogą istnieć w dwóch różnych katalogach, klasy o takich samych
nazwach mogą istnieć w różnych przestrzeniach nazw.

Z tego powodu istotne jest, aby Twój kod był przypisany do własnej przestrzeni nazw. Dzięki temu jego elementy (klasy,
funkcje, czy stałe) nie będą kolidowały z klasami bibliotek, których używasz. Traktuje o tym dokument [PSR-0][psr0].

W grudniu 2013 roku PHP-FIG przygotowało kolejny standard: [PSR-4][psr4], który pewnego dnia zastąpi standard [PSR-0][psr0].

* [Więcej informacji o przestrzeniach nazw][namespaces]

[namespaces]: http://php.net/manual/pl/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
