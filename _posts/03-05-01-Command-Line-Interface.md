---
title: Interfejs CLI
isChild: true
---

## Interfejs CLI (Command Line Interface) {#command_line_interface}

PHP znajduje zastosowanie głównie przy tworzeniu aplikacji webowych, ale może być również użyteczny jako język
skryptowy, uruchamiany z poziomu konsoli. Dzięki temu można łatwo automatyzować typowe zadania, jak testowanie
jednostkowe, proces deploymentu, czy administrację aplikacją.

Skrypty uruchamiane z poziomu konsoli mają dostęp do całego kodu Twojej aplikacji i mogą go uruchamiać w ten sam
sposób jak w przypadku wywołania z poziomu serwera WWW. Pamiętaj, aby nie umieszczać skryptów przeznaczonych do
uruchomienia pod konsolą w publicznej części Twojego projektu.

Srpróbuj uruchomić następujące polecenie z poziomu linii poleceń:

{% highlight bash %}
> php -i
{% endhighlight %}

Twoim oczom powinna ukazać się pełna konfiguracja PHP, zbliżona do tej, którą zwraca funkcja [`phpinfo`][phpinfo].

Inną ciekawą opcją jest `-a` - umożliwia ona uruchomienie interaktywnej konsoli PHP, podobnej do tej z Ruby'ego, czy
Pythona.

Aby zapoznać się z pełną listą opcji interfejsu konsolowego, zajrzyj na [tę stronę][cli-options].

Jeżeli argumentem wywołania polecenia `php` będzie plik z kodem źródłowym, zostanie on uruchomiony. Uruchamiając skrypt
z poziomu konsoli otrzymujesz dostęp do dwóch zmiennych - `$argc` i `$argv`. Pierwsza z nich jest liczbą naturalną,
reprezentującą ilość przekazanych argumentów wywołania, a druga tablicą z ich wartościami. Ponadto istnieje możliwość
zwrócenia kodu wyjścia, aby poinformować powłokę, czy skrypt wykonał się poprawnie. Więcej informacji na temat kodów
wyjścia znajdziesz [tutaj][exit-codes].

Poniżej znajdziesz kod skryptu drukującego napis "Witaj, $imie" z możliwością podania imienia przez linię poleceń. Plik
z przykładu nazywa się `hello.php`.

{% highlight php %}
<?php
if($argc != 2) {
    echo "Usage: php hello.php [imię].\n";
    exit(1);
}
$imie = $argv[1];
echo "Witaj, $imie!\n";
{% endhighlight %}

A oto przykład wywołania powyższego skryptu:

{% highlight bash %}
> php hello.php
Usage: php hello.php [imię]
> php hello.php Marek
Cześć, Marek!
{% endhighlight %}


 * [Jak uruchamiać skrypty PHP z linii poleceń][php-cli]
 * [Jak skonfigurować PHP w systemie windows, aby móc uruchamiać skrypty z linii poleceń][php-cli-windows]

[phpinfo]: http://php.net/manual/pl/function.phpinfo.php
[cli-options]: http://www.php.net/manual/pl/features.commandline.options.php
[argc]: http://php.net/manual/pl/reserved.variables.argc.php
[argv]: http://php.net/manual/pl/reserved.variables.argv.php
[php-cli]: http://php.net/manual/pl/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/pl/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits