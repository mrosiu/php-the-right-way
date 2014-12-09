---
title: Composer i Packagist
isChild: true
---

## Composer i Packagist {#composer_and_packagist_title}

Composer jest **genialnym** systemem wspomagającym zarządzanie zależnościami aplikacji w PHP. Wystarczy jeżeli
wylistujesz swoje zależności w pliku `composer.json`, a narzędzie to, przy użyciu kilku prostych poleceń, automagicznie
ściągnie odpowiednie wersje bibliotek i ich zależności oraz odpowiednio skonfiguruje autoloadera.

Za pomocą Composera można zainstalować wiele znanych bibliotek. Ich listę znajdziesz na stronie projektu [Packagist][1]
- oficjalnego repozytorium bibliotek kompatybilnych z tym systemem.

### Instalacja Composera

Composera możesz zainstalować lokalnie (w katalogu Twojego projektu) lub globalnie (np. w /usr/local/bin). Aby móc użyć
tego narzędzia, wejdź do jego katalogu swojego projektu i wydaj polecenie:

    curl -s https://getcomposer.org/installer | php

Polecenie to ściągnie do bieżącego katalogu plik `composer.phar`, który będziesz mógł uruchomić za pomocą PHP, aby
zarządzać zależnościami. Pamiętaj, że przekierowanie zawartości strony bezpośrednio do interpretera PHP może nie być
bezpieczne - przed wykonaniem tego polecenia zapoznaj się z kodem znajdującym się pod adresem
http://getcomposer.org/installer.

Aby zainstalować Composera dla wszystkich użytkowników, wystarczy jeżeli przeniesiesz ściągnięty plik `composer.phar`
do współdzielonego katalogu, np. `/usr/local/bin`, zmieniając jego nazwę na `composer`
(`sudo mv composer.phar /usr/local/bin/composer`).

### Ręczna instalacja Composera

Ręczna instalacja Composera jest bardziej skomplikowanym procesem, gdyż sam musisz sprawdzić swój system, aby
upewnić się, że spełnia on wymagania stawiane przez tę aplikację. Instalacja automatyczna sprawdza:
- czy używasz odpowiedniej wersji PHP,
- czy rozszerzenie phar jest zainstalowane,
- czy uprawnienia do katalogów są odpowiednie,
- czy nie zostały zainstalowane problematyczne rozszerzenia PHP,
- oraz czy plik `php.ini` zawiera odpowiednie ustawienia.

Aby pobrać Composera ręcznie, wykonaj następujące polecenia:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Ścieżka `$HOME/local/bin` (lub dowolna inna którą wybierzesz) powinna znajdować się w zmiennej środowiskowej $PATH,
dzięki czemu będziesz miał możliwość skorzystania z polecenia `composer` zamiast `php composer.phar`.

### Jak definiować i instalować zależności

Najpierw stwórz plik `composer.json` w katalogu głównym swojego projektu i umieść w nim odpowiednie wpisy. Poniższy
przykład demonstruje jak przy użyciu Composera zainstalować projekt [Twig][2]. W pliku `composer.json` umieść poniższą
zawartość:

	{
	    "require": {
	        "twig/twig": "1.8.*"
	    }
	}

A następnie, będąc w tym samym katalogu, uruchom poniższe polecenie:

    php composer.phar install

Efektem działania będzie ściągnięcie odpowiedniej wersji projektu Twig do katalogu `vendors/` oraz odpowiednie
skonfigurowanie autoloadera. Aby z niego skorzystać, musisz dołączyć plik `vendor/autoload.php` do swojego skryptu: 

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Od teraz możesz korzystać z klas dostarczonych przez bibliotekę.

* [Dokumentacja projektu Composer][3]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: http://getcomposer.org/doc/00-intro.md
