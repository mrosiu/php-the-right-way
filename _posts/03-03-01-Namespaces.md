---
title: Przestrzenie nazw
isChild: true
---

## Przestrzenie nazw

Jak wspomniano wcześniej, społeczność PHP jest tworzona przez niezliczoną ilość programistów. Powoduje to, że może
zdarzyć się sytuacja w której dwie rózne biblioteki używają klasy o takiej samej nazwie. W takim przypadku pojawi się
problem.

Naprzeciw temu problemowi wychodzą _przestrzenie nazw_, których działanie można porównać z funkcją katalogów w systemie
plików. Tak samo jak dwa pliki o tej samej nazwie mogą istnieć w dwóch różnych katalogach, klasy o takich samych
nazwach mogą istnieć w różnych przestrzeniach nazw.

Z tego powodu istotne jest, aby Twój kod był przypisany do wałsnej przestrzni nazw, aby jego elementy (klasy, funkcje,
czy stałe nie kolidowały z klasami biblitek, których używasz.

Dokument [PSR-0][psr0] omawia jak powinieneś stosować przestrzenie nazw, aby zabezpieczyć się przez takimi problemami.

* [Więcej informacji o przestrzeniach nazw][namespaces]

[namespaces]: http://php.net/manual/pl/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
