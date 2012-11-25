---
title: Wyjątki
isChild: true
---

## Wyjątki {#exceptions_title}

Wyjątki dostępne są w większości języków programowania, lecz programiści PHP często je pomijają. Języki takie jak Ruby
często używają wyjątków. Za każdym razem, gdy coś pójdzie nie tak, nieważne, czy jest to problem z wykonaniem żądania
HTTP, zapytania SQL, czy nawet ze znalezieniem pliku, Ruby rzuca wyjątek. Dzięki temu z łatwością można odnaleźć
przyczynę problemu.

W PHP niestety nie ma tak dobrze. Funkcja `file_get_contents()` w przypadku nieznalezienia żądanego pliku zwraca
`false` i komunikat błędu. Wiele starych frameworków, takich jak CodeIgniter w przypadku błędu zwraca po prostu `false`
i loguje komunikat do swojego własnego źródła, w najlepszym razie dając Ci do dyspozycji metodę a'la
`$this->upload->get_error()`, abyś sprawdził sobie co poszło nie tak. Problemem jest to, że musisz o tym wiedzieć lub
szukać rozwiązania w dokumentacji, zamiast otrzymać jasny komunikat w postaci wyjątku.

Innym problemem jest fakt, że zwykle w przypadku błędu aplikacje wyświetlają komunikat błędu na stronie i kończą
wykonywanie skryptu przez `exit`, przez co developerzy tracą możliwość dynamicznego obsłużenia takiego przypadku.
Naprzeciw temu wychodzą wyjątki, które informują dewelopera o problemie i pozwalają mu podjąć odpowiednie kroki.
Przykład:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('Mój temat');
$email->body('Jak się masz?');
$email->to('guy@example.com', 'Ktoś');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // Walidacja danych wejściowych nie powiodła się
}
catch(Fuel\Email\SendingFailedException $e)
{
    // Aplikacja nie była w stanie wysłać maila
}
{% endhighlight %}

### Wyjątki w SPL

Wyjątek sam w sobie nie ma żadnego konkretnego znaczenia i najprostszym sposobem na zmianę tego stanu rzeczy jest
nadanie mu nazwy:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

To pozwala na dodanie kilku bloków `catch` i obsługę różnych wyjątków w odmienny sposób. [Biblioteka SPL][splext]
dostarcza kilka typów wyjątków, których możesz używać w swojej aplikacji. Jest to między innymi wyjątek
`BadFunctionCallException` wyrzucany w przypadku wywołania złej funkcji, czy `InvalidArgumentException`, którego możesz
użyć w przypadku przekaaznia nieprawidłowego argumentu do funkcji czy metody. Pełną listę wyjątków, które dostarcza SPL
znajdziesz w manualu.

* [Artykuł na temat wyjątków w manualu][exceptions]
* [Lista wyjątków w bibliotece SPL][splexe]
* [Zagnieżdżanie wyjątków w PHP][nesting-exceptions-in-php]
* [Artykuł na temat dobrych praktyk dotyczących wyjatków w PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/pl/language.exceptions.php
[splexe]: http://php.net/manual/pl/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
