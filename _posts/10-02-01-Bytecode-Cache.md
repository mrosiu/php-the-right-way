---
title: Kod bajtowy
isChild: true
---

## Kod bajtowy

Kiedy wykonujemy program napisany w PHP, jego kod źródłowy jest najpierw kompilowany do postaci kodu bajtowego, a
następnie uruchamiany. Jeżeli między kolejnymi uruchomieniami plik z kodem nie zostaje zmodyfikowany, wynikowy kod
bajtowy jest taki sam za każdym razem. Oznacza to, że kolejne jego kompilacje nie są potrzebne i powodują jedynie
niepotrzebnym obciążenie procesora.

Istnieją narzędzia za pomocą których możemy ograniczyć ilość kompilacji zapamiętując wynikowy kod bajtowy, aby kolejne
żądania jego wykonania odbywały się znacznie szybciej. Narzędzia te potrafią drastycznie przyspieszyć działanie
aplikacji, a do tego są bardzo proste w konfiguracji. 

Najbardziej znanymi narzędziami tego typu są:

* [APC](http://php.net/manual/pl/book.apc.php)
* [XCache](http://xcache.lighttpd.net/)
* [Zend Optimizer+](http://www.zend.com/products/server/) (część pakietu Zend Server)
* [WinCache](http://www.iis.net/download/wincacheforphp) (rozszerzenie MS Windows Server)
