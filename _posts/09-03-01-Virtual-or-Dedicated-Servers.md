---
title: Serwery wirtualne lub dedykowane
isChild: true
---

## Serwery wirtualne lub dedykowane {#virtual_or_dedicated_servers_title}

Jeżeli potrafisz administrować serwerem bądź planujesz naukę w tym kierunku, zainteresuj się serwerami wirtualnymi.
Dzięki nim masz możliwość skonfigurowania każdego detalu swojego środowiska produkcyjnego.

### nginx i PHP-FPM

PHP potrafi dobrze współdziałać z serwerem [nginx](http://nginx.org) przy użyciu wbudowanego managera procesów FastCGI
(FPM). Nginx jest lekkim i szybkim serwerem WWW, który zużywa znacznie mniej zasobów maszyny niż Apache, przez co
potrafi obsłużyć więcej jednoczesnych procesów.

* [Czytaj dalej o serwerze nginx](http://nginx.org)
* [Czytaj dalej o PHP-FPM](http://php.net/manual/en/install.fpm.php)
* [Jak bezpiecznie skonfigurować PHP i nginx](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache i PHP

PHP i Apache mają za sobą długą historię. Serwer ten cechuje się łatwą, a zarazem dość obszerną konfiguracją, a także
posiada wiele [modułów](http://httpd.apache.org/docs/2.4/mod/) rozszerzających jego możliwości. Na serwerach
hostingowych jest często wybierany jako platforma pod popularne aplikacje open-source (np. Wordpress), czy aplikacje
bazujące na frameworkach. Apache jednakowoż podczas pracy zużywa więcej zasobów serwera, przez co nie może obsłużyć tak
wielu jednoczesnych połączeń, jak jego konkurent, nginx.

Istnieje kilka możliwości zainstalowania PHP na serwerze Apache. Najczęstszym wyborem jest
[prefork MPM](http://httpd.apache.org/docs/2.4/mod/prefork.html) (od Multi-Processing Modules) i moduł mod_php5. Jest
to najszybszy sposób, który wymaga relatywnie niewielkiego nakładu pracy administracyjnej i jest najlepszym podejściem
dla osób, które wolą ten czas przeznaczyć na kodowanie. Minusem jest fakt, że mod_php5 zużywa więecj zasobów, co może
wpłynąć na szybkość działania.

Jeżeli chcesz wycisnąć z Apache'a nieco więcej szybkości oraz stabilności działania, możesz użyć tego samego systemu
FPM, który współdziała z serwerem nginx i uruchomić mpm_worker (http://httpd.apache.org/docs/2.4/mod/worker.html)
lub [mpm_event](http://httpd.apache.org/docs/2.4/mod/event.html) z mod_fastcgi lub mod_fcgid. Aplikacje uruchomione w
takiej konfiguracji będą działać szybciej, ale jej instalacja będzie wymagała większego nakładu pracy.

* [Czytaj o serwerze Apache](http://httpd.apache.org/)
* [Czytaj o Multi-Processing Modules](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [Czytaj o mod_fastcgi](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [Czytaj o mod_fcgid](http://httpd.apache.org/mod_fcgid/)
