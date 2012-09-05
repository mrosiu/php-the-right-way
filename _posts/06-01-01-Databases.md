---
title: Bazy danych
---

# Bazy danych

Tworząc aplikacje webowe, wielokrotnie staniesz przed koniecznością przechowania pewnych informacji. Służą do tego
bazy danych. PHP wspiera wiele różnych silników baz danych. Zalecanym sposobem komunikacji z bazami danych _do wersji
5.1_ były natywne sterowniki, takie jak [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], itd.

Sterowniki te sprawują się dobrze o ile łączysz się z tylko jednym rodzajem bazy danych, np. MySQL, czy MSSQL, gdyż
każdy z nich posiada inne API, a nauka każdego z nich szybko może się okazać bezsensownym nakładem czasu. Dodatkowo,
sterownik mysql nie jest już aktywnie rozwijany i od wersji PHP 5.4.0 ma status "Long term deprecation", co oznacza, że
wkrótce może zostać usunięty z PHP. Jeżeli obecnie używasz w swojej aplikacji funkcji `mysql_connect()`, czy
`mysql_query()`, zapewne wkróce staniesz przed problemem przepisania tej części. Aby tego uniknąć, zaleca się
stosowanie obiektowych rozszerzeń, takich jak mysqli lub PDO.

* [Jak wybrać API do MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO jest bazodanową warstwą abstracji dostępną od PHP 5.1.0, która dostarcza  obiektowy interfejs do komunikacji z
wieloma silnikami baz danych. PDO nie tłumaczy Twoich zapytań SQL ani nie emuluje brakujących funkcjonalności; jest
natomiast biblioteką umożliwiającą łączenie się do wszystkich obsługiwanych przez siebie baz danych przez jedno wspólne
API, co jest doskonałym rozwiązaniem dla aplikacji w których osoba instalująca ją decyduje o typie silnika. 

Co ważne, PDO pozwala na przekazywanie parametrów do zapytania SQL bezpośrednio z żądania ($_GET, $_POST). Nie musisz
martwić się już o ataki SQL injection, gdyż biblioteka w odpowiedni sposób zabezpieczy ich wartości, aby nie były
szkodliwe. Dzieje się to dzięki "prepared statements" (`PDO::prepare()`) i wstrzykiwaniu parametrów przy użyciu metody
`bindParam()`. 

Spójrzmy na typowy przykład. Twój skrypt otrzymuje numeryczne ID w parametrze GET. To ID uzywane jest później w
zapytaniu SQL, aby wyciągnąć z bazy informacje na temat konkretnego rekordu. Poniżej przedstawiony jest kod, który
nie korzysta z "prepared statements": 

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NIE!
{% endhighlight %}

Cóż, ten kod jest tragiczny. Parametr `id` wstrzykiwany jest do zapytania SQL prosto z żądania (`$_GET['id']`), co
umożliwia wykonanie ataktu SQL injection, a w efekcie wykonanie dowolnego zapytania SQL na Twojej bazie danych. Aby
tego uniknąć, powinieneś zabezpieczyć wartość tego parametru. Dzięki `bindParam()`, cała operacja wykona się "pod
spodem":

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automatyczne zabezpieczenie wartości parametru
$stmt->execute();
{% endhighlight %}

To jest poprawny kod. PDO przy użyciu metody `bindParam()` zabezpiecza w odpowiedni wartość parametru uniemożliwiając
wykonanie ataku SQL injection.

* [Więcej informacji o PDO][1]

## Warstwy abstrakcji

Sporo frameworków posiada własną warstwę abstrakcji bazy danych. Niektóre z nich działają na bazie PDO, inne nie.
Często emulują funkcjonalności niedostępne w danym silniku poprzez opakowywanie zapytań w metody. Jest to oczywiście
pewien narzut czasowy, ale jeżeli Twoja aplikacja ma działać jednocześnie np. na MySQL, PostgreSQL i SQLite, czasem
przejrzystość kodu jest ważniejsza niż niewielki narzut.

Niektóre z tych warstw zostały napisane z uwzględnieniem standardu przestrzeni nazw `PSR-0`, dzięki czemu mogą być
użyte w dowolnej aplikacji napisanej w PHP.

* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/pl/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db

[mysql]: http://pl.php.net/mysql
[mysqli]: http://pl.php.net/mysqli
[pgsql]: http://pl.php.net/pgsql
