---
title: Data i czas
isChild: true
---

## Data i czas {#date_and_time_title}

W PHP istnieje wbudowana klasa `DateTime`, która dostarcza spójny, obiektowy interfejs do zarządzania datami i czasem.
Dzięki niej możesz łatwo wykonywać operacje takie jak odczyt, zapis, porównywanie oraz różne obliczenia, nawet w
wielu strefach czasowych. PHP oferuje również zwykłe funkcje, które potrafią wykonywać takie operacje, lecz wiodły one
prym w starszych dystrybucjach, gdzie `DateTime` nie było jeszcze dostępne.

Aby uzyskać obiekt klasy `DateTime` zawierający bieżący czas, należy po prostu użyć konstrukcji `new \DateTime`; aby
użyć określonej daty - należy skorzystać ze statycznej metody fabrykującej `createFromFormat()`. Metoda `format()`
potrafi natomiast skonwertować czas zapisany w obiekcie z powrotem na odpowiednio sformatowany ciąg znaków.

{% highlight php %}
<?php
$raw = '22.11.1968';
$start = \DateTime::createFromFormat('d.m.Y', $raw);

echo "Data rozpoczęcia: " . $start->format('Y-m-d') . "\n";
{% endhighlight %}

Operacje arytmetyczne na obiekcie `DateTime` najłatwiej wykonuje się za pomocą klasy `DateInterval`. `DateTime` posiada
metody `add()` i `sub()`, które przyjmują obiekt klasy `DateInterval` jako argument - dzięki temu możesz zapomnieć o
problemach związanych ze strefami czasowymi oraz istnieniem czasu letniego i zimowego. Przykładowo, aby obliczyć
interwał czasu między dwiema datami, możesz użyć metody `diff()`. Zwraca ona obiekt `DateInterval`, który bez zbędnych
obliczeń zamienisz na zrozumiały dla użytkownika ciąg znaków.

{% highlight php %}
<?php
// stwórz kopię obiektu $start i dodaj do niego miesiąc i 6 dni
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo "Różnica: " . $diff->format('%m miesiąc, %d dni (razem: %a dni)') . "\n";
// Różnica: 1 miesiąc, 6 dni (razem: 37 dni)
{% endhighlight %}

Stosując obiekty `DateTime` możesz używać zwykłych operatorów porównania:
{% highlight php %}
<?php
if($start < $end) {
    echo "Rozpoczęcie ma miejsce przed zakończeniem!\n";
}
{% endhighlight %}

Ostatni przykład pokazuje użycie klasy `DatePeriod`, która służy do iterowania po liście powtarzających się zdarzeń.
Przekazując do jego konstruktora dwa obiekty `DateTime` (początek i koniec) oraz interwał czasowy, otrzymamy iterator
zawierający listę wszystkich zdarzeń między nimi.

{% highlight php %}
<?php
// wyświetl listę wszystkich czwartków między datami $start i $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach($periodIterator as $date)
{
    // wyświetl datę
    echo $date->format('m/d/Y') . " ";
}
{% endhighlight %}

* [Strona w manualu na temat `DateTime`][datetime]
* [dostępne opcje formatowania dat w PHP][dateformat]

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
