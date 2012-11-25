---
title: Caching obiektów
isChild: true
---

## Caching obiektów {#object_caching_title}

Aby przyspieszyć działanie konkretnych funkcjonalności Twojej aplikacji, warto zastanowić się gdzie w kodzie następuje
odwołanie do źródeł danych, których pobranie jest czasochłonne, a częstość zmian jest niska. W takich sytuacjach warto
rozważyć możliwość użycia cachingu tychże danych. Caching polega na zapamiętaniu rezultatu działania określonego
fragmentu kodu w taki sposób, aby później można było wielokrotnie odwołać się do niego, zamiast ponownie wykonywać
czasochłonną operację. Dzięki odpowiedniemu użyciu cache'a programista może w łatwy sposób zwiększyć szybkość działania
aplikacji, a także zminimalizować obciążenie serwera.

Większość narzędzi, o których pisałem w poprzednim paragrafie, ma funkcję cachingu obiektów. APC, XCache, czy WinCache
oferują proste API do zapamiętywania wyników działania określonego kodu w ich wewnętrznej pamięci.

Najbardziej znanymi narzędziami do cache'owania danych w PHP jest APC i memcached. Oba oferują proste API i są łatwe w
instalacji i użyciu. Istotną różnicą między nimi jest fakt, że APC, zgodnie ze swoją architekturą, znaduje się na tym
samym serwerze, co kod, który jest uruchamiany, a memcached jest narzędziem sieciowym, które umożliwia dostęp z wielu
różnych maszyn, co powoduje, że jest nieznacznie wolniejszy niż APC.

Wybór jest dosyć prosty: jeżeli zależy Ci na skalowaniu aplikacji, wybierz zorientowany na to memcached. Jeżeli Twoja
aplikacja będzie działać na jednym serwerze, użyj APC.  

Przykładowy kod wykorzystujący APC:

{% highlight php %}
<?php
// sprawdź, czy istnieją dane zapisane jako 'expensive_data' w pamięci
$data = apc_fetch('expensive_data');
if (!$data)
{
    // danych nie ma w pamięci, wykonaj czasochłonną operację
    // i zapamiętaj wynik, aby można było użyć go później. 
    $data = get_expensive_data();
    apc_store('expensive_data', $data);
}

print_r($data);
{% endhighlight %}

Narzędzia do cachingu obiektów:

* [APC Functions](http://php.net/manual/pl/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache API](http://xcache.lighttpd.net/wiki/XcacheApi)
* [Funkcje WinCache](http://www.php.net/manual/pl/ref.wincache.php)
